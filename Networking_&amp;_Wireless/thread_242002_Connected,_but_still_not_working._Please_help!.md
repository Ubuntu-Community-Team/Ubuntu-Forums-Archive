---
title: "Connected, but still not working. Please help!"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by RobMBaker on 2006-08-23
OK, I've been setting up a WEP wireless network in my house and managed to get it all set up with 3 laptops running XPHome, 1 XPPro and 1 Mac. Ubuntu is the only one that doesn't work so far ...
I think I can connect to the router, as I get a DHCP address; but the router doesn't respond to any ping attempts.
My iwconfig for ath0 is:

ath0      IEEE 802.11g  ESSID:"Darlington"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0D:88:07:83:E2
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:54DC-6BA7-8F   Security mode:restricted
          Power Management:off
          Link Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and my ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:16:E3:02:2E:A0
          inet addr:192.168.0.162  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:fe02:2ea0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:4789 dropped:0 overruns:0 frame:4789
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:409 (409.0 b)  TX bytes:572 (572.0 b)
          Interrupt:217 Memory:f8a00000-f8a10000

There seem to be a lot of errors in the ifconfig, but I don't know what to do about it. I've tried disabling IPv6 (or whatever that was called) and still no joy. Also, I don't know how to interpret the signal, noise and link quality data.

Anyone know how to fix this? I have a feeling it's something quite simple, that I just don't know about, or have missed.

---

### Post by RobMBaker on 2006-08-26
OK, so maybe this isn't a simple fix ... seeing as no-one has even had an idea in 3 days.
Well, it's not really a big problem as I've been using ethernet for the moment ... it's just that it's annoying because Windows and Mac can both do it, where Ubuntu can't!

---

### Post by NetworkGuy on 2006-08-26
Have you tried doing this without WEP enabled on the router?

You are associated with the router.  That's the good news.  Why it isn't working, sounds like WEP.  If you can connect without WEP, then something is up with your WEP key.

I have the same issue that I'm trying to fix as time permits.

---

### Post by nelux on 2006-08-27
Hello,

Do a search for your NIC vendor here in the forums. There are plenty of guides how to get you going.

Good Luck.

Nelux

---

### Post by funchords on 2006-08-27
> **NetworkGuy said:**
> Have you tried doing this without WEP enabled on the router? ...  If you can connect without WEP, then something is up with your WEP key.If WEP was the issue, he wouldn't get a DHCP address.  

Anyone know what a 'frame' error is?  That's what his driver is reporting.  I'm sorry, poster, but I don't know what it is, either.

His device is ath0, which is an Atheros device.  The iwconfig looks good.  I don't think it's wireless-related.

Are there any blurbs in dmesg or /var/log/messages that occur when the card initializes?

---

### Post by funchords on 2006-08-27
> **RobMBaker said:**
> 
ath0      IEEE 802.11g  ESSID:"Darlington"
.
.
.
          Encryption key:54DC-6BA7-8F   Security mode:restricted
.
.
.

Does it help if you do these two commands

sudo iwconfig ath0 key open
sudo iwconfig ath0 key 54DC-6BA7-8F

I could be misunderstanding this parameter.  But if this helps, it may be because of confusion between Encryption and Authentication.  Most WEP networks are Open and Encrypted, but do not provide Authentication.  

I have a WPA network here, so I could not test this.

---

### Post by RobMBaker on 2006-08-28
OK, well I tried some of the suggestions - and had already done one. No joy ...
I think it might be WEP encryption that's the problem too, cos it shows that it's connected and everything, I just get a massive (nr 100%) RX loss rate. The only thing is, I can't try it on Open - cos all the other people in the house wouldn't like the disruption.

Oh well - I'll wait for a more automated wireless system to appear in Ubuntu before I try again ... like Mac or Windows ... only better :p 

Thanks for the suggestions though ...

---

### Post by RobMBaker on 2006-11-23
OK - anyone who finds this and is having similar problems with a Toshiba Satellite L20 (laptop):

I couldn't fix it, but I recently upgraded to Edgy; and thought "let's see if wireless works yet" and sure enough ... it did ... 'out of the box'.
You just put in the SSID and WEP key and you're away ... as simple as Windows XP at last ...

---

