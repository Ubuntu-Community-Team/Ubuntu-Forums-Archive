---
title: "WPC11 version 4 help"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by dmb83fan41 on 2006-11-25
I could really use some help on getting my Linksys WPC11 version 4 wireless card to work.  I have spent a few hours going through different forums but I keep getting more confused.  I am new to Ubuntu so that could be the cause of my headaches with trying to learn this.  If anyone could guide me through this I would forever thankful. :)

---

### Post by FrodoB on 2006-11-25
Please provide the output of:

lspci

iwconfig

Also provide the version of Ubuntu that you are using please.

---

### Post by dmb83fan41 on 2006-11-25
I am using version 6.06 of Ubuntu.  Thank you for any help you have.  Below is the requested info...

**lspci:**
brian@Laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
0000:02:04.1 CardBus bridge: O2 Micro, Inc. OZ6933/711E1 CardBus/SmartCardBus Controller (rev 01)
0000:03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
[B]
iwconfig:[/B]
brian@Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b  ESSID:"3038home"
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated
          Bit Rate=11 Mb/s
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=21/100  Signal level=-31 dBm  Noise level=-177 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by FrodoB on 2006-11-25
You are fortunate. This device is recognized by the Linux kernel. 

You just need to configure it using the GUI tools as shown here:

[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

Good luck.

---

### Post by dmb83fan41 on 2006-11-25
I have no idea what my WEP key is.  Do I need to have this to continue.  I did try without it and it seems to take a long time to configure.

---

### Post by FrodoB on 2006-11-25
You need to go into your routers setup and determine if you have a WEP key and if so what it is.  The router's key and the Ubuntu machines must match.

If you need to make common keys for your router and Ubuntu, this site can help you:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

---

### Post by dmb83fan41 on 2006-11-25
By changing or adding a new WEP key will I have to update the key on my other wireless machines (xbox 360, another notebook, desktop computer)?

---

### Post by dmb83fan41 on 2006-11-25
I did add WEP protection, but I was still unable to get my wireless card to connect to the internet.  Ugh, I am so close.  I just can't figure it out yet...it sees it there, but has it as disconnected.

---

### Post by FrodoB on 2006-11-25
At this stage it is usually a WEP key issue. Just check everything carefully. 

If it is setup correctly you should be able to control your connection using:

sudo ifdown wlan0

sudo ifup wlan0

at a terminal prompt, or through the Networking control panel.

---

### Post by Metaljaz on 2006-11-25
i have been following this post because i to am having problems with my internet under ubuntu 6.06LTS. i was able to access the net and check mail until i turned the computer off and turned it back on the next day. Now no internet. When i run lspci and iwconfig my card is also detected. I am going to try the link that was provided by FrodoB and see what happens.

---

### Post by dmb83fan41 on 2006-11-26
Keep me posted :-k

---

### Post by dmb83fan41 on 2006-11-26
I was finally able to get my wireless card to work after sacrificing my wireless setup.  I simply set my router to factory settings and used the name "Linksys" on Ubuntu.  It saw it right away and has been connected ever since.  I hope in the future though to re-setup my secure network.  I really have a headache right now, but I am so happy that I “stumbled” into setting this up.  Thanks to everyone for your help.

---

