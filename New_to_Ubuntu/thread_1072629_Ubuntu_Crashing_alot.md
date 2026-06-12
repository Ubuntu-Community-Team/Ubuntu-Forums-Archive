---
title: "Ubuntu Crashing alot"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Periswell on 2009-02-17
Hello

My computer keeps on crashing. When i am on programs like Blender or UrbanTerror, after a while the computer crashes. By 'crashes' i mean it stops for a second the some weird funky multicoloured hippie lines show up in places, forcing me to press the off button. It has happened to me 3 times today, has anyone got any ideas? I think it is something to do with it being in fullscreen (it only seems to crash on fullscreen programs like Blender and Urbanterror). Thanks in advance.

-joshua

---

### Post by handydan918 on 2009-02-17
What kind of video card are you running? If it's a nvidia or ATI, you may need to update your drivers. 
More info about the system will help eliminate bad guesses. Post the output of ```
lspci
```

---

### Post by Periswell on 2009-02-17
here is the lspci output:
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


-joshua

---

### Post by Periswell on 2009-02-18
No one can fix it?

i know it has been 13 hours since the last post but im doing some coursework in blender for my ICT GCSE and i cant have it crashing every 30 minutes.

-joshua

---

### Post by Cresho on 2009-02-18
you can launch blender in windowed mode
basically cd to your blender like I do..yours is diff..of course
```
cd ~/Installed_Programs/blender
./blender -w -w -p 600 500 801 601
```

your pc memory must of been altered rerouting video to something else.  CHeck your bios and add more memory.  Make sure you are running more ram than what your pc needs.  I run at least 2gb.

also, open up your pc and check your heatsinks.  Make sure you don't have any fuzz growing (dust particles) within the fins which hinders cooling.  THose hippie lines you are reffering to seems like incompatible drivers.  I suggest you stick an nvidia in your pc.

---

### Post by 3rdalbum on 2009-02-18
It could be a 3D driver problem, but the symptoms sound like the infamous Xbox 360 problems, except that your computer doesn't have a red ring of death :-)

Check that your computer's fans are working. If they have a speed selector, try putting them on "Medium". If your computer has a dust filter at the front, check it and clean off any dust. If that fails, make sure your system is up-to-date.

Otherwise, your power supply might be on its way out (not giving enough power when you're using 3D) or the graphics chip itself might be problematic. Intel graphics uses system RAM, doesn't it? Then you'd want to run Memtest for as long as possible.

It wouldn't hurt to check Gnome System Log's "messages" section and see if the kernel has logged any sensor warnings at the time of the crashes.

---

### Post by Periswell on 2009-02-18
ok thanks for the help.

im not going to run it in a window './blender -w -w -p 600 500 801 601' as it gets all glichy when i put my mouse to the edge of the screen (because i am not using the blender from the repositories as it is out of date and instead using one that i downloaded off the website) My computer always gets to hot, after a while of leaving the laptop on, the touchpad can burn your fingers, no joke. and there is nothing in the fan.

-joshua

---

### Post by 3rdalbum on 2009-02-18
Well there's your problem - laptop temperatures are always higher than desktop temperatures. If the touchpad is getting too hot to touch, then your graphics chip is likely to be boiling! You might want to invest in one of those cooling pads with the fans in it, or use a desktop computer for your gaming and 3D animation. Desktops are much much faster-per-dollar so you'll probably enjoy intensive computing tasks more on a desktop, not to mention having a bigger monitor :-)  It's more difficult to overheat a desktop too.

---

### Post by Cresho on 2009-02-18
> **3rdalbum said:**
> Well there's your problem - laptop temperatures are always higher than desktop temperatures. If the touchpad is getting too hot to touch, then your graphics chip is likely to be boiling! You might want to invest in one of those cooling pads with the fans in it, or use a desktop computer for your gaming and 3D animation. Desktops are much much faster-per-dollar so you'll probably enjoy intensive computing tasks more on a desktop, not to mention having a bigger monitor :-)  It's more difficult to overheat a desktop too.

Yup!  Overheating is the problem.  Either your fans don't work anymore or ....why dont you get one of these.
[http://news.cnet.com/8301-17938_105-9700201-1.html](http://news.cnet.com/8301-17938_105-9700201-1.html)

---

