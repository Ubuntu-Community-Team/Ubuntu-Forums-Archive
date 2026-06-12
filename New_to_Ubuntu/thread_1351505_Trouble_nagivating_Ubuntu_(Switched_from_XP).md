---
title: "Trouble nagivating Ubuntu (Switched from XP)"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by Synoc on 2009-12-10
Ok fine, you all win I'm using Ubuntu now... so here's the typical starter questions form an X Windows user. what equates (if anything) to device manager? I'm still getitng used to pokin around in OS guts. I got my Wireless networking to work... somehow. it just started working... but it stops when I move upstairs (it wasn't enough to kill the signal when it was Windows... If I can get the first question answered I might be able to get the second one myself with research, but since I don't have the documtation on my Dell anymore (it's an Inspiron 1150 from 5 years go, dual-band Wireless card) I have a time finding my system information out without device manager. thought I had done all my homework early, but as always theory does not equate to practice. Would appriciate the help. thank you. PS I have a month before i st art up college again so we get to know each other well, I'm an aqaurius if it matters : )

---

### Post by heyho on 2009-12-10
There's not really a device manager as such, everything is accessed through the system>preferences and system>admimistration menus.

As for your wireless, the first thing to do would be to identify your wireless hardware.  This is usually achieved by opening up a teminal (applications>accessories>terminal), and typing 

```
lspci
```

Post up the output of this command, and we'll see what you have.

---

### Post by Matt__ on 2009-12-10
in addition to the lspci command you could use the "service tag" on the bottom of your dell and plug it into the dell website to get all the hardware info you need..[see link here](http://support.euro.dell.com/support/topics/topic.aspx/emea/shared/support/my_systems_info/en/manuals?c=uk&cs=ukdhs1&l=en&s=dhs&~ck=anavml)

---

### Post by Synoc on 2009-12-11
Data from terminal:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller


Also another fun question. lets say, somehow, at some point in time today around 4PM eastern time... my open office locks up and keeps me from saving my presentation for my college class due tomorrow (not that this happened or anything : ) ) how would I close the program if the "Close" button in the left menu doesn't work, and the "X" on the right doesn't work? (BTW, IF this did happen I saved it to my PC first, so no worries there)

---

### Post by Thelasko on 2009-12-11
> **Synoc said:**
> Also another fun question. lets say, somehow, at some point in time today around 4PM eastern time... my open office locks up and keeps me from saving my presentation for my college class due tomorrow (not that this happened or anything : ) ) how would I close the program if the "Close" button in the left menu doesn't work, and the "X" on the right doesn't work? (BTW, IF this did happen I saved it to my PC first, so no worries there)

Well, I'm on an older version of Ubuntu, but I use System>Administration>System Monitor.  It works just like the system monitor in Windows.

---

### Post by mcdjork on 2009-12-11
To close an unresponsive program, you can either go to System > Administration > System Monitor and click the Processes tab (like Task Manager in Windows) or you can add the Force Quit applet to your panel (right click on Panel, Add to Panel..., Force Quit).

---

### Post by Synoc on 2009-12-11
ok I am currently connected vie Ethernet. my wireless won't even pick up the signal now or tell me there is one. Information for my card is posted above (had it working yesturday)

EDIT: Nevermind Unbuntu lost my connewction info had to set up a new connection, then it found it. but can I make it search for wi-fi even if they are secured Wi-fi? soI odn't have to hunt it down?

---

### Post by Matt__ on 2009-12-12
Hi Syn,
heres the broadcom wireless setup that applies to your wifi

[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4309](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4309)

good luck with it :)

---

### Post by 3rdalbum on 2009-12-12
If the program freezes up and you click the X, you will be asked if you want to force quit the program. When you click the Force Quit button, it will IMMEDIATELY be killed.

If you don't get any response from clicking the X, then your graphical server (Xorg) has probably frozen up; you can force Xorg to restart by pressing Alt-SysRq-K (sometimes the SysRq key is marked "Print Screen" or "Pr Sc"). This will kill all graphical programs.

---

### Post by Synoc on 2009-12-12
ok so got my wireless working... all those posts and it now decides on start up to download its own drive with fwcutter... whatever works... any ideas why my wireless range seems to be cut in half from what i was with Windows? can't evne take my laptop foa walk to get it some exercise, it's getting FAT (and I don't mean the file table).

---

### Post by Bigtime_Scrub on 2009-12-12
> **Synoc said:**
> ok so got my wireless working... all those posts and it now decides on start up to download its own drive with fwcutter... whatever works... any ideas why my wireless range seems to be cut in half from what i was with Windows? can't evne take my laptop foa walk to get it some exercise, it's getting FAT (and I don't mean the file table).

If you go to System -> Administration -> Hardware Drivers

what options are presented for you and do have an option to install, reboot, or is something already enabled?

---

### Post by Synoc on 2009-12-12
> **Bigtime_Scrub said:**
> If you go to System -> Administration -> Hardware Drivers

what options are presented for you and do have an option to install, reboot, or is something already enabled?
Broadcom B43 Wireless driver is activated

---

