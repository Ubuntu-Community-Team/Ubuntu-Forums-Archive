---
title: "Edgy thinks my wireless is an Ethernet"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Ubunted on 2006-10-28
My Thinkpad X30's built-in "B" wireless works fine under Dapper, however under Edgy - through upgrades or the Live CD - it sees it as "wlan0" but only lets me configure it as if it were an Ethernet interface - no place for selecting the WLAN or entering the WEP key.

Relevent lspci entries:
```
0000:01:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
0000:01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
```

---

### Post by trubblemaker on 2006-10-28
what's your output from 
```
 iwlist scan 
iwconfig
ifconfig

```

---

### Post by Ubunted on 2006-10-28
In Edgy Live CD:

```
ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
sit0      Interface doesn't support scanning.

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:60:2D:AE:E9  
          inet addr:192.168.83.100  Bcast:192.168.83.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe2d:aee9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:942195 (920.1 KiB)  TX bytes:125054 (122.1 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20904 (20.4 KiB)  TX bytes:20904 (20.4 KiB)

ubuntu@ubuntu:~$ 

```

On my Dapper install:

```

****@****-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Failed to read scan data : No data available

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

****@****-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:41:B3:C6:5C
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=8/92  Signal level=140/153  Noise level=113/153
          Rx invalid nwid:0  Rx invalid crypt:21  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

****@****-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:05:3C:06:64:12
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::205:3cff:fe06:6412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:290411 (283.6 KiB)  TX bytes:58506 (57.1 KiB)
          Interrupt:11 Memory:f8000000-f8000fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

****@****-laptop:~$

```

---

### Post by solomarv on 2006-10-28
I get the same exact problem:
[LIST]
[*]dmesg has not mention of wlan0
[*]wlan0 is thought of as an ethernet card
[*]ifconfig wlan0 up does not work
[*]iwlist wlan0 scan does not work
[*]iwconfig wlan0 says it's not a wireless card
[/LIST]
...other stuff... resulting in: no wireless.

---

### Post by Qazer on 2006-10-28
I have the same problem with a d-link dwl-510.

---

### Post by leo1a0 on 2006-10-28
I have exactly the same problem. I have a Thinkpad R40. First I upgraded from Dapper to Edgy after dowloading for two hours the update. Then I reinstalled Dapper from CD and everything went normal with the wireless card, so I dowloaded the Edgy LiveCD and running from it the wireless card is again identified as ethernet card. Dunno What to do... thanks for helping, I guess it's a bug in need to be fixed:-k

---

### Post by trubblemaker on 2006-10-29
well hate to rain on the parade but the card is registering and it is registering as a wireless card.  the "No scan results" is the key to showing that.  but by no means is the card working I agree.  So it doesn't matter that it's registered as a wireless card.  If i remeber correctly there are some howto's/trouble shooting for the prism driver for dapper, and they might be helpful for edgy, but I'm not sure, i don't have the card.

---

### Post by stani on 2007-02-05
I have exactly the same problem with my thinkpad x30. Does anybody have a solution for Edgy, which I prefer to use? If not, did anyone try it on feisty?
Thanks,
Stani

---

### Post by Steve S. on 2007-02-05
I don't have the same card, but I went through some of the same wireless issues with the Edgy upgrade.

At first all I could get to work was wlassistant, and I had to run that each time to get a connection.  It worked every time, but had to be run and didn't set up the wireless automatically.

Then, something worked to get it taken care of at boot up, but I couldn't tell you what...you can [see this thread]("http://www.ubuntuforums.org/showthread.php?t=317880") for what I tried if you want...something in there worked for sure, though.

I would start with wlassistant to get a connection, then go from there.  Of course, that is assuming it all worked with Dapper...if you had unresolved driver issues in Dapper, then that is for another how-to. :)

---

### Post by stani on 2007-03-10
This is the solution if you have prism2.5 wavelan:
[http://www.ubuntuforums.org/showpost.php?p=2155130&postcount=54](http://www.ubuntuforums.org/showpost.php?p=2155130&postcount=54)

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

### Post by trubblemaker on 2007-03-15
stani great to hear you posting bug info.

 If any ones got info on this it would be awesome if you posted to launchpad!

help the developers!

---

### Post by sunmouse on 2007-04-06
I get the same error and I am running 7.04 in my x30.

---

### Post by solomarv on 2007-05-20
By the way, Feisty solved the issues I had with wireless.

---

