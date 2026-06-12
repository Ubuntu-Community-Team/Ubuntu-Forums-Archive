---
title: "[SOLVED] How do I undo everything I did in this HOW TO? (Internet stopped working b/c"
date: 2008-01-12
forum: Networking &amp; Wireless
---

### Post by mahasmb on 2008-01-12
I was desperate and so I followed the following HOW TO on these forums.

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Unfortunately, not only did the HOW TO not work for me, but my internet has stopped working, since.

So how can I undo it all?

---

### Post by mahasmb on 2008-01-12
I've got wired working now, but wireless refuses to work, even though WICD tells me I'm connected half the time anywhere from 55% to 70% strength.

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Name"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:03:2F:37:B7:29   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by mahasmb on 2008-01-13
Anyone? Pretty please?

---

### Post by sqrt2 on 2008-01-13
Uninstall ipmasq (which most likely is causing your problem) and dnsmasq (which you don't need). Remove the line "net.ipv4.ip_forward = 1" from /etc/sysctl.conf or replace the 1 with a 0. This disables your system's functionality of acting as a router for others. Reboot.

If this doesn't work, post the output of "sudo route -n" and "sudo iptables -t nat -vnL".

---

### Post by mahasmb on 2008-01-14
Thank you very, very very very much for your help and reply. What you suggested seemed to work partially.

I can only get wireless working if I connect to the wired internet, disable and then re-enable the firmware for BCM43xx in "Restricted Drivers", and then connect to wireless with WICD. And only then can I disconnect my ethernet wire and have wireless working. But after I reboot, wireless no longer works again and iwconfig gives me the following:


```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

"eth1", which is for my wireless is completely missing.

Here's what you asked me to provide.

```

$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```

```
$ sudo iptables -t nat -vnL
Chain PREROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         


```

Again thank you very much for your help.

---

### Post by sqrt2 on 2008-01-14
For some reason either the bcm43xx driver isn't loaded or doesn't recognize your wireless interface. (It sounds strange that that would be the result of following this HOWTO. It's probably a completely unrelated problem.)

Does "dmesg | grep bcm43xx" say something right after booting the system?

---

### Post by mahasmb on 2008-01-14
"dmesg | grep bcm43xx" gives me no output right after I reboot.

Also, I tried to follow this HOW TO  [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)  which at step #8 led me to 
 [http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595](http://ubuntuforums.org/showpost.php?p=2999631&postcount=1595)  

After that HOW TO didn't work I *tried* to undo everything 
- uninstalled ndiswrapper
- uninstalled acer-acpi
- deleted " /etc/init.d/acer_acpi_wireless_enable"

I guess I might have missed something.

---

### Post by sqrt2 on 2008-01-14
The fact that you're not getting any output from "dmesg | grep bcm43xx" means that the bcm43xx driver is not loaded on boot. Try the following:

1) Uninstall ndiswrapper-utils.
2) Install bcm43xx and bcm43xx-fwcutter.
3) Download [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o).
4) Run "sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o".
5) If necessary, add "bcm43xx" to /etc/modules.
6) Reboot.

---

### Post by mahasmb on 2008-01-14
THANK YOU!

THANK YOU!

THANK YOU!

It works! :)

---

