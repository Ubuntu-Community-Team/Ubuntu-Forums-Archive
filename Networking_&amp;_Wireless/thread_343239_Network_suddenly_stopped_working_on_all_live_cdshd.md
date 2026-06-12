---
title: "Network suddenly stopped working on all live cds/hdd install, but working in Windows"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Sukarn on 2007-01-21
pppoeconf (and dhcp) was working fine for me from live cds and hdd installation until some time ago. I did a pppoeconf from a 6.06 desktop cd, and was browsing the net while it was being installed to the hdd (had somehow got some corrupt partitions, so did a complete fill with zeros and then installed the OS again). Then, after the installation was complete, I turned the comp off and went to sleep (around 11 PM). I woke up at about 2 AM, and then switch on Ubuntu (from hdd), did a pppoeconf, but it failed with the output as below.
Then just to make sure, I switched to the desktop cd, and still the output from pppoeconf was the same. I did a windows install, and voila, dhcp was working fine. switched to ubuntu, and no, its not working. Its been like this for 4 days now. I haven't been able to use the net in Ubuntu, and without net, its pretty much useless (no video, no audio...).
The live cds I have tried are - 5.10 (breezy badger), 6.06 (dapper drake), 6.06 64-bit (dapper drake), 6.10 (edgy eft), 6.10 64-bit (edgy eft), 7.04 (feisty fawn) herd 2. The difference in feisty herd 2 is that it finds 2 ethernet devices (where did the second one come from?) - eth0 and eth-something. I don't remember what the second one was.
I even tried setting the modem/router to autodial the pppoe connection, so it acted like an always on connection. It was working fine in Windows XP, but Ubuntu still did not detect a net connection available. ](*,) 
Another thing - if I try to open 192.168.1.1 in firefox (the modem/router's settings page), it fails to open with the "Unable to connect" (Firefox can't establish a connection to the server at 192.168.1.1) error. The same page is opening fine in Windows XP. Thats how I changed the settings to autodial pppoe, by going to that page in Windows.

sudo pppoeconf -
```

	  â&#8221;&#338;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;¤ ALL DEVICES FOUND? â&#8221;&#339;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218; I found 1 ethernet device:                               â&#8221;&#8218;
          â&#8221;&#8218; eth0                                                     â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218; Are all your ethernet interfaces listed above?           â&#8221;&#8218;
          â&#8221;&#8218; (If No, modconf will be started so you can load the      â&#8221;&#8218;
          â&#8221;&#8218; card drivers manually).                                  â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218; Or press ESC to abort here.                              â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;               <Yes>                  <No>                â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8221;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#732;

```
If I select No, then I am presented with the same screen again (is this called modconf?). The weird this is, I don't remember the statement in brackets (If No, modconf will be started so you can load the card drivers manually) being displayed when pppoeconf used to work for me.

On Yes -
```

          â&#8221;&#338;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;¤ SCANNING DEVICE â&#8221;&#339;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;
          â&#8221;&#8218; Looking for PPPoE Access Concentrator on eth0...         â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                            12%                           â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8221;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#732;

```
This goes on till 90%
Then the same thing with "multi-modem mode" in parenthesis below "Looking for PPPoE..."

And then -
```

          â&#8221;&#338;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;¤ NOT CONNECTED â&#8221;&#339;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218; Sorry, I scanned 1 interface, but the Access             â&#8221;&#8218;
          â&#8221;&#8218; Concentrator of your provider did not respond. Please    â&#8221;&#8218;
          â&#8221;&#8218; check your network and modem cables. Another reason      â&#8221;&#8218;
          â&#8221;&#8218; for the scan failure may also be another running pppoe   â&#8221;&#8218;
          â&#8221;&#8218; process which controls the modem.                        â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8218;                          <Ok>                            â&#8221;&#8218;
          â&#8221;&#8218;                                                          â&#8221;&#8218;
          â&#8221;&#8221;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#732;

```
ifconfig output -
```

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:F3:92:97:90
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe92:9790/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xc400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15456 (15.0 KiB)  TX bytes:15456 (15.0 KiB)

```
```

ubuntu@ubuntu:~$ ping -c 2 192.168.1.1
Network is Unreachable.

```

If you want any more information, then please ask me. I want to get this thing working again. Very weird that this had to happen moments I put Ubuntu stickers on my guitar and the front of my CPU. Was it waiting for me to do that :confused: 

NOTE: The outputs were copied to a text file from Ubuntu 6.06 64-bit live cd and then saved to a Fat32 partition. In Windows, Wordpad seemed to be having some problem reading that file, and displayed | as â&#8221;, and some other characters as weird ones.

---

### Post by Sukarn on 2007-01-22
Just wanted to add that I'm getting the same results from Debian that I was getting in Ubuntu

EDIT: Just tried openSUSE, dhcp is failing there too. I wonder how windows has it going.

Please help me here guys.

---

### Post by BrentC on 2007-02-02
I'm having almost the same exact problem as you Sukarn. I reinstalled Ubuntu and now it doesn't recognize my internet connection, yet windows does. I get the same errors in PPPoEconf.

---

### Post by Sukarn on 2007-02-08
Doesn't anyone have any idea about this?
I've run out of ideas to make it run now.
BrentC, if you manage to get it working, can you please post here about it?

---

### Post by glenndrayton on 2007-02-12
We are having similar problems with 6.10 (Edgy Eft).  We have tried four computers, complete install, some inside vmware, others just full install of Unbuntu only.

In all cases the ethernet (wired) appears configured fine, and we can ping anywhere (inside and out), but firefox won't navigate to any pages (connection times out) and Synapics will not download any information. In other words the install is completely useless.

It is worrying that you get the same issue on several versions of Ubuntu. What is going on here? Why is no one coming to the party with a fix? I've talked to two other users online and they are stuck with no inet browsing as well.

This problem needs immediate resolution, its a bl**dy joke!

---

### Post by Sukarn on 2007-02-13
Yep, I used to be an active member in the community, and used to be testing the latest versions of ubuntu...But since this problem started, I haven't been able to use Ubuntu, let alone participate in the community.

This needs to be fixed!!

My problem is different from glenndrayton's though. I am not able to access the internet at all. I'm not able to ping remote hosts. I'm not even able to ping the modem/router (192.168.1.1).

I will be getting a different internet connection in about 2 months. I have to wait that long since I had paid for the current connection in advance. I can only hope that the new modem/router I get with the new connection (different company), will work with Ubuntu.

The only thing left for me is to test is to take this router out and test it at a friend's house. Though I doubt that will help as its working in windows.

---

### Post by Sukarn on 2007-04-07
Well, for some reason, its working fine when I connect it through USB. It works as if its connected through ethernet, listing the device as an ethernet device, but it doesn't work when I connect it through ethernet instead of USB... :S

---

