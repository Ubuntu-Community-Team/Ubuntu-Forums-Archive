---
title: "Belkin F5D7050 v3 confusion"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by NewDigger on 2008-02-02
Hello, wonder if one of you could help me.

I know that this device has been talked about quite a lot, but I can't seem to find something helpful for me.
I tested it with the live CD and it worked when I put in my information. I installed Linux, and restarted. I put in the security information, and it connected. It then dropped the connection and now when I look under Wireless Networks none are listed.

I have tried rebooting, unplugging the device, plugging it in again, and I can't get it to list any wireless networks again, or connect to it manually. The little light on the adapter also no longer flashes. I am certain the device isn't broken as well since it works in Windows. I'm using Ubuntu 7.10.

Any help?

---

### Post by rustybronco on 2008-02-02
please post the output of **lsusb**
I believe it to be a rt73 chipset so see this thread [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
also in my signature is a guide from kevdog on how to connect from the command line.

---

### Post by NewDigger on 2008-02-02
I've followed the instructions, and now its kind of jammed at Manual Configuration and still hasn't connected.

I am using WPA for security. What confused me is how it connected the first time, but then lost connection and started to refuse to connect. I also can't detect any wireless networks when I scan for the, in the terminal now.

lsusb gives me the following.
Bus 003 Device 002: ID 046d:c502 Logitech, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0930:6532 Toshiba Corp. 
Bus 004 Device 003: ID 050d:705a Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 001 Device 001: ID 0000:0000  

Anything else I can try?

---

### Post by Hightide on 2008-02-02
HI newdigger

do you have a look at Kevdog';s wireless diagnostic as recommended by rustybronco?  it may help.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

regards

:)

---

### Post by Paris Heng on 2008-02-02
Hi, 

I also having problem in Belkin F5D7050 v4. 

I issued lsusb:

> heng@heng:/etc/init.d$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 006 Device 005: ID 050d:705c Belkin Components 
Bus 006 Device 004: ID 0951:1603 Kingston Technology 
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 1241:1233 Belkin 
Bus 001 Device 005: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000 

For the driver, I just installed through the synaptic:

Installed: **[COLOR="Red"]zd1211-source[/COLOR]**

I run well, I wonder why? Because, in the synaptic, I did not mentioned about Belkin.[COLOR="Blue"] Why, somebody tell me?[/COLOR]

> Hardware supported includes:

  Vendor/Name         USB id
  3COM 3CRUSB10075    6891:a727
  AOpen 802.11g WL54  07b8:6001
  iNexQ UR055g        1435:0711
  Sitecom WL-113      0df6:9071
  Telegent TG54USB    129b:1666
  TwinMOS G240        126F:a006
  Yakumo QuickWLAN    0b3b:1630
  Airlink+ AWLL3025   0ace:1211
  Zyxel ZyAIR G-220   0586:3401
  X-Micro XWL-11GUZX  0ace:1211
  Edimax EW-7317UG    0ace:1211
  Safecom SWLU-5400   07b8:6001
  Longshine LCS-8131G 07b8:6001
  Planet WL-U356      0ace:1211
  Sweex wireless 54MB 5173:1809
  Acer WLAN-G-US1     0ace:1211
  Trendnet TEW-424UB  0ace:1211
  DrayTek Vigor 550   0675:0550
  Asus WL-159g        0b05:170c
  Trust NW-3100

---

### Post by NewDigger on 2008-02-02
> **Hightide said:**
> HI newdigger

do you have a look at Kevdog';s wireless diagnostic as recommended by rustybronco?  it may help.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

regards

:)

I did look at it, but I don't have an internet connection to get the package since I can't use the wireless connection so I am slightly stranded in that matter.
Also if it worked 'out of the box' for the first 5 minutes or so, why would it suddenly just stop? That is what I am mostly confused about.

EDIT: Just been and looked back over the link and read about the Ra Link chipset. I then followed the instructions for that and it works!!!!!
Thank you for your help both.

I can finally leave Windows in the dust.

---

### Post by rustybronco on 2008-02-02
Sorry I didn't get back to you sooner but I have been wacking on a server that has been giving me fits (7.10 server and centos5), so I went an downloaded 6.06.2 server and what do you know it works fine. GLAD it's working for you.
```
lsusb gives me the following.
Bus 003 Device 002: ID 046d:c502 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 005: ID 0930:6532 Toshiba Corp.
**Bus 004 Device 003: ID 050d:705a Belkin Components**
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:0850 Logitech, Inc. QuickCam Web
Bus 001 Device 001: ID 0000:0000
``` 

> Card: Belkin FSD7050 (or is it F5D7050) (USB 802.11b/g 54 Mbps)
Chipset: rt73
usbid: **050d:705a**
Kevdog wrote a heck of a guide don't you think?

---

