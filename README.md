# UniFi Switch SFP

Uses SSH agent items to monitor the optical parameters of SFP fiber transceivers installed in UniFi Switches (e.g. US-24-250W). Requires the configuration of user macros at the host level: `{$UNIFI_SSH_USER}` and `{$UNIFI_SSH_PASS}`.

Listed on [Zabbix Share](https://share.zabbix.com/network_devices/ubiquiti/unifi-switch-sfp).

Monitored items are:

*   Temperature (of SFP module)
*   Input Voltage
*   Input Current
*   Output Power (optical dBm)
*   Input Power (optical dBm)
*   Transmission Fault (boolean)
*   Loss of Signal (boolean)

Template is configured for a 24-port switch with 2 SFP ports, so `{$UNIFI_SFP1_PORT} = "0/25"` and `{$UNIFI_SFP2_PORT} = "0/26"`. These macros can be overridden at the host level for 16-port (0/17 and 0/18) and 48-port (0/49 and 0/50) switches.

Avoid setting the check interval too frequently, as SSH agent checks consume more resources than regular, Zabbix agent checks. Uses dependent items.

**Configurable User Macros**

| Macro                | Default Value |
| -------------------- | ------------- |
| `{$UNIFI_SSH_USER}`  | ubnt          |
| `{$UNIFI_SSH_PASS}`  | ubnt          |
| `{$UNIFI_SFP1_PORT}` | 0/25          |
| `{$UNIFI_SFP2_PORT}` | 0/26          |
