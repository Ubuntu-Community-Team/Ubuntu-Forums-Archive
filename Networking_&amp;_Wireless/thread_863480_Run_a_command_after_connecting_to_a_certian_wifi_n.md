---
title: "Run a command after connecting to a certian wifi network"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Phantom784 on 2008-07-18
At my university (Penn State), we have to use a VPN to get online once we connect to their open wireless network.  I have successfully configured the VPN for use on linux.  However, every time I connect to the wifi, I have to go to the terminal and type in the command to lanuch the vpn.  Is there a way to get ubuntu to automatically run this command (as root) whenever I connect to the penn state wifi network (and only that wifi network)?

---

### Post by Phantom784 on 2008-07-18
I figured it out myself!  If anyone's interested.

Add a script to /etc/network/if-up.d

```
#!/bin/bash
if iwconfig|grep -c pennstate
then                                                         
        pkill vpnc
        vpnc psu.conf
fi

```
change the part after -c for the ssid to look for, and put the commands to run between then and fi

---

### Post by dregoroid on 2008-10-29
good solution, worked for me

---

