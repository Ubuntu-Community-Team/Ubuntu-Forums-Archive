---
title: "can't see wireless networks in Hardy"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Guy23 on 2008-06-24
I have an Atheros wireless card and I had it working perfectly with madwifi. I accidentally right clicked and disabled wireless networking up in the tool bar and now I can not see a list of available wireless networks. When I type 'iwconfig' my wireless card doesn't even show up.

I can't seem to find anything on google or in the forums. Please help.

Thanks in advance for your help!

---

### Post by Guy23 on 2008-06-25
Just an update: I reinstalled madwifi, but things are still not working right. It seems that I do not have the device 'wifi0' on my machine. When I try to run kismet I get the error

```
ERROR:  Unable to create VAP: No such device
ERROR:  Unable to create monitor-mode VAP
WARNING: wifi0 appears to not accept the Madwifi-NG controls. Will attempt to configure it as a standard Madwifi-old interface. If you are using madwifi-ng, be sure to set the source interface to the wifiX control interface, NOT athX
FATAL: GetIFFlags: interface wifi0: No such device
debug - open failed: /sys/class/net/wifi0/device/ No such file or directory
Done.
```

Any help would be greatly appreciated.

---

### Post by plewisfdx on 2008-06-25
I assume you've rebooted since you turned wifi off, correct?

Go to System->Administration->Network and see if there is an unchecked wifi adapter there.  Unlock, then check it if its there.

if that fails, lspci and paste the output here.

---

### Post by Guy23 on 2008-06-26
Yes, I have restarted. When I go to the network settings window described above, there is no option for wireless. I only have 'wired connection' and 'point to point connection'.

Here is the output to lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by plewisfdx on 2008-06-26
Ok, I'm looking into this, but do you have a wifi radio on/off button on your laptop?

I'm thinking the software "disable wireless" may have turned off the radio, so look for a way to turn it back on.  What is the model laptop?

Also, if you're dual booting, is it working in windows?  If it is, then don't bother looking for the radio on/off.  :D

---

### Post by Guy23 on 2008-06-26
Yup, the wifi radio button was turned off. Since it shines red in ubuntu all the time I didn't even think to check it. Thanks for all of your help!

---

### Post by Guy23 on 2008-07-05
Things are not working again. This time I did not accidentally disable the wireless networking. But I am having the same problems as before. The wifi radio button is activated and wireless works when I boot into Windows. The only symptom that I have that is different from before is that now when I run kismet I get the following:

```
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
Done.
```

I really don't know where to begin...

---

### Post by kumoshk on 2009-03-20
> **Guy23 said:**
> Yup, the wifi radio button was turned off. Since it shines red in ubuntu all the time I didn't even think to check it. Thanks for all of your help!

How did you turn it on again? I think I'm having the same problem. I've tried lots of methods to get this card up and running, but I can't get a list of available networks. I've found a few ways that let the network icon mention wireless stuff, but no automatic networks. When I go to network tools, it says everything for my wireless card is either 'not available' or there is a 0 by it. That doesn't look promising. I'm guessing it thinks it's turned off. It does show up under lspci:
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig produces this:
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by MysticGold04 on 2009-03-20
I just had the same type of issues trying to INSTALL hardy on my Acer laptop that has an Atheros card.  I could not get it to work for the life of me with MadWifi drivers, so I decided to try and install Intrepid 8.10 and voila! My wireless worked out of the box.   Unless you NEED to stay with Hardy, I'd upgrade to Intrepid.  I wanted to use Hardy because of the LTS, but I didn't want to have wireless issues.. thats why I decided to install Intrepid... better support for Atheros wireless cards.

---

### Post by darrenn on 2009-03-20
This is fixed in jaunty they tell me. So you won't have this problem anymore.

---

### Post by kumoshk on 2009-03-23
Well, I tried everything, pretty much. All the compiling I tried ended up failing in one particular or the other. Not sure why. It should have worked fine, since I had all the pre-requisites and such.

I found a way to get my other wireless card working (on my laptop).

Anyhow, I finally tried out Jaunty alpha 6—and, it works! It works with my laptop, too. Anyway, it's just as well, I've been waiting to try out Ext4 for some time now.

I don't know if I'll bother putting Jaunty on my laptop when the stable release comes out, though, since my wireless already works (I had a time figuring that one out)—at least not until PowerDVD is available for it as it is with the two releases before. But, there doesn't seem to be any other way to get the wireless on my desktop working, except through Jaunty. Well, there probably is, but it would probably be more work than it's worth to find out at this point (since this works and all without having to configure anything).

---

