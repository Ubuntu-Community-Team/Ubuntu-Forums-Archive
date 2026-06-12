---
title: "Freezing after log in music plays"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Dutch70 on 2011-02-18
Hi, 

I installed Kubuntu Maverick into Ubuntu Maverick, it worked fine for about a month. Now when I log into the "kde plasma workspace" (Kubuntu). The screen comes on for about 20-30sec. & everything works fine for that time. As soon as the log in music plays, it freezes instantly. It used to work fine most of the time. Not sure what changed, I believe it worked fine after my last kernel update. 

Ubuntu use to freeze on me, until I followed post #22 of this thread...
[http://ubuntuforums.org/showthread.php?t=1307001&page=3]("http://ubuntuforums.org/showthread.php?t=1307001&page=3")

I've done that in Kubuntu also, but it use to freeze at random times. Now it freezes every time as soon as the log in music plays.

Can anyone help me with this please?

---

### Post by Cracklepop on 2011-02-18
Turn off the login music?

---

### Post by Dutch70 on 2011-02-18
> **Cracklepop said:**
> Turn off the login music?

While I appreciate you trying to help cracklepop, but I seriously doubt that it's the music itself that's causing the problem. 

The music just signifies when you're actually logged in. So to rephrase...It freezes **as soon** as it finishes the log in.

---

### Post by NightwishFan on 2011-02-18
You might be surprised. It is worth a shot. My advice is unplug from ethernet if you have one, it might be network-manager crashing. Not sure if Kubuntu has a "safe mode" at the log in. Perhaps that may help.

---

### Post by inobe on 2011-02-18
why don't we go straight to the most likely problem, it ain't software, in order to verify that, tell us about that free pci-e slot, any cards video occupying it?

if yes, could you give the make and model?

---

### Post by Dutch70 on 2011-02-18
Thanks everyone, I tried unhooking my wireless usb adapter(desktop)
and firefox opens automatically (as it has been) after the login screen & it still freezes. <brrrr> 

Not sure how to turn off the login music, esp with it freezing.

Note: firefox & 2 instances of cairo dock we're opening on their own since the problem started. I closed both of the instances of cairo dock, but firefox keeps opening. 

> **inobe said:**
> why don't we go straight to the most likely problem, it ain't software, in order to verify that, tell us about that free pci-e slot, any cards video occupying it?

if yes, could you give the make and model?

I don't think there is anything in the pci-e slot. Integrated graphics card :) or am I missing something?

video card...
```
david@david--SR5350F:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:04.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```

---

### Post by NightwishFan on 2011-02-18
I hear various reports of trouble with that chip, it might be hanging on trying to enable desktop effects, but then again KDE is normally pretty good with knowing when it wont work. So at the moment I really do not have any solutions.

---

### Post by inobe on 2011-02-18
> **Dutch70 said:**
> 
I don't think there is anything in the pci-e slot. Integrated graphics card :) or am I missing something?

video card...
```
david@david--SR5350F:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:04.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```


that intel graphics is just way below low end, the intel drivers are the buggiest, the chip itself cannot handle compiz and/ or kwin affects

i am almost certain that if you stuck a pci-e nvidia card in there 6xxx series and up, and installed the nvidia driver, you wont see these frequent freezes.

i have never had a freeze on any linux desktop with my nvidia card!

it froze a lot on my laptop with intel graphics, i tried countless workarounds only to have slow desktop affects and poor video performance.

i hope my suggestions help

---

### Post by Dutch70 on 2011-02-18
> **inobe said:**
> that intel graphics is just way below low end, the intel drivers are the buggiest, the chip itself cannot handle compiz and/ or kwin affects

i am almost certain that if you stuck a pci-e nvidia card in there 6xxx series and up, and installed the nvidia driver, you wont see these frequent freezes.

i have never had a freeze on any linux desktop with my nvidia card!

it froze a lot on my laptop with intel graphics, i tried countless workarounds only to have slow desktop affects and poor video performance.

i hope my suggestions help

Thanks inobe & yes it is a pitiful video card. 
 However Compiz works great on a heavily modified Ubuntu 10.10, on the same computer. I've even got the extra effects going & haven't had any problems at all...**since, that is..** I followed post #22 in this guide.
[*[COLOR="Blue"]Intel 82945G[/COLOR]*]("http://ubuntuforums.org/showthread.php?t=1307001&page=3")

Until then it was random freezes nothing like what's going on with Kubuntu now.

Also, Compiz worked well in Kubuntu until a few days ago.

---

### Post by inobe on 2011-02-19
have a look what i got.

```
linux-boss:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Network controller: RaLink RT2800 802.11n PCI
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
**02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)**
```

an old nvidia pci-e card

kubuntu 10.10 64bit with kde 4.6, desktop affects are very good.

my system [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01151591&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=ca&lang=en&product=3548643](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01151591&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=ca&lang=en&product=3548643)

the nvidia integrated graphics were fine, i had the pci-e and didn't want it sitting on the shelf.''

i also have opensuse 11.3 64bit on here with kde4.6 with no performance issues.

your system is a bit better than mines besides the intel graphics!

the point, you may continue to see freezes, an when you fix it, once you run updates, things will go back to freezing.

---

### Post by Dutch70 on 2011-02-19
Nice, unfortunately I had never heard of Ubuntu or Linux when I bought this computer :( 

Matter of fact, I didn't know anything except how to browse the web. I used windows for about 3 mths before learning about & switching to Linux. Now, on this machine. I have Vista, Ubuntu & Kubuntu on the hdd & about seven other Linux distro's installed in virtualbox. 

We are getting off topic though, as I said...
Kubuntu worked great until about a week ago, so I'ts not that my video card can't handle it.

---

### Post by inobe on 2011-02-19
> **Dutch70 said:**
> 
Kubuntu worked great until about a week ago, so I'ts not that my video card can't handle it.

you can start here i hope you find a workaround.

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+intel+graphics&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+intel+graphics&ie=utf-8&oe=utf-8)

---

### Post by Dutch70 on 2011-02-19
> **inobe said:**
> you can start here i hope you find a workaround.

[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+intel+graphics&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+intel+graphics&ie=utf-8&oe=utf-8)

Thanks inobe, I've checked there a little. Haven't found anything yet.

Update: I am running Kubuntu 10.10 from a flash drive right now, and it's doing great so far. No compiz, but desktop effects are enabled.
Seems to me that it has to be in a setting, or something I've done in Ubuntu... that Kubuntu don't like.

Or it could be something in kubuntu. Why would cairo dock settings manager & firefox open on their own as soon as I login? 

Note  that I usually opened cairo dock set mngr in kubuntu to relocate cairo dock.

---

