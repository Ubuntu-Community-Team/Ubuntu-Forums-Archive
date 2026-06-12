---
title: "[SOLVED] looking for a wireless USB or PCI adapter with good signal and WPA support e"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by thomas7.10 on 2008-03-09
Hi!

I was looking on this page: [http://ubuntuforums.org/showthread.php?t=370108]("http://ubuntuforums.org/showthread.php?t=370108") but i still have questions. I tried to figure out something on the net but i didn't get it managed to find the right information.
Anyway. I have a Linksys WRT54GL router and I'm looking for a PCI card or a USB adapter that supports the g-standard and WPA. It should also have a good signal strength and it should be supported by programms like aircracker and these.

Does anyone have an idea what product i should buy?

Thanks in advance!

Thomas

---

### Post by scottro on 2008-03-09
Until seeing a couple of threads in the last two days, I would have said the WUSB54GC by Linksys.  For me, it worked out of the box with no problems. 

However, I"ve seen a couple of threads--only in the last few days--from people who find it drops connections and the like.   Still, I'll throw it out there as a suggestion.  

(I only used it for a few days--shortly afterwards, I got the internal wireless working and gave the USB stick to a friend.)

---

### Post by thomas7.10 on 2008-03-09
thanks for the recommendation an this USB stick supports WPA and everything?

---

### Post by rustybronco on 2008-03-09
from personal experience with wpa1 and pci cards.

[http://ubuntuhcl.org/browse/product?id=111](http://ubuntuhcl.org/browse/product?id=111)
[http://ubuntuhcl.org/browse/product?id=110](http://ubuntuhcl.org/browse/product?id=110)

they are not what you would call long range cards (70-90% @ 20 foot), but for a best buy house brand cards not to bad a value.

---

### Post by thomas7.10 on 2008-03-09
well I want to use it with my PC and not with a laptop that's why i can't use PCMCIA.

---

### Post by rustybronco on 2008-03-09
> **thomas7.10 said:**
> well I want to use it with my PC and not with a laptop that's why i can't use PCMCIA.sorry I misread pci as pcmcia (how I don't know), no problem I will edit my above post.
***edited*** got some of those also...

---

### Post by thomas7.10 on 2008-03-09
Sorry for wrtiting again but i tried to get such a Dynex pci card but it is not aviable in Sweden - not even on Amazon in Germany. So it would take me ages and lot's of shipping costs and taxes to get such a pci card. Do you have something to recommend that is not produced by Dynex?

---

### Post by scottro on 2008-03-09
To answer your earlier question, that Linksys USB worked with WPA2 and non broadcasting network for me.

---

### Post by thomas7.10 on 2008-03-09
Ok i ordered now the linksys USB - i hope it will work ;)

---

### Post by scottro on 2008-03-09
Please do update us with the info.  I have a page on wireless, sort of Fedora oriented, where I say that the particular stick worked for me.  Therefore, if there are people having problems with it, I'd like to get that on the page too.  

Thanks

---

### Post by lelmo85 on 2008-03-09
I think you are making a good choice . I use Linksys WRT54G router with Linksys WUSB54G adapter about 40 feet apart Word of caution: count on resetting (is that the word?) your router and modem at odd intervals. Simple process; power down router and then modem, leave power off a minute or so, plug modem back in to power first, then router. Should kick right off.

---

### Post by cometa2k7 on 2008-03-09
I use a **Belkin Wireless G USB Network Adapter**

Ubuntu seems to let it work out of the box, and previously I had it running with ndiswrapper, so it should work for most linux systems.

There probably are other wireless adapters out there, I found this one by luck.

---

### Post by Hightide on 2008-03-09
Hi

The Linksy usb is popular and reasonably priced on [Amazon]("http://www.amazon.co.uk/s/ref=nb_ss_w_h_?url=search-alias%3Daps&field-keywords=linksy&Go.x=0&Go.y=0&Go=Go")

regards

:)

---

### Post by thomas7.10 on 2008-03-09
Ok i will let you know if it works out of the box and if it looses connection from time to time...

Thomas

---

### Post by scottro on 2008-03-09
Thank you very much.

---

### Post by ruiruas on 2008-03-09
Hi, I bought an EDIMAX 7318usg (25-30€) and as far as signal goes... it's one of the best (it's the usb one with the additional 4db antenna). It also supports WPA, WPA2, WEP, etc. The only problem is the native linux drivers seem to have some bug, but I installed it with "ndiswrapper" and the windows drivers, blacklisting the native ones and now it works great.

---

### Post by wieman01 on 2008-03-10
I don't really recommend Linksys' WUSB54G V4 because it does not work really well with the current kernel/version of Ubuntu. Certainly, with 'ndiswrapper' there is not much of an issue but you will have to do a lot of tweaking. Stay away from V4 which is Ralink based. My two cents...

---

### Post by thomas7.10 on 2008-03-10
well we will need 2 PCI or USB WLAN devices. One is a Windows machine and i assume that it is going to work fine with the linxsys. Maybe i'm going to buy myself an edimax.
Can of you recommend a manual on ndiswrapper and the use of windows drivers? 

Thomas

---

### Post by wieman01 on 2008-03-10
I can recommend my own guide (see signature - Ralink) for instance. It should work for all sorts of adapters, not only Ralink ones. Check it out and post there if you need help.

---

### Post by thomas7.10 on 2008-03-11
Hi!

I'm just wondering whether this is possible: Why can't i blacklist the drivers of the Linksys USB adapter and use ndiswrapper to get the windowsdriver of Linksys to work?

Thomas

---

### Post by wieman01 on 2008-03-11
You could do so... but why bother? There are adapters that work straight out of the box.

---

### Post by thomas7.10 on 2008-03-11
Well i can't find these adapters that just work out of the box, are available in my region and do not lose the connection. Maybe the Belkin USB one. Well i will see what i can do. How do you what chipsets you have to blacklist? I want to try it with linksys - just to learn something...

Thomas

---

### Post by wieman01 on 2008-03-11
What adapter have you got and which version number is it?

You find out by issuing:
> sudo lshw -C network

---

### Post by Anzan on 2008-03-11
I'm using a Belkin Wireless G USB Network Adaptor, 802.11g - 54 Mbps with Gutsy on an HP DV9000 series laptop (as I cannot as yet get the built-in to work).

---

### Post by thomas7.10 on 2008-03-12
Hi wieman01

i just got the linksys adapter and plugged it in.

It is recognized by ubuntu and "your" command (sudo lshw -C network) gives me that reply (I replaced the MAC address with Xs):

```
 
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

I can't find any hint on the version number...

Thomas

---

### Post by wieman01 on 2008-03-12
The version should be on the back of the device... Can you find it? I think there is a tiny label revealing the version number.

---

### Post by thomas7.10 on 2008-03-12
I've got a serial number: MLF00H204169
A FCC ID: Q87-WUSB54GC
An IC: 3839A-WUSB54GC

And a label saying: Manufactured 02/2008

I don't know if it is one of the numbers but i'm going to look on google now. I assume that it is possible to get the version number if you now when it was manufactured.

By the way: Are you sleeping sometimes? Whenever I'm online you're too.

---

### Post by wieman01 on 2008-03-12
Oh, it's a GC... that's different. I was more referring to the WUSB54G but I guess the aren't on sale any longer.

Man, I think we might be in a different time zone. Therefore... :-)

You can try my 'ndiswrapper' tutorial, as I am pretty sure this one won't work right away. "sudo lshw -C network" does not look promising. Before you do so, please also post:
> sudo iwlist scan

---

### Post by thomas7.10 on 2008-03-12
ok the result was:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:1B:11:4D:24:71
                    ESSID:"link"
                    Mode:Master
                    Channel:7
                    Frequency:2.442 GHz
                    Signal level=-70 dBm  
                    Encryption key:on
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000007663fe09d8
          Cell 02 - Address: 00:1B:11:9A:67:8C
                    ESSID:"Folkungag"
                    Mode:Master
                    Channel:10
                    Frequency:2.457 GHz
                    Signal level=-80 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000018f24e2615
          Cell 03 - Address: 00:14:6C:7A:7E:EA
                    ESSID:"NETGEAR"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-60 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000017c10bff60
          Cell 04 - Address: 00:12:BF:3C:0F:10
                    ESSID:"philips"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Signal level=-78 dBm  
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000189cdb1dc93
          Cell 05 - Address: 00:19:E3:32:D4:A7
                    ESSID:"TJ"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz
                    Signal level=-74 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (2) : TKIP WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000033bf15d7a
          Cell 06 - Address: 00:01:38:8B:FE:5D
                    ESSID:"GN_private_B9"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-78 dBm  
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000001918ac3fd7e
          Cell 07 - Address: 00:17:F2:51:D5:8C
                    ESSID:"julia"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz
                    Signal level=-76 dBm  
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000058e455702

```

---

### Post by wieman01 on 2008-03-12
Wow, excellent. It seems to work! Now can you connect to your local network using Network Manager? Does it pick up the 'wlan0' interfaces?

---

### Post by thomas7.10 on 2008-03-12
I can connect but i don't have a wlan yet - my router didn't come yet. When it comes i#m going to try to use it as it is now. If it loses connection would there be a possibility to use ndiswrapper?

---

### Post by wieman01 on 2008-03-12
Yes, ndiswrapper will be an option. But let's try without first. :-) Report back when you are ready.

---

### Post by thomas7.10 on 2008-03-13
So now i'm writing you with my connected Linksys adapter to the wlan. It doesn't work so well.

It works good and fast and then there is something like a slow period where almost no data is transmitted. After that it starts to work fine again for a while.  The connection status is always on about 80%. Sometimes in between it changes to 0% and then it comes again to 80%.

So i think it's better to change to ndiswrapper. Can you help me with that?

Thomas

---

### Post by wieman01 on 2008-03-13
Sure I can, Thomas. Take a look at my tutorial please. And could you please the output of...
> sudo lshw -C network
...once again?

We can undo the changes anytime you like.

---

### Post by burnclouds on 2008-03-13
I have had great success with any of the atheros chips.

---

### Post by thomas7.10 on 2008-03-13
Ok i follow now the tutorial i found out that i'm using the rt73usb driver right now. I try myself and ask here if I have questions - thanks for yout help wieman01

---

### Post by wieman01 on 2008-03-13
No problem. Post there if you need a hand.

---

### Post by thomas7.10 on 2008-03-13
Ok tried now to follow the tutorial. 

I installed the driver and i did the "ndiswrapper -l" and i got as a reply:

```

desktop : invalid driver!
rt73 : driver installed
        device (13B1:0020) present (alternate driver: rt73usb)
wusb54gc_20051228 : invalid driver!

```

On the one hand the driver seems to be installed on the other hand it is invalid... is it working?

---

### Post by wieman01 on 2008-03-13
Please restart the PC after blacklisting the old (Linux) driver. Still the same error message? If so, you need to reinstall ndiswrapper. Just remove it using Synaptic and reinstall it. That will remove all existing drivers.

Do you have the right version of the driver? For 32-bit or 64-bit?

---

### Post by thomas7.10 on 2008-03-13
So i restarted the computer and it works. The signal isn't that good as it was with the original 'driver' but the signal doesn't seem to get lost.

Thank you very much

---

### Post by wieman01 on 2008-03-13
You are welcome, mate. That was painless. :-)

---

