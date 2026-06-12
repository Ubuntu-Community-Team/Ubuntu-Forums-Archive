---
title: "Software Centre??"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by chris0108 on 2010-01-19
Just started using, two days, find it really good just having a few problems, first one is my wireless connection it just wont connect, the second one is with the software centre, when i go on it everything comes up but there is no install or remove option (they are there but not highlighted) do i need to change something?

Many thanks Chris

---

### Post by Merk42 on 2010-01-19
I don't know much about fixing wireless cards, but I do know that you'll need to explain which card you have.

Are you running Software Center simply by clicking on it from the applications menu?

---

### Post by nick_goodfate on 2010-01-19
you must be connected to the web, to install from software center ....

---

### Post by Methuselah on 2010-01-19
[Nevermind, nick_goodfate explained]

---

### Post by chris0108 on 2010-01-19
i have connected to web via the lan cable at present, i have gone to applications to open the software centre, now i have got the install option coming up,i hadnt put in my email address! Only problem now is it says the download is not avalible?

Thank you for the fast replies, i will post about the wireless on the correct forum section with more info.

---

### Post by nick_goodfate on 2010-01-19
take a look here : [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
or try to install the software you want with synaptic System->administration->synaptic package manager , or with apt-get in terminal. for example if you try to install VLC . open synaptic and write to the search field "vlc" , check for install the first package called "vlc and accept every other package it needs to install with it . Or tyoe in terminal > sudo apt-get install vlc

---

### Post by warfacegod on 2010-01-19
The reason Ubuntu S.C. isn't working is bevause it isn't asking for your password. To bypass this:

right click your main menu (where it says Applications,Places, System) and select Edit Menus. In the window that opens, highlight Ubuntu Software Center and click properties over on the right. In that window where it says Command: replace/user/bin.... with this:

```
gksu software-center
```

---

### Post by chris0108 on 2010-01-19
:D:D:D:D Thank you, went on the synaic package manager downloaded one game, which went perfect, and now downloading something with the software centre.

Spot on advice, many many thanks

---

### Post by warfacegod on 2010-01-19
Glad to help. AS far as your wireless goes. Try going to: System> Admin.> Hardware Drivers and activating the recommended wireless driver if there is one there. While you are there, you may want to activate your video driver as well.

---

### Post by Redmage913 on 2010-01-19
If you have a Broadcom wireless card and neither of the hardware drivers...drivers (forgive the double word usage) work, you might have to reinstall the package.  

<Lifted from Ubuntu Mini> [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

You might have to reinstall the [COLOR=#000099]bcmwl-kernel-source [COLOR=black]package.

NOTE: This is only specific to computers with Broadcom cards that don't work out of the box.  If you can connect with your wired but not wireless card that might be the problem.
[/COLOR][/COLOR]

---

### Post by warfacegod on 2010-01-19
Applications> Accessories> Terminal:

```
sudo lspci
```

will tell you what your wireless chipset is. It will be one of the lines that says; Ethernet controller.

---

### Post by chris0108 on 2010-01-19
In the hardware drivers it says no proprietory drivers in use, now i find this strange cause i installed the belkin driver using ndiswrapper only this morning?

sudo lspci brings this up ;

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Belkin Device 701f (rev 20)

I have downloaded the latest drivers from the belkin website.
Funny thing is when i was reading up about the belkin card on here it recommeneded using the realtek 8185 drivers, when i tried with those it didnt recognise them at all, with the belkin drivers it knows what they are but says it cant test the hardware?

Sorry that was a bit long winded

---

### Post by warfacegod on 2010-01-19
If you manually installed them they won't show in Hardware Drivers. I suggest you post another thread in Networking & Wireless and mark this one solved under thread tools.

---

### Post by chris0108 on 2010-01-19
No problem, many thanks again

---

