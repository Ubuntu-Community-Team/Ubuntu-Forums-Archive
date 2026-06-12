---
title: "Broadcom 1390 (4311) only works unencrypted"
date: 2007-03-13
forum: Networking &amp; Wireless
---

### Post by firecat53 on 2007-03-13
Problem:   Broadcom (dell) 1390 mini-PCI card inside my hp dv6000 laptop will only work on an unencrypted network. Will not work with WEP or WPA.  The weird part is that it responds the same from Knoppix Live CD as it does to the Feisty I've got installed.

Things I've tried:
1. Install ndiswrapper from the repos.
2. Compile and install latest (1.38) ndiswrapper from source per very good directions from FrodoB in the wiki.
3. Changed order of iwconfig commands (e.g. configuring key before essid and vice versa
4. Tested the card on this computer from windoz...works perfectly with/without WEP. Same network and all.

Applicable dmesg output:
```
[  873.142359] wlan0: ethernet device 00:14:a5:bf:ee:d8 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[  873.142404] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  873.174871] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  873.186179] ndiswrapper (add_wep_key:820): adding encryption key 1 failed (C0010015)
[  878.258945] ndiswrapper: probe of 1-4:1.0 failed with error -110

```

Output of "sudo iwconfig wlan0 key s:passphrase"

```
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```

I've googled this to death and found people with similar errors, but never a resolution.
Exact same behavior with repo ndiswrapper and compiled. Also the same before and after installing nvidia drivers.

Please please please help!!!

Thanks, Scott

---

### Post by kokiri on 2007-03-13
My best advice being that I also have a broadcom wifi card is to stop using the ndiswrapper drivers all together as the bcm43xx drivers are very good now. Do a google search for bcm43xx-firmware_1.3-1ubuntu2.tar.gz
it's a set of good pre-cut firmwares for bcm43xx based wifi cards, they've worked great for me

You need to copy all the bcm43xx files to /lib/firmware/(insert running kernel dir here)
and just to be safe make a dir in there called bcm43xx and copy them there as well

or you can get the bcm43xx-fwcutter that's in the apt repo and cut your own from your windows drivers.

then add ndiswrapper to your /etc/modprobe.d/blacklist so they don't load and add bcm43xx to your /etc/modules


My experience is that on modern kernels with the bcm43xx module and a ndiswrapper module there's some fighting that goes on the mucks up the encryption authenticating, not sure why but getting rid of ndiswrapper and going with the kernel bcm43xx modules just works better. And to boot I find I get better range and power consumption

---

### Post by der_vegi on 2007-03-16
well, the bcm43xx still seems to have its problems. i have a dell 1490 network card (broadcom 4311), but it is very slow.

using the firmware you get installing the fwcutter and using the firmware bcm43xx-firmware_1.3-1ubuntu2.tar.gz, i get only an internet speed of about 30k sitting directly next to my router. using my cable i get 600k.

---

### Post by firecat53 on 2007-03-17
Well, I guess patience has paid off. Wireless seems to be working perfectly with ndiswrapper using the default Network manager both unencrypted and with wpa. I did compile ndiswrapper, so now that it's working, I'm a little hesitant to try the default version again :)  

Not sure exactly what changed...perhaps a new version of Network Manager? I wasn't really paying attention to the upgrades over the last week.

Scott

---

### Post by der_vegi on 2007-03-17
yeah, ndiswrapper works for my dell wireless 1490 on amd64 as well, using the dell drivers [http://ftp.us.dell.com/network/R140747.EXE]("http://ftp.us.dell.com/network/R140747.EXE")

the only nasty thing is, that wpa authentication seems to last muuuuch longer than with the bcm43xx and sometimes even fails. but at least i have 600k then, with bcm43xx i only geht 30k. *g

---

### Post by chili555 on 2007-03-17
From man iwconfig: ```
 Passphrase is currently not supported
```but then it goes on later to say: ```
 iwconfig eth0 key s:password
``` 
I know a guy that heard of a guy that met a guy who said he got WEP working with a passphrase, but I've never actually seen it.

I suggest using the hex 10- or 26-character key like this: ```
sudo iwconfig wlan0 key 096c7f280e2abc7ba1159e4afe
``` You might need to sudo gedit /etc/network/interfaces and put it in there: wireless-key 096c7f280e2abc7ba1159e4afe

Also make sure your router is broacasting key #1.

Your actual key will vary.

---

### Post by firecat53 on 2007-03-17
Well, it worked last night with WPA. Now it's back to unencrypted only and I can't figure out why!! I updated last night to 2.6.20-11 and recompiled ndiswrapper. Also added irqfixup to my boot stanza to fix a usb port problem. Guess I'll go back one kernel and see if it works again. Hard to tell sometimes if these are feisty related or just Broadcom related problems!!

Scott

---

### Post by Kobalt on 2007-03-17
I have Feisty and the exact same card and it's working quite neatly. 
I've compiled ndiswrapper from sources and used the driver from Hp website (since my laptop is an Hp). Maybe your problem is with this driver : where did you get it ? Is it up to date ?

---

### Post by krayzee8 on 2007-03-21
I have the same problem with my Dell 1390 card in my Compaq V5209US Laptop.  I attempted several different methods to get the wireless up on Fedora.  I read about some success with Ubuntu, so I gave it a shot and did a fresh install of Ubuntu.  I actually got the wireless card working with Ndiswrapper (which is further than I was able to get on Fedora!).  Unfortunately, it only works on unencrypted networks :( .  If anyone finds a work around for this, I would love to know it.

---

