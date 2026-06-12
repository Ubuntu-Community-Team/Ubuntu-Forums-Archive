---
title: "upside down webcam in website?"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by soylentcola on 2011-06-11
So my webcam runs fine in Cheese (which is really the only webcam program I use) but when I try to run it online through a website (i.e. [this one]("http://robo.to")) the webcam shows upside down...

I'm on an ASUS K60I and I'm not really sure how to fix this.  I've tried searching through the forums but it seems like the fixes there are for installed programs and since this isn't installed it doesn't really help.

Is there anyone who could help out?

**Edit:** It shows up upside down in Skype as well. D:

---

### Post by jtarin on 2011-06-11
Have you checked Cheese Special Effects to see if "Vertical Flip" is enabled? I know it's basic, but sometimes the basic, obvious answer works.  

if not.......[See if this is ]("http://ubuntuforums.org/showthread.php?t=838210") is applicable to your cam.

---

### Post by wojox on 2011-06-11
What happens if you turn the camera upside down? :p

---

### Post by jtarin on 2011-06-11
> **wojox said:**
> What happens if you turn the camera upside down? :p
The keyboard falls apart.:p

---

### Post by jtarin on 2011-06-11
[And another fix.]("http://forums.linuxmint.com/viewtopic.php?f=49&t=33109&start=0") Possibly easier.

---

### Post by soylentcola on 2011-06-11
I'll check with results in a moment.

I should note that it's a built-in cam as well.

---

### Post by soylentcola on 2011-06-12
```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 13d3:5130 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

neither solution worked, and I've posted my lsusb output (since it's a built-in camera I don't think it will show up.  I installed lbv4l-0 as well, no luck. =\

**EDIT:** I should also note that the online site I'm using to record is doing so through adobe flash...if that helps narrow down any possible issues.

---

### Post by jtarin on 2011-06-12
Can you detect your device with the command "usb-devices"?

---

### Post by soylentcola on 2011-06-12
I'm guessing it's the second one (Sonix Technology USB 2.0 Camera)

```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=5130 Rev=12.11
S:  Manufacturer=Sonix Technology Co., Ltd.
S:  Product=USB 2.0 Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1a.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=06 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=07 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=08 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.38-8-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

and the driver is uvcvideo so I'm wondering why that first link you gave didn't work... hmm...

---

### Post by soylentcola on 2011-06-12
Okay, I ran gstreamer-properties and the webcam showed up in the /dev/video0 folder and it runs right-side up...gonna fiddle around a bit with it more to see what happens.

---

### Post by NightwishFan on 2011-06-12
I have this issue as well. The camera is actually 'installed' upside down. Gstreamer manually flips it I assume. So far I have not located a fix.

---

### Post by jtarin on 2011-06-12
libv4l.....do you have installed? Maybe a newer version? From what I can gather this is what controls that behavior.

---

### Post by soylentcola on 2011-06-16
As it turns out IMC Networks IS the camera (after doing a bit of searching that's what I found out) so I'm going back to retry that original link you gave me to the forum post on the fix, I'll let you know how it goes. :D

---

### Post by soylentcola on 2011-06-16
m'kay, so I have libv4l installed, but I'm not 100% sure how to get it to work when I'm using my webcam through a website.  I tried running that terminal script and opening chromium, but it didn't help...

---

### Post by jtarin on 2011-06-16
I dunno.You might ask on the website.

---

