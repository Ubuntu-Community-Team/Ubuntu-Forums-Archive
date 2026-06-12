---
title: "iBook Airport, UGH!"
date: 2005-06-19
forum: Networking &amp; Wireless
---

### Post by Flying Llama on 2005-06-19
Hello all,

I've been experimenting with several different linux distros on my iBook G3, 800mhz, the dual usb snow white version (not the clamshell). I've tried Debian (which basically didn't work), YellowDog, and now Ubuntu (which is definitely the best). None of them were able to get my airport card connected to my network (i'm using the old, standard card, not the broadcam, but the base station, or access point, is Extreme). In system/administration/networking, I can go and enable the card (eth1), which says its active, though when I close it and reopen it (not even a reboot), goes back to being deactivated. My little network monitor in the top right corner flashes simultaneously from time to time, but only for a split second. What is it sending, and to who?
I am using a dual boot system with MacOSX Tiger on the other side, which IMO is much more polished and way more advanced, Linux seems more "Beta". But I'm curious. :-P

---

### Post by DJ_Max on 2005-06-20
OS X is developed specificaly for Apple computers, LinuxPPC is not. But with liitle configuration it can be just as good, or even better, as I rarely boot in OS X. Airport Extreme won't work with Linux, yet. Since Apple won't/can't release any specs. Regular Airport works.

---

### Post by Flying Llama on 2005-06-20
[QUOTE=DJ_Max]OS X is developed specificaly for Apple computers, LinuxPPC is not. But with liitle configuration it can be just as good, or even better, as I rarely boot in OS X. Airport Extreme won't work with Linux, yet. Since Apple won't/can't release any specs. Regular Airport works.[/QUOTE]

But as I said, I want to use Ubuntu regularily, but without internet it will never be possible. And as I said in my post, I am using the old airport, the one that should work.
Someone help!

llama :-x

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=Flying Llama] (i'm using the old, standard card, not the broadcam, but the base station, or access point, is Extreme).[/QUOTE]

Could that be the problem?

I have an idea. Take you iBook to some place you know has free internet, change the ssid to the word:

any

and see if it works. Me airport card works out of the box.

---

### Post by Flying Llama on 2005-06-20
[QUOTE=poofyhairguy]Could that be the problem?

I have an idea. Take you iBook to some place you know has free internet, change the ssid to the word:

any

and see if it works. Me airport card works out of the box.[/QUOTE]

Hey, that's actually a brilliant idea! I'll try that as soon as possible.
Thanks,

llama :grin:

---

### Post by Flying Llama on 2005-06-20
Here is a newer and more detailed expanation:

Hello all,

I have been having a problem with every distribution of linux I try,
and now even Ubuntu. I have an 800MHz G3 Apple iBook (not the
clamshell) which has a standard, 802.11b wireless Airport card. I can
go in System - Administration - Networking and activate my eth1 (the
Airport card), and enter in the ESSID and WEP 128bit password.
(ESSID=***-*** ***** where * is a letter, so it has a space in it).
The WEP is 13 characters long. I set it to automatically configure IP
and such using DHCP. This works fine in OSX (it's a dual-boot system),
and my DHCP server is an Airport Extreme Base Station (access point),
meaning it's 802.11b/g compatible, and this access point is connected
to my cable modem using ethernet. Normally everything should work, but
it doesn't.

Here is the feedback I get on lspci:
[http://img60.echo.cx/img60/6307/dsc069888ty.jpg]("http://img60.echo.cx/img60/6307/dsc069888ty.jpg")
[http://img60.echo.cx/img60/1738/dsc069874hs.jpg]("http://img60.echo.cx/img60/1738/dsc069874hs.jpg")

Here is what I get on eth1 in ifconfg:
eth1     Link encap:Ethernet HWaddr 00:30:65:0B:ED:F3
           inet6 addr: fe80::230:65ff:fe0b:edf3/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:358 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0b) TX bytes:0 (0.0 b)
           interrupt:57

On typing iwconfig I get:
eth1        IEEE 802.11-DS   ESSID:"***-*** *****"   Nickname:"HERMES I"
              Mode: Managed   Frequency:2.457 GHz   Access
Point:44:44:44:44:44:44
              Bit Rate:11Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
              Retry Limit:4   RTS thr:off   Fragment trr:off
              Power Management:off
              Link Quality=0/92   Signal Level=134/153   Noise Level=134/153
              RX invalid crypt:0   Rx invalid frag:0
              Tx excessive retries:0   Invalid misc:0   Missed Beacon:0

In iwlist scan:
eth1: Failed to read scan data : Operation not supported

_______________
Thanks in advance,
llama

---

