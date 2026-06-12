---
title: "Ubuntu 10.10 wifi occasionally stops working"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by evez on 2011-08-19
Hi, I'm using Ubuntu 10.10 on an ASUS K40IN series. Using wifi at home (WPA conn) and lately it's randomly stopped working until I reboot. 
Annoying..
Can anyone help?

---

### Post by eisbaw on 2011-08-19
Restarting WLAN drivers and the networking subsystem is likely to fix your problems.

Unfortunately, this is only really possible from the commandline.
I have put the following in a script, wlan_restart.sh:

service network-manager stop
modprobe -r wl 
modprobe -i wl

ifconfig eth1 down
rfkill unblock 1
rfkill unblock 2
rfkill unblock 3
rfkill unblock all
ifconfig eth1 up
iwconfig eth1 txpower 20dbm

service network-manager start

sleep 1
nmcli nm wifi on

nmcli con up uuid 541e13cd-330a-496f-98c3-06d1cce9a153


Please replace eth1 and the uuid-number with your own.

---

### Post by evez on 2011-08-19
Hi Eisbaw. thanks.. I'm always a bit embarrassed for being so ignorant and crap techie but I must say I don't understand your reply.. 
Is this what I need to copy/paste in the command line?:

service network-manager stop
modprobe -r wl 
modprobe -i wl

ifconfig eth1 down
rfkill unblock 1
rfkill unblock 2
rfkill unblock 3
rfkill unblock all
ifconfig eth1 up
iwconfig eth1 txpower 20dbm

service network-manager start

sleep 1
nmcli nm wifi on

nmcli con up uuid 541e13cd-330a-496f-98c3-06d1cce9a153

And how do I know what my eth1 and uuid-number are?

---

