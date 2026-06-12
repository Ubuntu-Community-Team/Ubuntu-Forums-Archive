---
title: "wireless enabled, but can't connect"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by violetcandy on 2010-05-01
I have only had Ubuntu 10.04 for a day. I run a dual OS with Win XP Home on my Dell Inspiron B130. I'm working on getting rid of Win altogether. I figured out how to enable my wireless card (Broadcam B43) but it just won't connect. I know I'm entering the SSID and password right. I also added the MAC address. I'm currently using my ethernet cable but there is no a/c in this room!

```

```violetcandy@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

---

### Post by Jon Monreal on 2010-05-01
Have you tried going to System>Administration>Hardware Drivers and seeing if the drivers are available?

---

### Post by violetcandy on 2010-05-01
Yeah, that's how I found my Broadcam B43 driver. 
[http://picasaweb.google.com/lh/photo/pG0_ZNdns7feD7ixscpcig?feat=directlink](http://picasaweb.google.com/lh/photo/pG0_ZNdns7feD7ixscpcig?feat=directlink)
[IMG]http://picasaweb.google.com/lh/photo/pG0_ZNdns7feD7ixscpcig?feat=directlink[/IMG]

---

### Post by Jon Monreal on 2010-05-01
Hello,

Could you try [these instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Internet%20access") (stopping when you get to "LiveCD/LiveUSB" and try again?

If this doesn't work, there are other things to be tried.

Thanks.

---

### Post by violetcandy on 2010-05-02
I'm not sure when this happened but I was able to actually see my wireless network earlier. Now it says "wireless disabled". Btw, it said this before your last instructions so it wasn't the new driver. I'm more confused now.

---

### Post by Jon Monreal on 2010-05-02
I have to run for now, but I'll be back tomorrow.

If your laptop has a physical wireless on/off switch, make sure it is turned on. Also try right-clicking on the NetworkManager (wireless) Applet and make sure "Enable Wireless" is checked.

Thanks.

---

### Post by david20063 on 2010-05-02
Not sure if you have this problem or not but I have a button on my keyboard to toggle my wireless on and off and if I accidentally hit it I have to hold it in for about 10-30 seconds to get it to turn back on.

---

### Post by violetcandy on 2010-05-02
I forgot I had turned off the wireless. That's on again, I can see my wireless network. Wireless is definitely enabled. I'm back at square one. Thanks for your time though!!!

---

### Post by xumuk37 on 2010-05-02
```
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
sudo reboot
```

---

### Post by violetcandy on 2010-05-02
Reinstalled bcmwl. It still says "disconnected" under "Wireless Networks". It tries to connect but just doesn't. It's not giving me a error message. Is there a log I can check to see if there is an error? I really appreciate you guys helping me out. It's hot in here!

---

### Post by violetcandy on 2010-05-02
Now my internet doesn't work at all on my computer! Please help!


Update:
(Currently reformatting so I can at least use my "wired" network.)

---

### Post by violetcandy on 2010-05-02
I reinstalled Ubuntu 10.04, updated my driver (Broadcom B43), rebooted and voila! My wired and wireless both work. I don't even understand but that's ok.

---

