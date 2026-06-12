---
title: "Ubuntu VM can't connect to Synology in bridged mode"
date: 2016-05-30
forum: Networking &amp; Wireless
---

### Post by Stuart_Isaac on 2016-05-30
[COLOR=#141414][FONT=Lucida Grande]I have an Ubuntu 14.04 VM running in VMware Fusion 8 on an iMac running OS X 10.11. When I have the VM configured to use the bridged networking mode, Ubuntu can't connect to my Synology NAS (DS415+ on DSM 6). Ping fails, SSH fails, login via the web interface fails, and SMB fails. However, I can SSH and otherwise connect from the VM to the host iMac and to other computers on the LAN. The firewall on the NAS is disabled, and there's no firewall running on the VM. I can also SSH from the NAS to the Ubuntu VM, just not from the Ubuntu VM to the NAS. Every other machine on the LAN can connect to the NAS just fine.[/FONT][/COLOR]

[COLOR=#141414][FONT=Lucida Grande]If I switch the VM's network settings to use the "Share with my Mac" mode rather than bridged mode, it's able to connect to the VM successfully. However, I want the VM to use bridged networking so it's a first-class citizen on the LAN.[/FONT][/COLOR]

[COLOR=#141414][FONT=Lucida Grande]Does anyone have insight into how to resolve this?[/FONT][/COLOR]

---

### Post by Stuart_Isaac on 2016-06-01
Well, it turns out that I'm an idiot. I'd forgotten that I'd statically assigned the unused second ethernet port on the NAS the same IP address that I was using with DHCP reservation for the Ubuntu VM. So despite the fact that the port was inactive, the Synology was refusing connection attempts from an IP address that it recognized as its own.

---

