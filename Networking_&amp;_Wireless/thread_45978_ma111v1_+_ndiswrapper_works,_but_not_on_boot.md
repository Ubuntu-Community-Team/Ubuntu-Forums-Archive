---
title: "ma111v1 + ndiswrapper works, but not on boot"
date: 2005-07-02
forum: Networking &amp; Wireless
---

### Post by gregwh on 2005-07-02
Hi all,

I'll contribute to the growing wireless posts.

I installed ubuntu 5.04.  I chose wlan0 during install, but that didn't work so I elected to configure networking later.

After getting ubuntu up, I found that wlan0 didn't appear in System->Administration->Networking.  Hunting around I came across [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto).

I installed the ndiswrapper-utils using the synaptic package manager and ran
 ndiswrapper -i NETMA111.INF
 ndiswrapper -m
 modprobe ndiswrapper
 ndiswrapper -l  (hardware present!!)
 gedit /etc/modules (and added ndiswraper)
 System->Administration->Networking (configured, hit activate)

All was well and I could surf, etc.

When I reboot, however, it doesn't come up.  "dmesg" shows
 ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
 ndiswrapper: driver netma111 (NETGEAR, Inc.,09/29/2004, 3.1.3.32) added
but netstat -rn doesn't show anything.

If I unplug the ma111 usb cable and plug it back it in then do a "sudo /etc/init.d/networking restart" it works fine.  Any ideas why it doesn't come up on boot?

Thanks,
Greg

Here's my /etc/networking/interfaces

$ more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface wlan0 inet static
address 192.168.0.150
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid XXXXX

auto wlan0

---

### Post by spd106 on 2005-07-03
Hi, this one got me for ages. I spent months looking for an answer. I the end I changed the line **map eth0** to **map wlan0** and it worked fine. If you still need eth0 then just insert the line in before it.

Hope this helps

---

### Post by gregwh on 2005-07-03
Thanks.  I tried changing "eth0" to "wlan0" and rebooting, but not joy.  Same behavior.  Doesn't work on boot, but unplugging the adapter and replugging it in followed by "sudo /etc/init.d/networking restart" gets things running.  This adapter seems very finicky when booting.  Awhile ago I tried wlan-ng with on red hat.  The machine would hang on boot unless I unplugged it.  (I eventually gave up.)

---

### Post by TRAVISL on 2005-07-06
I followed the same steps you did and when I did ```
modprobe ndiswrapper
``` I got his error.
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```
Any help would be great.  Which driver did you use? I might be using the wrong one I guess.  Thanks.
Travis

---

### Post by gregwh on 2005-07-07
modprobe requires root privileges.  You should either do them from a "root terminal" or put "sudo" in front of each command.

Greg

---

### Post by blazko on 2005-07-07
Hello,

No, me and someone other are having the same probs, it is not about a missing privilegge. Changing verbosity does not tell more either. But when I entered recovery mode, modprobe was quite telling: some internal calls of ndiswrapper failed. I am currently installing a fresh version from sourceforge and see (worked on Debian Sid for me).

Greetings, Timo

---

### Post by gregwh on 2005-07-10
An update on my situation.  Strangely enough, the interface comes up from a cold boot (as I discovered after a power outage), but doesn't come up from a reboot.  However, after a cold boot the computer locks up after a few minutes of browsing and I have to turn it off.  If I cold boot, then unplug/replug the interface and "sudo /etc/init.d/networking restart," then it runs fine.  Strange.

Greg

---

