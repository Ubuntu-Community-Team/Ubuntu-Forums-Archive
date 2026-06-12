---
title: "Network card connects but doesn't display."
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by bobby2000 on 2007-12-21
Hey, the wireless connects to the network, but when i go on FF the sites don't show.

If its any help:

eth0      Link encap:Ethernet  HWaddr 00:16:E6:1A:A3:7C
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:11:50:B2:76:FA
          inet addr:86.141.68.106  Bcast:86.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:53 dropped:3 overruns:0 frame:53
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2515 (2.4 KB)  TX bytes:9440 (9.2 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Cheers & Merry Christmas

---

### Post by mellowd on 2007-12-21
Can you do this, open up a terminal and type

```
ping www.google.com
```


then 

```
sudo aptitude install traceroute
traceroute www.google.com
```

Paste your results here please.

---

### Post by bobby2000 on 2007-12-21
neither worked 

jack@jacks-desktop:~$ sudo aptitude install traceroute
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following NEW packages will be installed:
  traceroute
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.1kB of archives. After unpacking 176kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  traceroute

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main traceroute 2.0.9~rc1-1
  Could not resolve ‘gb.archive.ubuntu.com’
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.9~rc1-1_i386.deb:](http://gb.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.9~rc1-1_i386.deb:) Could not resolve ‘gb.archive.ubuntu.com’
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
jack@jacks-desktop:~$ traceroute [www.google.com](www.google.com)
The program 'traceroute' can be found in the following packages:
 * traceroute-nanog
 * traceroute
Try: sudo apt-get install <selected package>
bash: traceroute: command not found

---

### Post by mellowd on 2007-12-21
hmm, I was hoping that traceroute could be installed off the CD. Is your CD still in your sources.list file?

Secondly, if you ping, you get no response?

I'm seeing a lot of errors on eth1. More errors than then clean packets. How exactly are you connected?

---

### Post by bobby2000 on 2007-12-21
CD no longer in sources list. connecting through a belkin usb wireless adapter. It connects properly, and fm another computer i can confirm that it is connected, but actually on the system it won't access.

---

### Post by mellowd on 2007-12-21
> **bobby2000 said:**
> CD no longer in sources list. connecting through a belkin usb wireless adapter. It connects properly, and fm another computer i can confirm that it is connected, but actually on the system it won't access.

Could you add the Cd for now and installed traceroute. That will really help a lot in finding where the connectivity stops

---

### Post by bobby2000 on 2007-12-21
unable to use traceroute... next suggestion :(

---

### Post by mellowd on 2007-12-21
Not able to install it from the CD?

---

### Post by bobby2000 on 2007-12-21
nope, ive gone to plan d... reformat hd and re-install... cheers anyway. Do you have wlm as a way to contact you easily?

---

### Post by mellowd on 2007-12-21
wait wait, you shouldn't need to do that. as long as you update your sources.list to use your ubuntu CD we should be able to get it installed. Traceroute will help a lot in finding where the issue lies exactly.

wlm?

---

### Post by bobby2000 on 2007-12-21
too late, i was experiencing other problems as well anyway. Hopefully with this it shouldiron out a few other issues.


WLM = windows live messenger... ie msn

---

### Post by mellowd on 2007-12-21
Ah, sorry, I don't use msn at all :/

---

### Post by bobby2000 on 2007-12-21
:O ah ok, what would be your suggestions for the first things to do once installed?

---

### Post by mellowd on 2007-12-21
install traceroute as soon as you can, see how far the trace gets and post here. Also paste the output of ifconfig here once reinstalled

---

