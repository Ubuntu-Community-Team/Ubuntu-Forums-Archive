---
title: "Update Graphics Driver"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by JustMegawatt on 2009-08-09
Hello, I have recently tried to play WoW. The sound comes up just fine, it's just that I can't see a thing, not even the login screen. I hear the sound of the frost wyrm in the background roaring, and the other login screen sounds, but I cannot see a thing. I am sure it has to do with my graphics card.

This is my lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

My graphics card is Intel family chipset 965G. I have downloaded the update from [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/), the latest 64 bit version. It is now on my desktop, yet I do not know how to install it. I tried running the install.sh using the terminal, yet a window would open then it would just suddenly close. 

Please help, complete newbie here. Also, how would I run WoW.exe using wine? I tried ```
 wine wow.exe -opengl 
``` on the terminal, and it goes into the windows 32 folder and says it cannot be found. 

```
wine: could not load L"C:\\windows\\system32\\wow.exe": Module not found
```

---

### Post by jauntyjackalope on 2009-08-09
I'd look here...It has full instructions
[http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)

---

### Post by JustMegawatt on 2009-08-09
Yes well, you see, I already have it installed. I have tried adding -opengl to the WoW config.wtf file and yet, it still does not work. 

Let me describe it more thoroughly;

I click on the gnome icon at the top left corner, click on wine, click on programs, world of warcraft, then world of warcraft.exe. 

As soon as this happens, a launcher immediately pops up and it has all the info and everything on it. As in, the news updates show up, everything shows up, I am able to click on the links and it would open a firefox window with the link I clicked on.

Anyway, I skip all of this, since no one really reads the news, because it's a waste of time. Reading the news about WoW is a waste of time, is what I am saying. So then it runs WoW and WoW crashes. It pops up with an error. 

So, I found a way to fix this, by running it in windowed mode. After running it in windowed mode, it works out okay, but I cannot see a thing. It has to do with my graphics card.

My question was, how do I update my graphics card? Not, how do I make WoW run?

---

### Post by halitech on 2009-08-09
did you look at the instructions for installing the driver?

[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

---

### Post by JustMegawatt on 2009-08-09
I did not update my graphics drive, but after some tampering with the system, I got WoW to work. Thank you for the link to the guide by the way, that guide was way too complicated, not because it was hard to follow, but because most of the links did not work. Such as 

```
gitwhatever
```none of those worked.

I have a problem though. If I run it with OpenGL, it looks like this [IMG]http://justmegawatt.com/laptop/images/Screenshot-9.png

and if I run it without opengl, it lags then crashes in less than two minutes. I am currently going to try downloading the latest opengl to see if that owuld do anything. I will post backp my results, but if you have anymore advice, please help. I would love to upgrade my graphics driver. Please, help!

Update: Got it to work in great graphics
What I did: Turned OpenGL off, ran wine in full screen, ran WoW in full screen

Problems: Slow. Very, slow. It would take about 10-20 seconds to type in "Hello" 
Is there a solution to this? Here's the latest picture

[IMG]http://justmegawatt.com/laptop/images/screenshot-10.png

---

### Post by deBALZAC on 2009-09-02
I had the same problems here when I tried to run it in full screen mode.

So I turned off GL mode and then I started WoW in the windowned mode. This time the game worked fine.

Try it and let's see what you got.

Off course the best thing was to run it on full screen mode, but I don't know how.

---

### Post by pissedoffdude on 2009-09-02
> **JustMegawatt said:**
> \
My graphics card is Intel family chipset 965G. 
I don't think you'll have much luck being able to run WoW with that chipset, even with the latest drivers.  What I recommend you do is stick to windows for wow or try running it in d3d mode by adding the line SET gxAPI "d3d".  Don't run it in opengl mode, as intel's driver don't work with it too well.

---

