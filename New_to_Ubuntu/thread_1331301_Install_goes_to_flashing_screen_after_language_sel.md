---
title: "Install goes to flashing screen after language select"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Balf on 2009-11-19
I have just started with Ubuntu and have it working on an old PC I had lurking in the cupboard.  On trying to install it on my normal PC the screen goes all stripy green and flashing after I have entered the language.   I thought perhaps it would eventually start so I left it for half an hour. When I came back Windows XP had booted up.   I used the middle option on the install to keep Windows.

The PC has an AMD Athlon(tm) Processor LE-1640 2.68Ghz with 1.87gB RAM. The video adaptor is a NVIDIA GeForce 7050 PV / NVIDIA nForce 630a

Can anyone help?

Peter

---

### Post by wrgb2 on 2009-11-19
Have you tried running from the live CD?  Choose the option to try Ubuntu without making any changes to your system.  If the Live CD boots up, click on the install icon to install Ubuntu from there.

---

### Post by Balf on 2009-11-19
Yes, it does the same

---

### Post by wrgb2 on 2009-11-19
You could try downloading the Alternate Installer CD and try the a text mode install.  It looks like Ubuntu is having trouble with your video card and the GUI installation.

---

### Post by Balf on 2009-11-22
Thanks for the reply.  What is the text mode install?  I downloaded and burnt the alternative version but when I boot from the CD it doesn't give me the "install without making changes to your computer" option.  I don't want to obliterate the Windows system on my PC because I am using Dbase 2k on it.
Peter

---

### Post by wrgb2 on 2009-11-22
I don't remember the exact text, but the regular install (I think it simply saya Install Ubuntu on this PC) will help you install Ubuntu side-by-side with Windows -- it won't obliterate it.  This link might help -- [https://help.ubuntu.com/9.10/installation-guide/i386/index.html](https://help.ubuntu.com/9.10/installation-guide/i386/index.html)

---

### Post by Balf on 2009-11-23
I have put in an empty hard disk and performed the text install.  It got to the end without any problems.  I then removed the CD and rebooted.  After the splash screen the flashing green stripes came back.   Is there a way to boot up like a windows safe mode?  I am beginning to think it's not worth all the bother!
Thanks for your previous replies,
Peter.

---

### Post by wrgb2 on 2009-11-23
You can choose Recovery Mode from the Grub menu and see if it boots.  If not, choose recovery mode again and choose the option to boot to a command prompt.  Login and type startx from the command line and see if Gnome comes up.  If it doesn't, make a note of the errors and post back here.

---

### Post by Balf on 2009-11-24
Thank you for the advice.  I followed your instructions and after I pressed return having entered "startx" at the command prompt, the green lines appeared.   It looks as though there is the log in screen somewhere in the background, behind the flashing lines.
Is it not possible to start without the video driver loaded?
Peter

---

### Post by wrgb2 on 2009-11-24
I'm assuming you're running 9.10, let me know before doing this if you're not.
You can start with the default VESA driver by doing the following:

Boot to a command prompt in recovery mode

Type 

sudo nano /etc/X11/xorg.conf

Now type in the following lines (sorry):

Section "Device"

        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
	Identifier      "Configured Monitor"
EndSection

Section "Screen"
	Identifier      "Default Screen"
	Monitor         "Configured Monitor"
	Device          "Configured Video Device"
EndSection

Save the file with ^O

Now type:

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

This should get you running with Vesa graphics and we can see about adding the driver for your NVIDIA card.

---

### Post by Balf on 2009-11-24
Hello again,

Typed it all exactly as you said and when I went to save it came up with a file name of :
/etcX/org.conf which I changed to /etc/X11/xorg.conf and it asked if I wanted to save to the changed file name and I said yes.

Then I rebooted and the password was asked for in the terminal screen after which it came up with an error screen:

Fatal server Error
No Screens found

Interesting, no?

Peter

---

### Post by wrgb2 on 2009-11-24
Hmmm....that worked the last time I used it.  I'm out of ideas, maybe someone else can help.

---

### Post by Balf on 2009-11-24
Yes I'm running 9.10

I typed in what you said and now I get:
Fatal server error
no screens found

Peter

---

### Post by Balf on 2009-11-24
Sorry, couldn't see my previous reply!

Thank you for all your help.  Perhaps someone else will pick up the situation.

Peter

---

### Post by Balf on 2009-11-25
Hello, It's me again!   With my morning head on I thought I would check the file you asked me to type.  I entered the sudo nano /etc/X11/xorg.conf and the file came up on the screen.  I lied to you! I had left out a ["] and typed:
Device Configured Video Device"
instead of:
Device "Configured Video Device"

I corrected it and now it boots up ok

So thank you very much for your help.  I'll check the drivers in the system, when I get a moment.

Cheers,
Peter

---

### Post by wrgb2 on 2009-11-25
Glad to hear it was just a typo!  You can check to see what proprietary driver(s) are available for your card in System > Administration > Hardware Drivers.

Good luck.

---

### Post by Balf on 2009-11-25
The correct driver has been activated and it's all tickatyboo!  I just need to find how to set my azerty keyboard so that ctrl alt à gives me the ampersand and all will be well.

Thanks again,

Peter

---

