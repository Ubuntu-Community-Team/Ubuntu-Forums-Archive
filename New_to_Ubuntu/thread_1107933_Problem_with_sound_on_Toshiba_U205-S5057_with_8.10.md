---
title: "Problem with sound on Toshiba U205-S5057 with 8.10"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by damianpastor on 2009-03-27
Hi, I have a Laptop Toshiba Satellite U205-5057, and a few months ago I installed Ubuntu Desktop 8.10. The sound didn't work since then. I tried all the sound fixes i founded, but nothing works to me. I tried to update alsa drivers, installing pulse audio, alsamixer and all the tips i founded in the web but nothing works to my toshiba laptop. In the System>Preference>Sound have the "Analog Device AD1891 (OSS Mixer)" and others refered to the same analog device "(AD198x analog)" Please help me. 

Thanks
Damian

---

### Post by Narvinye on 2009-04-16
I'm running a Toshiba A215 AMD with ATI chipset for audio.  Fortunately I've never had an issue with sound but from 7.04 and on I've had issues with capture and wireless on each install.  I'd recommend posting the output of the lspci command so that we can see what PCI items are in use for sound.  

Even though I've never had issues with sound output I did notice a drastic difference when I installed the 9.04 beta. Right off the bat the wireless and capture worked on the native install.  I'm stoked!

I also installed the 9.04 beta on my brother's Gateway and everything worked on the native install.  If you have your home directory on its own partition (highly recommended) it may be worth it to install 9.04 to see if it helps.  I always think there could be a conflict when installing multiple drivers for the same card but I'm not sure it that is true.

:)

---

### Post by damianpastor on 2009-04-22
Here is the lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Regards
Damian

---

### Post by Choobie on 2009-04-24
It looks like we have the same sound card.

From my lspci:

```
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
```


Anyways, I remember that I also couldn't get audio to work in 8.10, what I eventually did on that version is install OSS. You could check this out if you are interested: [http://www.4front-tech.com/forum/viewtopic.php?t=1438](http://www.4front-tech.com/forum/viewtopic.php?t=1438)  But do that at your own risk, from what I understand is that OSS isn't considered "100% compatible" and isn't supported by the Ubuntu developers or community.

I found that sound *almost* works 100% out of the box in versions 8.04 and 9.04, so maybe it was just a hickup in 8.10 or something, thats all above my head. The only thing that seems not to work is my headphone jack (and I haven't tried recording either though) and I am still working on getting a fix for that.

---

### Post by damianpastor on 2009-04-27
Ok, I installed Ubuntu 9.04, but nothing was better. Now I will trying to use Fedora 10.I'll tell the results.

Thanks
Damian

---

### Post by damianpastor on 2009-04-28
I tried Fedora 10, but nothing went good for the sound. The problem is the same, some not supported driver hasn't let me hear the sound. Finally I intalled Windows and all go fine, sorry I pass again to the dark side, I didn't have choice.

Thanks anyway
Damian

---

### Post by sdcope on 2009-09-27
Bump.

I've been struggling with this for over a year now.  I give up.  Windows away.

---

