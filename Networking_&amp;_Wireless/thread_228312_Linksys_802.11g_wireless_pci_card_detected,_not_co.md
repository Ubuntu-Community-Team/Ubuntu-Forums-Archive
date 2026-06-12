---
title: "Linksys 802.11g wireless pci card detected, not connected"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by westin on 2006-08-03
I just switched from RH9 to Ubuntu because I read they had better wireless support... while this is true, and my card was actually detected, it will not connect to the router.  It says it is activated, but if I close 'Networking' and reopen it, it says the connection is not active... I don't get any error messages. any help would be appreciated... 

here is the result of iwconfig:

eth0 IEEE 802.11b/g ESSID:"bosk"  Nickname:"Broadcom 4306"
     Mode:Managed Frequency=2.437 GHz  Access Point:Invalid
     Bit Rate=1 Mb/s
     RTS thr:off Fragment thr:off
     Encryption key: ****-****-** [it has the correct key listed]
     Security mode:open
     Link Quality:0 Signal Level:0 Noise Level:0 
     Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
     Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I have excellent signal with my laptop in the same room, and the windows partition works fine... so it is not a signal issue... Thanks in advance for any advice...

westin

---

### Post by russbuss on 2006-08-03
> **westin said:**
> I just switched from RH9 to Ubuntu because I read they had better wireless support... while this is true, and my card was actually detected, it will not connect to the router.  It says it is activated, but if I close 'Networking' and reopen it, it says the connection is not active... I don't get any error messages. any help would be appreciated... 

here is the result of iwconfig:

eth0 IEEE 802.11b/g ESSID:"bosk"  Nickname:"Broadcom 4306"
     Mode:Managed Frequency=2.437 GHz  Access Point:Invalid
     Bit Rate=1 Mb/s
     RTS thr:off Fragment thr:off
     Encryption key: ****-****-** [it has the correct key listed]
     Security mode:open
     Link Quality:0 Signal Level:0 Noise Level:0 
     Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
     Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I have excellent signal with my laptop in the same room, and the windows partition works fine... so it is not a signal issue... Thanks in advance for any advice...

westin


I had a similar problem when I first started using Ubuntu.  I determined that my problem stemmed from using encryption.  I turned off my encryption and everything worked without a hitch (and still does).  Give this a shot and see if it helps.  It is a good sign that your card is getting recognized, though.  I should add that my card is a few years old, but is wireless G so should be comparable to yours.

There are ways to make encryption work although I still haven't looked into it yet (last I checked it was in the wiki under "WPA Supplicant").  This is primarily because I connect through an airport and they are known to be a tad temperamental when it comes to working with Ubuntu.

Good Luck!

---

### Post by westin on 2006-08-03
originally posted by russbuss:

> I determined that my problem stemmed from using encryption. I turned off my encryption and everything worked without a hitch (and still does).

Thanks for the reply :) but I have actually tried this with encryption disabled also... it did the same thing... whenever I try to 'sudo ifup eth0' it keeps saying 'sending: network is down' and then it will up the interval... until it finally gives up... if it is any help, here what I get with 'ifconfig eth0'

eth0      Link encap:Ethernet  HWaddr 00:0C:41:65:A6:39
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000

---

### Post by russbuss on 2006-08-12
> **westin said:**
> originally posted by russbuss:
if it is any help, here what I get with 'ifconfig eth0'

eth0      Link encap:Ethernet  HWaddr 00:0C:41:65:A6:39
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000

Hmmm.... I don't know if this will help, but my wireless PCI card comes up as my ra0 interface.  I'm afraid, however, that I don't know why this is the case.  Are you sure that the hardware address in your eth0 output matches the hardware address of your pci card (i.e. on the pci card itself or on the linksys box it came in)?

In my Networking dialogue I have:

Wireless Connection: The interface ra0 is active
Ethernet Connection: The interface eth0 is not configured
Modem Connection: The interface ppp0 is not configured

I do not have a cable connected to my not-wireless ethernet card so the fact that my wireless card is my only active interface might have something to do with it.  I can't remember if I ever de-activated my not-wireless interface (which might be why it is listed as not configured).

Here are my ifconfig ra0 and ifconfig eth0 outputs:

ra0       Link encap:Ethernet  HWaddr 00:0F:66:70:97:44
          inet addr:192.168.1.5  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:fe70:9744/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5206414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8778972 errors:1607 dropped:1607 overruns:0 carrier:0
          collisions:100602 txqueuelen:1000
          RX bytes:1161332091 (1.0 GiB)  TX bytes:2720078020 (2.5 GiB)
          Interrupt:209 Base address:0xc000

eth0      Link encap:Ethernet  HWaddr 00:30:1B:B7:B8:BE
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


So, maybe if you can get your wireless card to be recognized as your ra0 interface it might help?

Hope this helps somehow....

---

### Post by flub on 2006-08-12
westin, I'm having exacttly the same problem.

Anyone with any ideas? Is there a config file for wireless that we can check the settings.

It all appears connected but I cannot even ping the router.

---

### Post by mrtrick on 2006-11-06
I have the exact same issue, but mine is a Zyxel g-302 card. Anyone have a fix? Even entering WEP key... still shows same... connected showing rec errors and not data transfer

---

### Post by flukierdonut on 2007-06-14
what drivers are you using, windows?

---

### Post by dardack on 2007-06-14
I had issues until i uninstalled network-manager and i was connecting manually until someone pointed me to wicd (wicd.sourceforge.net i believe).  1.2.9 works great for me.

---

