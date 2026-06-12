---
title: "Ubuntu reverts to wired connection on restart instead of bridge"
date: 2022-12-14
forum: Networking &amp; Wireless
---

### Post by smbunn on 2022-12-14
I have followed advice on this excellent site to set up a bridge (br0) using Network Manager and Netplan.

This allowed my Docker container with a KVM machine running HomeAssistant to share my wired Ethernet connection and have its own IP Address, separate to the IP address of the Ubuntu machine itself.

However every time I reboot, the wired Ethernet takes over again instead of the bridge and I have to plug in a keyboard, mouse and monitor to run one single command:  [COLOR=#0000ff]*nmcli con down "Wired connection 1"*[/COLOR]
If I run [COLOR=#0000FF]*brctl show*[/COLOR] before downing the wired connection there is no bridge showing and eno1 is using the wired Ethernet.

As soon as I down the wired connection, and if I run [COLOR=#0000ff]*brctl show*[/COLOR] again, now it lists my bridge [COLOR=#0000ff]*br0*[/COLOR] and everything works again.  My ubuntu is happy on 192.168.1.38 and my HomeAssistant responds perfectly on 192.168.1.22

I have set up the bridge in netplan and I know netplan runs at boot time because i see netplan_br0 and netplan_eno1 as two devices via [I][COLOR=#0000ff]nmcli con show
[/COLOR]
How do make it remember to down the wired connection and keep the bridge running on reboot please?[/I]

---

### Post by smbunn on 2022-12-15
[SOLVED]
I got some feedback on Sourceforge.  All I needed to do was remove the original "Wired connection 1" which I did from the standard Settings GUI.  As soon as I did this I saw the bridge take over as the wired connection.  A reboot confirmed it was all working.

---

