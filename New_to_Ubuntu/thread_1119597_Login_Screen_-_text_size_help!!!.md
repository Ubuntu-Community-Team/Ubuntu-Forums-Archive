---
title: "Login Screen - text size help!!!"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by dBuster on 2009-04-08
Okay, I have searched and tried the ctrl alt +/- and no luck on fixing it.  the xorg.conf file is empty on this build.  It is 8.10 a version I am not that familiar with since I have 8.04 and 9.04 in use on my machines.  

This is the pc I am setting up for my sister and outside of the font issue on the login screen I am pretty much done.  

I will try to get screen shots for you, but the text basically on the login screen is huge!  Especially using the login screen where they choose their name.  Then the tips come on and take over the screen!  

Any ideas as to a fix or a way to reduce them??  Searching keeps leading me down the same path with what I mentioned earlier and that does not seem to work.

---

### Post by s.fox on 2009-04-08
Hi,

[This]("http://ubuntuforums.org/showthread.php?t=363958") thread describes someone who had the same sort of problem as you.  They were able to change the font size.  Hopefully this will also work for you.

REMEMBER:  Make a backup before you change any of the XML. :)

-Ash R

---

### Post by unutbu on 2009-04-08
Ash R's way will change the theme's font size.
Here is an example of how to alter the overall resolution of the login screen:
[http://ohioloco.ubuntuforums.org/showthread.php?p=6848688#post6848688](http://ohioloco.ubuntuforums.org/showthread.php?p=6848688#post6848688)

Since this involves editing /etc/X11/xorg.conf, make a backup first:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20090408
```

You'll want to add/edit a section like this:
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		**Virtual	1024 768**
	EndSubSection
EndSection

```
and change the "Virtual 1024 768" to your desired resolution.

---

### Post by dBuster on 2009-04-08
> Re: Login Screen - text size help!!!
Hi,

This thread describes someone who had the same sort of problem as you. They were able to change the font size. Hopefully this will also work for you.

REMEMBER: Make a backup before you change any of the XML.

-Ash R 

I did read that thread...  Didn't find it too useful except where to locate the xml file.  I am planning on looking at the xml file however trying to locate the GTK file that is mentioned is not as easy as it sounds.  Not knowing which file to touch I am best to leave alone.  So that first recommendation, I will try the xml file however I do not believe it will fully solve my issue as per the thread mentioned.

> Re: Login Screen - text size help!!!
Ash R's way will change the theme's font size.
Here is an example of how to alter the overall resolution of the login screen:
[http://ohioloco.ubuntuforums.org/sho...88#post6848688](http://ohioloco.ubuntuforums.org/sho...88#post6848688)

Since this involves editing /etc/X11/xorg.conf, make a backup first:
Code:

When I try to open the xorg.conf file it is empty!  I have not yet tried it from terminal though and will gedit it tonight.  Hopefully it will not be empty when I do so.   

I will have to check out that web site when I get a few minutes later on this morning.  Hope I can find something useful there.

---

### Post by unutbu on 2009-04-08
I'm confident /etc/X11/xorg.conf exists on your machine because without this file, I don't think the computer will present you with a graphical display.

After making a backup of xorg.conf```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20090408
```

try editing it with the command
```

gksu gedit /etc/X11/xorg.conf
```
(gksu is needed to obtain the root privileges necessary for editing this file.)

---

### Post by dBuster on 2009-04-08
You know...  I try what everyone is saying with the commands everyone is telling me and I am telling everyone that the file is EMPTY!  There is nothing in the xorg.conf file!!!!

What the heck!?

FILE size is ZERO!  

Next suggestion???

---

### Post by unutbu on 2009-04-08
[s]Edit: Hm... I think Jaunty has no xorg.conf...[/s]
Edit2: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta) implies Jaunty does have an /etc/X11/xorg.conf

Please post the output of
```

ls -l /etc/X11
```

Are you using Jaunty, or Intrepid? Your profile says you are using Jaunty, but your original post seems to say the problem is happening on an Intrepid machine?

What kind of video card is in this machine?

---

### Post by dBuster on 2009-04-09
> **unutbu said:**
> [s]Edit: Hm... I think Jaunty has no xorg.conf...[/s]
Edit2: [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta) implies Jaunty does have an /etc/X11/xorg.conf

Please post the output of
```

ls -l /etc/X11
```

Are you using Jaunty, or Intrepid? Your profile says you are using Jaunty, but your original post seems to say the problem is happening on an Intrepid machine?

What kind of video card is in this machine?

```
fred@ubuntu:~$ ls -l /etc/X11
total 44
drwxr-xr-x 2 root root 4096 2009-04-05 11:50 app-defaults
drwxr-xr-x 2 root root 4096 2009-04-05 10:01 cursors
-rw-r--r-- 1 root root   14 2009-04-05 09:58 default-display-manager
drwxr-xr-x 6 root root 4096 2009-04-05 09:50 fonts
lrwxrwxrwx 1 root root   13 2009-04-05 09:37 X -> /usr/bin/Xorg
drwxr-xr-x 3 root root 4096 2009-04-05 09:52 xinit
drwxr-xr-x 2 root root 4096 2009-04-05 11:40 xkb
-rw-r--r-- 1 root root    0 2009-04-05 09:36 xorg.conf
-rw-r--r-- 1 root root    0 2009-04-08 18:49 xorg.conf-20090408
drwxr-xr-x 2 root root 4096 2009-04-05 09:36 Xresources
-rwxr-xr-x 1 root root 3730 2008-10-23 08:40 Xsession
drwxr-xr-x 2 root root 4096 2009-04-05 11:49 Xsession.d
-rw-r--r-- 1 root root  265 2008-10-23 08:40 Xsession.options
-rw------- 1 root root  614 2009-04-05 09:36 Xwrapper.config
fred@ubuntu:~$ 

```

This is on an Intrepid machine I am setting up for my sister.  It is an older machine that they have been having issues with windows so to eliminate their having windows crash because they have 280 plus viruses I am loading up Intrepid for them to use.  I spent 4 days removing viruses from the machine and that was no fun!  I have to return the pc to them tomorrow morning so unless I can resolve this text/font size issue on the login screen I may have to scrap Ubuntu on this pc.

It is a Dell Dimension 3000 with  "Integrated Intel Extreme Graphics 2" graphics on the mainboard.  I have allocated the maximum memory via the bios for this card to use, I believe it is 256mb...  There is 1280mb of ram in the machine.

The Jaunty in my profile is for my laptop.  I actually have Hardy on one laptop and Jaunty on this one.  My two machines are 64 bit and theirs is only 32...

---

### Post by byStanderone on 2009-04-09
...just a point of reminder, X in the X11 is capital letter X.

---

### Post by dBuster on 2009-04-09
I got the box to create a xorg.conf file by running dpkg-reconfigure xserver-xorg.

So now I have a basic xorg.conf...  there is pretty much nothing really in it.  Is there a good source to grab a good configuration for it?  It has an intel graphics chip so something along those lines I am sure would help...

---

### Post by Jakey_TheSnake on 2009-04-09
TO change login screen resolution you can either do it manually by editing your /boot/grub/menu.lst

to meet your colour/resolution requirements as stated by this guide:
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-03/msg00062.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-03/msg00062.html)

Or by installing start-up manager and changing it using a GUI, this has worked for some people in the past when all else has failed. 

Please see this thread as a reference: 
[http://ubuntuforums.org/showthread.php?t=703331](http://ubuntuforums.org/showthread.php?t=703331)

---

### Post by dBuster on 2009-04-09
Thank you for the info, however after reading that thread you referenced, it appears that it was never resolved...  So it wasn't any help and I do not see how changing the grub screen resolution would affect the login screen since xorg has taken over the screen at that point....

I was able though to make some progress...  I located the .xml file for that theme and edited a font size, not sure since I am at work which one it was, but I took it from being a 12 to 10 or 11 and it seems to be smaller in the input areas of the login screen.  The menus are still HUGE though.  Might have to ditch the multiple users and make my sister and her husband use the same one login...  bypassing the login screen altogether....

So frustrating that this is not resolved somewhere along the lines with as many launchpad postings and other issues I have come across in the past week regarding this.

---

### Post by unutbu on 2009-04-09
dBuster, have you tried using the Virtual line in your xorg.conf as described in post #3?

Please post your /etc/X11/xorg.conf.

(If I understand correctly, you were able to create a basic xorg.conf, yes?)

---

### Post by dBuster on 2009-04-09
> **unutbu said:**
> dBuster, have you tried using the Virtual line in your xorg.conf as described in post #3?

Please post your /etc/X11/xorg.conf.

(If I understand correctly, you were able to create a basic xorg.conf, yes?)

Yes I was able to create a basic xorg.conf...

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

That is it...

I can try that line... as mentioned...

---

### Post by unutbu on 2009-04-09
You'll need a bit more than just the "Virtual" line.
Try changing your "Screen" section from

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
to
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	1024 768
	EndSubSection
EndSection
```

changing "1024 768" to a width and height appropriate for your monitor and video card.

---

### Post by dBuster on 2009-04-09
> **unutbu said:**
> You'll need a bit more than just the "Virtual" line.
Try changing your "Screen" section from

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
to
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	1024 768
	EndSubSection
EndSection
```

changing "1024 768" to a width and height appropriate for your monitor and video card.

Okay if it means anything the resolution is 1152 x 864...

Oh and your solution didn't solve the problem...  hmmm back to square one?!  Might be time to give up on multiple users and for them to use just the one user...  Hate to take a step backwards but that appears like the solution at the moment...

---

### Post by dBuster on 2009-04-09
hmmm just a thought...  should since this is an intel based graphics chip be using vesa instead of the intel???

---

### Post by dBuster on 2009-04-09
Just edited the /etc/gdm/gdm.conf to make the following changes.  Might work?!  I am crossing my fingers and will update in the morning whether or not it did.  Seems that entry was similar but yet different in the original file.
```

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 -dpi 96
```

---

### Post by dBuster on 2009-04-10
That last post I made about the gdm file, guess what, IT WORKED!!!

So I wish there was a way to make this solved and I will have to add some tags to it for others to search for it.

This is the website that I used to get the information from, near the bottom...

[Troubleshooting HUGE Fonts - Ubuntu Wiki]("https://wiki.ubuntu.com/X/Troubleshooting/HugeFonts")

---

