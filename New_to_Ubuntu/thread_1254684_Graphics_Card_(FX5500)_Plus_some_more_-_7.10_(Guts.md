---
title: "Graphics Card (FX5500) Plus some more - 7.10 (Gutsy)"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by IkeRay on 2009-08-31
First, as you can see, I'm still on Gutsy as I don't use ubuntu as much as I should, I mainly use windows.  well, my windows crapped out on me, got over run with vundo and viruses that corrupted the boot and I can't seem to get recovery console to run...it sucks.  word of the wise for windows users, if you have a faint vundo attack, don't leave your computer on for 3 days without being there, even if you THINK you cleaned the computer, vundo is a pain.

SO, here I am with ~500mb ubuntu hard drive space which means I can't update to 8.04 (?) because it needs 700mb free.  any work around?  is there a way to increase the partition size without having to delete said partition, or would it be easier to burn a 8.04 live cd and re-install/update that way?

as for the graphics card, I went through the System>grapics and installed the nVidia that matched the card (FX generic) and the onboard graphics spit out snow, restarted with card now installed and monitor remains black after GRUB menu but remains active, if I switch to onboard it goes idle.  its a CRT connected via VGA, FX5500 AGPx4, if that matters.

when I tried to do installs, I keep getting errors thrown, but not patient enough to read through them, I figured it's because I'm on 7.10.

finally, is there a way to scan windows registry or directory via linux or would I just be able to scan files not startup entries?  I know this isn't a windows forum, but the problem with XP is that it boots and shows the background, but no icons, no task bar, alt+ctrl+del/shift+ctrl+esc yields "task manager disabled by admin" even though the only user IS the admin.  safemode is the same way.  recovery console is asking for admin password which is supposed to be blank, but its telling me its wrong.

thanks, even if you can only help with the ubuntu issues :)

---

### Post by tgeer43 on 2009-08-31
Provided the current partition layout allows it you can increase the size of your Ubuntu partition without affecting its contents by running 'gksudo gparted' in a terminal or by selecting 'Partition Editor' from the System->Administration menu.

However, since you already have issues with your current Ubuntu installation I would recommend saving any important data from your 7.10 installation and then reformatting the partition. Then you can install the latest release, 9.04 Jaunty from Live CD. 

You'll be better off in the long run.

tgeer

---

### Post by Mark Phelps on 2009-09-01
> **IkeRay said:**
>  ... finally, is there a way to scan windows registry or directory via linux ... 
If you Google for Avira rescue CD, you will find sites where you can download an ISO image and burn the Avira antivirus CD.  You can then boot from this and perform a virus scan of your machine.

---

### Post by IkeRay on 2009-09-01
ok, I'm kind of stuck now.  this is my first and only linux.

I disconnected my nVidia card since it apparently wasn't working and reconnected the monitor to the onboard graphics, but now all I get is snow when ubuntu loads the graphics/startx.  I've been doing lots of searches but can't find a fix.  also, I apparently did something bad, when I type startx now I get > no screens found
fatal IO error 104 (Connetion reset by peer) on X server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

I also tried

> startx --display :1
and still getting same error.

alt+ctrl+f7 doesn't do anything.


I don't have another computer to burn a CD on, so I need to get the GUI working again on linux so I can burn a CD for the new distro and try that repair CD for windows....

---

### Post by LewRockwell on 2009-09-01
you need to do two things:

one, scrounge up another hard drive so you can set this one aside

two, find a computer buddy so you can get some fresh CDs burnt without messing with your machine and it's current problems/questionable status


get the latest Ubuntu 9.04 Jaunty Jackalope LiveCD, put all the hardware you desire into the machine as you like(while you've got it open you should really max-out the ram since it is so free/inexpensive these days), and boot up the LiveCD and see how your system performs(again, scrounge up another hard drive so you don't lose valuable data from your problem drive)


then, once you've got a fresh install of Ubuntu you'll be able to burn that Avira rescue disk for use with your buggered drive and hopefully debug it so that you can install it in your system as a slave drive to harvest the data(and then perhaps use it as a secondary drive)

.

---

### Post by IkeRay on 2009-09-01
> **LewRockwell said:**
> you need to do two things:

one, scrounge up another hard drive so you can set this one aside

two, find a computer buddy so you can get some fresh CDs burnt without messing with your machine and it's current problems/questionable status


get the latest Ubuntu 9.04 Jaunty Jackalope LiveCD, put all the hardware you desire into the machine as you like(while you've got it open you should really max-out the ram since it is so free/inexpensive these days), and boot up the LiveCD and see how your system performs(again, scrounge up another hard drive so you don't lose valuable data from your problem drive)


then, once you've got a fresh install of Ubuntu you'll be able to burn that Avira rescue disk for use with your buggered drive and hopefully debug it so that you can install it in your system as a slave drive to harvest the data(and then perhaps use it as a secondary drive)

.

so there is no work around for the graphics error?  if I could simply get this to boot correctly again (never should've tried installing that graphics card on it) then I can use this distro to burn the cd's.  I don't have any family that lives near me, and I don't really see "friends" outside of my family...

I guess I can wait until tomorrow or so and use my brother's computer to burn some cd's.  the computer I'm on now is a win2k but it doesn't have a cd/dvd burner, any chance I can boot using a USB drive?

also, this RAM IS maxed out...512mb pc133, 1.4ghz celeron.  that computer does everything I need it to do typically, but has been fuddled up, both by viruses and myself apparently, that its now unusable.

---

### Post by IkeRay on 2009-09-01
sudo lshw -C video
> 
Description: VGA compatible controller
product: 82815 Chipset Graphics Controller (CGC_
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 04
width: 32 bits
clock 66mhz
configuration: driver=i810_smbus latency=0 module=i2c_i810


created a new /etc/X11/xorg.conf by 

first, close any X session
$ sudo /etc/init.d/gdm stop

create a new xorg.conf
$ cd /etc/X11
$ sudo Xorg -configure

move the new config
$ sudo mv xorg.conf.new xorg.conf

the file now reads
> 
Driver "intel"
VendorName "Intel Corporation"
BoardName 82815 CGC
BusID PCI:0:2:0


does that look right?  its still snow.  its not really "snow" like the old rabbit ears antenna's got, its lots of horizontal lines flickering (and snow like).


also at startup I get > failed to start the X server (your graphical interface).  It is likely that it is not set up correctly. Would you liek to view the X server output to diagnose the problem?  <yes>

> /etc/gdm/failsafeXServer: line47 [: too many arguments
Warning: Failsafe mode was already attempted winthin 30 seconds.
Warning: Falling back to gdm to report the issue. <ok>

> The X server is now disabled.  Restart GDM when it is configured correctly. <ok>

then snow, so I press alt+ctrl+F1 [Enter] and log in

typed sudo nano /etc/gdm/failsafeXServer  but don't know how the lines are counted.  are they lines only with text or all lines including blanks?

---

### Post by IkeRay on 2009-09-01
update:

got the GUI to finally load, and changed drivers back to intel graphics.
followed - 

[quote=DaddyX3]This is booting from hard drive? IF so hit esc key after BIOS post you will get to grub select (recovery mode) from listed kernels.

when it starts to load you should get dropped at a command prompt after it has loaded a basic set of programs to ram.
should say something like "enter password: (or Ctrl+D for maintenance). Enter password then Type:
dpkg-reconfigure xserver-xorg
follow all the prompts with arrow keys, spacebare to tick things, and enter to accept. It will ask you if you want it to try and automatically detect video card, say yes>> next screen you should be able to review what it came up with and have the option to select a different driver from what it has selected for you, select vesa instead of "nv" or "nvidia" continue through all the remaining prompts (defaults are usually just fine, but pay attention) Have you already done this or is it possible?[/quote]

rebooted and it works flawlessly, now I'm burning 9.04, but question.  will my system be able to handle 9.04?  7.04 works fine but my system is lacking for most OS's...1.4ghz celeron 512mb RAM 128mb graphics card (currently pulled)

---

