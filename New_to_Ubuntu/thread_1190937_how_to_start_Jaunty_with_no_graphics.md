---
title: "how to start Jaunty with no graphics?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-06-18
I need to install Nvidia drivers for a graphics card.

My old desktop has an Intel 82565G graphics controller built in to the motherboard and this is (I think) interfering with driver installation.

How does one configure Jaunty so that Ubuntu boots into a terminal?

That way I could go through the installation procedure with the new card (selected in BIOS at boot) and not have to worry about which config file Ubuntu is seeing.

---

### Post by fooman on 2009-06-18
boot up to the desktop,  then press ctrl-alt-f1

that will drop you to a console (terminal?),  once there,  login with your user name & password,  then type the following:

```
sudo /etc/init.d/gdm stop
```

that will kill the x-server and allow you to proceed with the nvidia installation.

---

### Post by raymondvillain on 2009-06-18
I didn't explain things clearly.

If I try to boot with the Nvidia card, Ubuntu hangs as soon as it goes into graphics mode.

I have to boot directly to a screen without graphics.

Is that possible?

---

### Post by fooman on 2009-06-18
as you boot up and you see the grub screen....try booting into recovery mode.  after that loads up...choose "xfix" from the menu.  when that completes, choose "resume normal boot"

see if that gets you up to the desktop. 

you might also try "drop to a root shell" from the recovery mode menu. that will get you to a terminal like console.    trouble with that is that a x-server will still be running and *may* not allow you to install the driver.

try the xfix option first....good luck.

---

### Post by overdrank on 2009-06-18
Ok raymondvillain we are going round in circle [here]("http://ubuntuforums.org/showthread.php?p=7475370#post7475370") and [here]("http://ubuntuforums.org/showthread.php?t=1190471")
and now here.
Creating new threads is not going to help your issue. It will cause confusion I believe. 

So you are installing a new graphics card on your system, have you disabled the onboard intel graphics in bios?
Is the new graphics card pci or agp?
You do get video from the new graphics card, have you tried booting into recovery mode and using xfix?

---

### Post by The Cog on 2009-06-18
You can prevent the GUI starting with:
**sudo chmod -X /etc/init.d/gdm**
You can test X from here with the command **startx**

**sudo chmod +X /etc/init.d/gdm**
will re-enable starting the GUI at boot.

---

### Post by raymondvillain on 2009-06-18
Right you are, overdrank.  My apologies.  It seemed like nobody was reading things that were more than an hour old.

New graphics card is a "PNY VERTO Nvidia GeForce 8400 GS" PCI.

Onboard graphics are easy to disable in BIOS.  I even have 2 monitors hooked up, one to each video output.

I went through the steps ([http://ubuntuforums.org/showthread.php?t=1125400&highlight=default+runlevel](http://ubuntuforums.org/showthread.php?t=1125400&highlight=default+runlevel)) very carefully to install Nvidia drivers for linux.

All seemed well at each step of the install.  Then, I re-boot, disable the onboard graphics and enable the nvidia 8400 GS, exit BIOS setup, and the computer comes back up with the usual messages ("Grub loading, grub 1.5, etc.") nice and clear on the monitor connected to the new graphics card.  Finally the Ubuntu logo appears and everything comes to a halt.  All is kaput.  I have to cut the power to the box, restore power, and press the start button.  And restore the onboard graphics in BIOS, and from there, run with default graphics.  Nothing coming out of the Nvidia board.

I tried booting into recovery mode but the installation locked up very quickly.  Many lines of text scrolling by quickly, then:

udevd-event[1204] /bin/mkdir /var/run/network: abnormal exit

and then it would completely hang.

Nothing I did could prevent hanging (or lockup) except to re-boot, enable the onboard graphics, and have Ubuntu "re-configure" the graphics.

I have tried xfix, it did not help.  Are there any special tricks to running xfix?

Can you offer any other suggestions?

Thanks for all your help.

P. S.  I can return the new card and exchange it for one that is known to work.  Do you have a favorite?  Lots of Ubuntu users are posting to the Ubuntu forums with nvidia problems.  Is ATI any better?

---

### Post by stalkier on 2009-06-18
> **raymondvillain said:**
> Right you are, overdrank.  My apologies.  It seemed like nobody was reading things that were more than an hour old.

New graphics card is a "PNY VERTO Nvidia GeForce 8400 GS" PCI.

Onboard graphics are easy to disable in BIOS.  I even have 2 monitors hooked up, one to each video output.

I went through the steps ([http://ubuntuforums.org/showthread.php?t=1125400&highlight=default+runlevel](http://ubuntuforums.org/showthread.php?t=1125400&highlight=default+runlevel)) very carefully to install Nvidia drivers for linux.

All seemed well at each step of the install.  Then, I re-boot, disable the onboard graphics and enable the nvidia 8400 GS, exit BIOS setup, and the computer comes back up with the usual messages ("Grub loading, grub 1.5, etc.") nice and clear on the monitor connected to the new graphics card.  Finally the Ubuntu logo appears and everything comes to a halt.  All is kaput.  I have to cut the power to the box, restore power, and press the start button.  And restore the onboard graphics in BIOS, and from there, run with default graphics.  Nothing coming out of the Nvidia board.

I tried booting into recovery mode but the installation locked up very quickly.  Many lines of text scrolling by quickly, then:

udevd-event[1204] /bin/mkdir /var/run/network: abnormal exit

and then it would completely hang.

Nothing I did could prevent hanging (or lockup) except to re-boot, enable the onboard graphics, and have Ubuntu "re-configure" the graphics.

I have tried xfix, it did not help.  Are there any special tricks to running xfix?

Can you offer any other suggestions?

Thanks for all your help.

P. S.  I can return the new card and exchange it for one that is known to work.  Do you have a favorite?  Lots of Ubuntu users are posting to the Ubuntu forums with nvidia problems.  Is ATI any better?

I have had good luck with both ATI and NVidea Chipsets with Linux. I have heard alot of people have trouble with newer ATI cards, however. The newest one I had was a couple years old and was a AGP slot on a AMD Athlon XP CPU. I am running a XFX 8500GT on my desktop (PCIe) and have no problems. I believe I am using the NVidea System tools thing or whatever it is called. All was enabled thru Proprietary Drivers.

---

