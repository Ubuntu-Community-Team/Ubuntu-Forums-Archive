---
title: "I love ubuntu but these issues are driving me nuts..."
date: 2009-11-12
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-12
1. No sound, very difficult to figure this out.
2. No flash....trust me I have tried everything. It spikes my CPU to 100% and darkens the page.
3. No control + key functions like CTRL + V or CTRL + X etc

Very fustrating.

I would prefer to blitz it all and do a clean re-install but I am very scared to lose my thunderbird email folders etc. I have been researching and have had some very helpful replies on thunderbird but I really have to feel that I can save my TB profile and then re-install in the working machine....

Would you re-install?

---

### Post by inportb on 2009-11-12
I'd reinstall only if I feel that it'd make a difference. Isn't there a .mozilla directory that you could backup?

---

### Post by falconindy on 2009-11-12
There's extremely few reasons to re-install Linux. More than likely, the issues that you have won't be fixed by a new installation.

---

### Post by camaron1 on 2009-11-12
I take it you are on 9.10
1-try unistalling pulseaudio (it fixed my audio)
2-If you've tried everything not much to tell you
3-Go to System>preferences>keyboard shortcuts

---

### Post by danastasio on 2009-11-12
tell us a little bit about your computer, we may be able to help you out. post the output of 
```
lspci
```
and 
```
uname -a
```
so we know what you are working with, and if you could tell us about your computer personally, that would be nice as well

also did you install the "software modem" in restricted drivers? I did and i lost my sound, uninstall it and see if that works

---

### Post by listerdl on 2009-11-12
[QUOTE=danastasio;8304761]tell us a little bit about your computer, we may be able to help you out. post the output of 
```
lspci
```

This Produces:

```
henry@TOSHIBA-laptop:~$ lspci
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
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```
 
```
uname -a
```

This produced:

```

henry@TOSHIBA-laptop:~$ uname -a
Linux TOSHIBA-laptop 2.6.27-15-generic #1 SMP Tue Oct 20 06:52:09 UTC 2009 i686 GNU/Linux



```


Thanks for the help!!!!!!!!!!!

---

### Post by unamanic on 2009-11-12
If you have the time and patience to fix it you will learn more than if you re install.  But whichever route you go, back-up, back-up, back-up. 

.mozilla = firefox settings (cookies, passwords)
.thunderbird -or- .mozilla-thunderbird (varies by distribution, not sure which ubuntu uses) = thunderbird email

---

### Post by impert on 2009-11-12
Try following the instructions [here]("http://ubuntuforums.org/showthread.php?t=205449") and [here]("http://ubuntuforums.org/showthread.php?t=766683") 
They have always worked for me.

---

### Post by listerdl on 2009-11-12
YES!!!!!!!!!!!

IT IS WORKING....

I did some googling and came across a post in these forums that worked!!

From Synaptic Package Manager

Any flash has to be uninstalled example:
gnash
swfdec-mozilla

and than install :
flashplugin-nonfree
flashplugin-nonfree-extrasound

THAT WORKED!!!!!!!!!!

Seriously - I dont really know what I did and why that worked but it did. Seruiously that has like taken me 6 hours to fix but I quite enjoy it though!

Thanks...

Now for the other two problems...sound and these ctrl key issues.....

I guess it is very satisfying fixing it, better when you understand why!

Thanks again guys

---

### Post by mr clark25 on 2009-11-12
> **camaron1 said:**
> 
1-try unistalling pulseaudio (it fixed my audio)

thanks, this fixed my audio problem to.

---

### Post by camaron1 on 2009-11-12
> **mr clark25 said:**
> thanks, this fixed my audio problem to.
Good, you may want to install now GNOME-ALSA MIXER to control your sound.

---

