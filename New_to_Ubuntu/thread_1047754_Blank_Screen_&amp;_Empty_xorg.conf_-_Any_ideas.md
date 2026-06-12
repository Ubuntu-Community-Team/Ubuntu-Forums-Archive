---
title: "Blank Screen &amp; Empty xorg.conf - Any ideas?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by Pilgrim_UK on 2009-01-22
PC = Old HP/Compaq Compaq Evo P4 512MB RAM
Monitor = Samsung SyncMaster 223BW

**The Problem:**
[INDENT]Complete Linux newbie, have just installed Ubuntu Desktop 8.10 from the CD.  

Install went well but after the reboot (and any subsequent one) then login I get a blank screen with just a mouse cursor (however the actual graphical login screen itself displays and functions fine).  

I have left it at the blank screen for 20 mins or so to ensure nothing is going on.

Have found the options in the bottom corner of the login screen and tried to login to Gnome Safe mode - still get a blank screen.

I can login to a Terminal Safe mode (terminal window appears in low right hand corner).[/INDENT]

**Additional Info:**
[INDENT]Used 'lspci' to determine graphics card/chipset = Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

Used 'less /etc/X11/xorg.conf' to see the xorg.conf file.  It is pretty much empty of settings apart from what I would call header labels for the 3 sections (Device, Monitor and Screen) and basic identifier rows that contain no system specific information (e.g. Device Identifier "Configured Video Device").[/INDENT]

And that's where I've ground to a halt (not a lot to show for several hours effort I'm afraid).  

Any pointers as to next steps are gratefully received, thanks!

---

### Post by yeats on 2009-01-22
Have you made any changes to xorg.conf that you know of?  Have you installed anything that might have made changes to it?  Anything else you might have changed recently?

---

### Post by Pilgrim_UK on 2009-01-22
No changes to xorg.conf.  It's a fresh/virgin install on the PC so have never logged into Ubuntu successfully as yet.

---

### Post by Zach.Town on 2009-01-22
I could have the same problem?

[http://ubuntuforums.org/showthread.php?t=1047804](http://ubuntuforums.org/showthread.php?t=1047804)

---

### Post by Pilgrim_UK on 2009-01-23
I don't really have enough experience (i.e. none re Linux) to draw conclusions on similarities between our issues.  

One key difference is that after login mine just shows a blank screen (which is not a terminal window).  Also, during config I did not get asked to select a graphics card driver via the taskbar (have not seen a taskbar yet!).

---

### Post by Omegaxis on 2009-01-23
I am having a similar issue.......
[my thread]("http://ubuntuforums.org/showthread.php?t=1036357")
If I can find an answer, I'll post it in this thread.

Do you happen to know if you have an integrated video card (you wouldn't of had to put this in yourself)? 
or a PCI or AGP video card (You probably would have had to install this).
Also, is it going through a DVI or VGA port?

---

### Post by Pilgrim_UK on 2009-01-23
Video card is integrated:
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device

Video output is via VGA.

Thanks

---

### Post by Omegaxis on 2009-01-23
When you get to the login screen freeze:

```
CTRL+ALT+F1 <Login as prompted, note that nothing will appear when you type your password.
Then type the following>
sudo lshw -class DISPLAY
```

Then report back here with what ever that spits out.

It make take a while for me to get back, as I have to get to work.

---

### Post by Pilgrim_UK on 2009-01-23
OK, have sussed it!  Had to remove compiz which apparrently adds graphical desktop effects.

Details here [http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/]("http://benaiah41.wordpress.com/2008/11/01/ubuntu-810-freezes-after-login-screen/")

Cheers

---

