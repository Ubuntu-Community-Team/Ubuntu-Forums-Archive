---
title: "I've got my bond working, but how do I get internet connectivity on my Motherboard NI"
date: 2022-10-27
forum: Networking &amp; Wireless
---

### Post by hamptonsitm on 2022-10-27
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291196&stc=1[/IMG]

First time poster go easy :-)[COLOR=#1A1A1A][FONT=&quot]Essentially if my devices on the bond network go down (switch/SFP+ NIC/DAC's), I'd love to plug a cable into the Motherboard NIC and it just works on good ol' DHCP.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]I have spent a bit of time now going through Google/Fourms to get this far but now I am stuck.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&quot]If it's possible I'd love to use renderer: networkd or networkmanager to see the GUI in action.

I'm using Ubuntu Server 22.04 w/ Desktop Installed + Ubuntu Pro enabled.

Thanks in advance[/FONT][/COLOR]

---

### Post by TheFu on 2022-10-27
Please don't post images of text.

Where's the gateway4 entry?  How would the OS know where to send traffic that isn't on the same subnet if there isn't any gateway specified?

BTW, there are other mistakes, but without text, it is too hard.

---

### Post by hamptonsitm on 2022-10-31
Apologies

[COLOR=#666666][FONT=Lato]# Let NetworkManager manage all devices on this system[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]network:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]      ethernets:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]        enp1s0f0:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          dhcp4: false[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          dhcp6: false[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          optional: true[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]        enp1s0f1:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          dhcp4: false[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          dhcp6: false[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          optional: true[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]      bonds:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]        bond0:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          interfaces: [enp1s0f0, enp1s0f1][/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          addresses: [192.168.1.248/24][/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          gateway4: 192.168.1.254[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          nameservers:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]                    addresses: [192.168.1.254][/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]          parameters:[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]                  mode: 802.3ad[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]                  #mode: balance-alb[/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]                  mii-monitor-interval: 1 [/FONT][/COLOR]
[COLOR=#666666][FONT=Lato]                  primary: enp1s0f0[/FONT][/COLOR]

---

