---
title: "Set tls-cipher for OpenVPN in Kubuntu 23.10"
date: 2023-11-27
forum: Networking &amp; Wireless
---

### Post by gugani-pub on 2023-11-27
New install of Kubuntu 23.10. In previous releases to add the OpenVPN connection I do:

1: Add the VPN connection as normal using the Network Manager GUI
2: Edit the connection file in /etc/NetworkManager/system-connections/(connectionname).nmconnection where (connectionname) is the name of your VPN conection
3: In the [vpn] section, beneath the line that starts ca=, add a new line reading
tls-cipher=DEFAULT:@SECLEVEL=0
4: Save the file
5: Enter the command systemctl restart NetworkManager

But now in 23.10 that is not working. There is info about the change in the [release notes]("https://discourse.ubuntu.com/t/mantic-minotaur-release-notes/35534"):

**NetworkManager now uses Netplan** as its default settings-storage backend. On upgrade, all connection profiles from /etc/NetworkManager/system-connections/ are transparently migrated to /etc/netplan/90-NM-*.yaml and become ephemeral, Netplan-rendered connection profiles in /run/NetworkManager/system-connections/. Backups of the original profiles are automatically created in /var/lib/NetworkManager/backups/ (read more at [NetworkManager YAML settings backend 22]("https://netplan.readthedocs.io/en/stable/netplan-everywhere") and [LP: #1985994 7]("https://bugs.launchpad.net/netplan/+bug/1985994")).

I am trying to add the configuration in the already existing /etc/netplan/90-NM-*.yaml, but I cannot find the option equivalent in Netplan to the tls-cipher=DEFAULT:@SECLEVEL=0 option in NetworManager. 
Could someone give me some advice. Greetings.

---

### Post by gugani-pub on 2023-11-28
Now I feel a little stupid, I realized that tls-cipher is an option in the OpenVPN configuration, not NetworkManager. I added the option to the ovpn file:
[FONT=monospace][COLOR=#0000ff]tls-cipher[/COLOR][COLOR=#000000] "[/COLOR][COLOR=#ff54ff]DEFAULT:@SECLEVEL=0[/COLOR][COLOR=#000000]"[/COLOR]
Then I [/FONT]added it via Network Manager. By the way, you can use the gui or in cli like this:
[FONT=monospace][COLOR=#0000ff]nmcli connection import type openvpn file file.ovpn[/COLOR][COLOR=#000000]
Now I can check the option I was looking for automatically crea[/COLOR][/FONT]ted in /etc/netplan/90-NM-*.yaml:
[FONT=monospace][COLOR=#0000ff]**vpn.tls-cipher**[/COLOR][COLOR=#ffd7d7]:[/COLOR][COLOR=#000000] [/COLOR][COLOR=#ff54ff]"DEFAULT:@SECLEVEL=0"
[/COLOR][/FONT]
Note: 
For GNOME 43+ (Debian 12, Ubuntu 23.04 etc) you can add some parameters (e.g. DEFAULT:@SECLEVEL=0") via GUI.
This way NetworkManager service restart is not required.

 Connection settings > Identity > Advanced > TLS Authentication > TLS cipher string)



[FONT=monospace]
[/FONT]

---

