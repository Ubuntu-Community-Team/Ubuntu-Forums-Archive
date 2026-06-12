---
title: "Is this a graphics card or installation problem?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by BlitzLio on 2010-06-21
After installation and a reboot, I finally get to the login screen. When logged in as virtual console 1, I tried press alt-f7 and also crtl-alt-f7 to get to the GUI mode but what appears on the screen next is just a black screen with this "_" , I waited for some time and nothing changes. May I know if this is installation error or graphics card error? I heard all Linux distros have Intel drivers for graphics cards.

---

### Post by Windows Nerd on 2010-06-21
> **BlitzLio said:**
> After installation and a reboot, I finally get to the login screen. When logged in as virtual console 1, I tried press alt-f7 and also crtl-alt-f7 to get to the GUI mode but what appears on the screen next is just a black screen with this "_" , I waited for some time and nothing changes. May I know if this is installation error or graphics card error? I heard all Linux distros have Intel drivers for graphics cards.

Wait, it booted into CLI mode? I am unsure why you are logging on to TTY 1 (AKA virtual console 1). For confirmation: did you just install Ubuntu, then on reboot, you didn't change _anything_ and ended up with a TTY 1?

If such is true, then it is likely a graphics card problem. Which graphics card do you have?

---

### Post by BlitzLio on 2010-06-21
Mine graphics card and my laptop specifications are:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller:_ [COLOR=SeaGreen]Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/COLOR]_
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

It just brought me to CLI mode and then black screen with "_" after I press crtl-alt -f7, just hangs there.
Do I need to do a reinstall? Using the test Ubuntu mode from the CD has no problem with the graphics.

I followed the installation instructions and nothing else. Maybe I should do a reinstall.

---

### Post by Windows Nerd on 2010-06-21
> **BlitzLio said:**
> Mine graphics card and my laptop specifications are:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller:_ [COLOR=SeaGreen]Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)[/COLOR]_
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

It just brought me to CLI mode and then black screen with "_" after I press crtl-alt -f7, just hangs there.
Do I need to do a reinstall? Using the test Ubuntu mode from the CD has no problem with the graphics.

I followed the installation instructions and nothing else. Maybe I should do a reinstall.
You have the same (almost, a slightly different model) graphics card (it is actually an onboard card) as I do on my laptop, and mine works flawlessly. If it was like this right after installation w/ no updates I doubt reinstalling would do anything. 

Can you get to a GUI interface by starting it from the CLI?

After logging in via CLI with the username and password you set during install, run this command:

```
sudo startx
```

If that does not work, maybe installing updates may do the trick:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BlitzLio on 2010-06-22
Sorry, I did not see your post earlier and started my reinstallation. I think it was probably because I did not connect my laptop to the internet while installing as I saw a downloading process occur during the reinstallation which never appeared in my first one.

Either way, thanks and your commands look pretty useful to me in the future.

---

### Post by Windows Nerd on 2010-06-22
Okay, cool, it all works now?

---

