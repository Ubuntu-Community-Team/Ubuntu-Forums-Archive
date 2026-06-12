---
title: "Hardy 8.04 Wireless Networking for N-Routers / Broadcom Wireless Cards"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by jkhh07 on 2008-07-30
[I]Broadcom 4328 wireless card a/b/g/pre-N running on an HP 6715b Business Notebook
Ubuntu 8.04 with Ndiswrapper
Using a Belkin N wireless Router 
[/I]

I can connect to my Belkin Wireless N router at home, **_[U][B][B][B]B[B]UT ONLY through [U][B]A non-secure connection.**[/B]_ [/B][/B][/B][/U][/U][/B]When I enable security on my router using WPA1 Personal or WPA2 with PSK, I canNot connect. My computer picks up the signal and everything. I enter the network name, define type of authentication, and enter PSK but if I hover over the wireless icon, it says gets to a status of "waiting on network key from router"

I **_*CAN *_**connect to a WPA2 at work with a PSK using a W**ireless G router**. Both PSK at work and home are 8 characters long. I have tried the exact same setup with both HP drivers and Dell Drivers.

=============================================================
--> I ran **dmesg **and because it was so long, I put it into a word document and attached as :"dmesg.doc" (it was so long it cut some off the top in the TERMINAL window)
--> I also ran **iwlist scan **and it brought up about 15 different networks as I Live in an aparmtent. I took just my ESSID and pasted it below but the rest of it is attached as: "ubuntu forums 2 commands.doc" 
______________________________________________________________
**hajekiho@hajekiho-laptop:~$ ndiswrapper -l**

bcmwl5 : driver installed
	device (14E4:4328) present

**hajekiho@hajekiho-laptop:~$ iwconfig**

lo        no wireless extensions.
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
eth0      no wireless extensions.

**hajekiho@hajekiho-laptop:~$ iwlist scan**
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:66:1A:C6
                    ESSID:"hajekiho"                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on

Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11                     Mb/s;9 Mb/s 18 Mb/s; 36 Mb/s; 54 Mb/s; 6Mb/s;12 Mb/s
24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

=================================================

I will get the same settings from Work later today but I thought i'd help get us a head start with this for now. WIll post later today.. probably around 1800 CT GMT -6:00

HELP!!

---

### Post by jkhh07 on 2008-07-30
edit

---

### Post by pytheas22 on 2008-07-30
I'm not sure what's going on when you try to connect at home...dmesg doesn't mention much about it.

If you change your router at home to only use g mode and set WPA1 encryption, can you connect then?

Anyway, I'll look at dmesg some more and wait on your scanning results from your network at work and get back to you with more ideas later.

---

### Post by jkhh07 on 2008-07-30
**_This is the scan from work and here I can connect with no problem._**
[B]
hajekiho@hajekiho-laptop:~$ ndiswrapper -l[/B]
bcmwl5 : driver installed
	device (14E4:4328) present
**hajekiho@hajekiho-laptop:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Buchanan"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0B:85:5C:29:AE   
          Bit Rate=18 Mb/s   Tx-Power:20 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
**hajekiho@hajekiho-laptop:~$ iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:85:5C:29:AE
                    ESSID:"Buchanan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by pytheas22 on 2008-07-30
Thanks for that.  It looks like your network at work uses only WPA2 encryption, but at home you're using WPA1.  Can you try changing your home router to use WPA2 (and only WPA2)?  I think it would work then.  WPA1 and WPA2 are both equally secure; they just use different algorithms.

In your router's configuration utility (which you probably access by typing 192.168.1.1 or 192.168.0.1 in your browser), the option to switch to use only WPA2 should be obvious, but if you're not sure what to select, post a screenshot of the options.  Also, make sure it's not set to use both WPA1 or WPA2 (some routers do this)--make it only use WPA2.

If it still doesn't work after making the change, can you please post:

```
iwlist scan
```

at home again?

---

### Post by jkhh07 on 2008-07-31
OK I disabled security at home and **Could Connect** and ran iwlist scan.

          Cell 01 - Address: 00:1C:DF:66:1A:C6
                    ESSID:"hajekiho"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
===========================================================================

I set security at 64bit WEP. **_Could_**  connect here using "open system" option for authentication.

hajekiho@hajekiho-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:66:1A:C6
                    ESSID:"hajekiho"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
I tried the same security but using "shared key" option on laptop - This never let me connect.
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::
==========================================================================
Here I tried 128bit WEP **_and also got connected_**.

hajekiho@hajekiho-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:66:1A:C6
                    ESSID:"hajekiho"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:100/100  Signal level:-31 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
==========================================================================

I tried WPA 1 and WPA 2 using all combinations of AES and TKIP but still was **NOT able** to get connected. Below is a scan while using the most secure encryption. WPA2 / TKIP + AES. **THE ONLY DIFFERENCE I see between the _WPA2 @ work and home** is_ something very small as to how it is being identified, and I think it actually might have something to do with why its not working. 

hajekiho@hajekiho-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1C:DF:66:1A:C6
                    ESSID:"hajekiho"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK



If you look at at "IE: WPA Version 1" and then later  "IE: IEEE 802.11i/WPA2 Version 1" => this is DIFFERENT than when connecting at WORK.
At work they are flipped. The first listed with the standard included 
=> 802.11i/WPA2 Version 1 _**and then**_ lists "ie wpa version 1" 

Now I do not even have an intermediate level of Network Knowledge but I would think that the process of connecting to a wireless network is to first, Identify the type of encryption /// then identify the type of authentication /// then execute. -> this seems to me like when my computer is trying to connect using WPA @ home, it has this FLIPPED from the process used at work.

DOes that make sense/possible?





.

---

### Post by pytheas22 on 2008-07-31
The way that Linux deals with WPA networks (WEP is much simpler) is by using something called wpa_supplicant, which is like a big set of steps that tells the wireless card how to negotiate the connection.  Depending on the specific configuration of the WPA network, the steps are different.  Network Manager tries to figure out on-the-fly what the steps should be, but it can be tricky, especially if the router doesn't advertise information in the way that NM expects.

It may help to try using wicd to connect instead.  It's a different wireless manager that sometimes can connect where Network Manager can't.  It's also easier to trouble-shoot because it saves the wpa_supplicant configuration that it tried to use (Network Manager does it all as it goes and doesn't save a record anywhere), so you can look at it later and try to figure out where it went wrong if it failed to connect.

To install wicd, you first download the installer from [here]("http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0").

Then you need to uninstall NM, because they conflict:
```

sudo apt-get remove network-manager
```

Finally, double-click on the wicd installer that you downloaded previously, and it should install.  wicd should then be in your Applications>Internet menu.  Use that and see if it is able to connect to your network using WPA1 or 2.

By the way, in case you want NM back for some reason, you can reinstall it with:
```

sudo apt-get install network-manager-gnome
```

---

### Post by jkhh07 on 2008-07-31
Sounds like a plan I will try this and get back.

IF you were to follow the link below, it'll show the same interface of the router that I have. 

[http://www.belkin.com/support/article/?lid=en&pid=F5D8233-4&aid=10177&scid=942](http://www.belkin.com/support/article/?lid=en&pid=F5D8233-4&aid=10177&scid=942)

I was thinking that if my router actually broadcasts both WPA1 and WPA2 at the same time but then only authorizes 1 or the other, then maybe this could cause issues and confuse the wireless card, if ya get what I mean

The only way to set them apart is to choose the Authentication method either TKIP or AES. There is also feature that combines these together, but I am not sure when this is Combination-Feature is enabled whether or not they use both at the same time or if it just makes it backward compatible to either one. I will try the WICD and see what happens.

---

### Post by pytheas22 on 2008-08-01
> The only way to set them apart is to choose the Authentication method either TKIP or AES. There is also feature that combines these together, but I am not sure when this is Combination-Feature is enabled whether or not they use both at the same time or if it just makes it backward compatible to either one. I will try the WICD and see what happens.

I'm not sure exactly how it works either...I wish router vendors would provide a more powerful interface for configuring wireless so that you knew exactly what each option does.

But try changing to use only TKIP and see if makes a difference.  Also give wicd a shot and see if it helps.

---

### Post by jkhh07 on 2008-08-03
Alright, I followed your instructions and it got me in trouble haha. When I tried installing Wicd, it said i must First remove Network manager. I ran the code from terminal and... uh.. well.... it knocked out all Networking all together. Even LAN. from here, I spent a few hours in forums and got Network Manager back on there and downloaded Wicd. I installed it, and the system said it had to remove Network Manager. I proceeded and now I think its worse. I can't even connect to any Encrypted network at all. IS there something I can do? I can connect to LAN though so at least that.

Follow this here. Does this apply to my card?

[http://linuxwireless.org/en/users/Drivers/b43#unsupported](http://linuxwireless.org/en/users/Drivers/b43#unsupported)

---

### Post by pytheas22 on 2008-08-03
I'm really sorry that wicd caused problems...I've never had problems with it and often it can connect in places where NM can't.  If wicd can't connect you to any encrypted network, though, you could uninstall it with:
```

sudo apt-get install network-manager-gnome
```

That should prompt you to remove wicd and install NM again at the same time.  Then you should at least be able to connect again at work, and could try playing with the TKIP settings on your router to see if it helps.
> 
Follow this here. Does this apply to my card?

[http://linuxwireless.org/en/users/Dr...43#unsupported](http://linuxwireless.org/en/users/Dr...43#unsupported)

Yes, your card isn't yet supported by b43, the native Linux driver for Broadcom chipsets.  If it were, you could try using that instead of ndiswrapper, but it's pretty clear from the developers' website that your card is not going to work with b43.  You could keep checking back, however, to see when support is implemented.  You could also take a look at the developers' mailing list archives, [email]bcm43xx-dev@lists.berlios.de[/email], and could ask them about support for the 4328 chip (but don't bother them about it unless you're sure they haven't already addressed the issue on the mailing list or their website).

---

### Post by showcaser on 2008-09-02
hey jkhh07, in case your are still having trouble I have one suggestion.

I had essentially the same problem with a broadcom 4329, after many hours of messing around what finally got it to work was simply changing the router to BG-Only mode. It appears the draft-n messes things up when trying to connect with a WPA encryption. Setting the router to b or g (or both) and suddenly everything worked fine.

Hope this helps.

---

### Post by jkhh07 on 2009-11-04
Resolution:

My draft-N card was not supported by the developers.
-The router at home I was using cannot set itself to a g-mode only for the connection

 a.) a+b+g mode
 b.) N mode

 cc.) wpa2+wpa1
 dd.) WEP
 ff.) open

The workaround for this was to get a different router and abandon the wireless-N benefits as the card was simply just not supported for this particular setup.

---

