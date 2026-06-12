---
title: "Tablet pc drivers? -confused-"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-17
hello all i have tx2z tablet pc, i have read over the [B]HOWTO setting up ubuntu 8.10 intrepid on the HP tx2z tablet pc thread.

[http://ubuntuforums.org/showthread.php?t=1038898](http://ubuntuforums.org/showthread.php?t=1038898)

however i am not able to find the driver for the touchsceen, the rotate screen button, and the auto rotate when i switch pc to tablet mode. and how to install if it is diffrent then the appication>accessories>terminal route.

 Also any other drivers that i may need to install that i do not know of, please post.

 I also would like my mute button to light up red as it did with ms if possible but not necessary

and is there a wordart  and mindmanger[/B]** "like" program**[B]  that i can add on to ubuntu

thanks so much guys i have fell in love with this program and this community, i don't think i will ever go back to windoze


[/B]

---

### Post by R3fr4cti0n on 2009-08-17
I would really love to find the drivers to finger flicks that is what i use most on this computer thanks

---

### Post by Favux on 2009-08-17
Hi R3fr4cti0n,

I've answered you twice now, once each on two of your other posts.  Why haven't you responded?

I think you're using Ubuntu Jaunty (9.04).  To get the TX2z to work in Jaunty you need to use an xorg.conf.  To edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
But first you need to patch your kernel with patches from Rafi Rubin to get the n-trig digitizer ready to work.  Since that is sort of difficult Ayuthia has done it for you and prepackage the results in deb.s.  You download the right deb for your cpu architecture and double click on it and it installs.

See Appendix 2 near the bottom of the HOW TO here:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  For the xorg.conf and link to Ayuthia's kernel deb.s and kernel patching HOW TO.

---

### Post by R3fr4cti0n on 2009-08-17
thx favux, i dont see any other post. i am using 8.10 intrep i think it is called. but it is 8.10 for sure will this process work with it/

---

### Post by R3fr4cti0n on 2009-08-17
favux if you are answering me i cannot see your posts.. try again and if i dont respond plz email me @ [email]deleteentershift@gmail.com[/email]

---

### Post by Favux on 2009-08-17
Hi R3fr4cti0n,

Use Advanced Search and search your name.

No that only works for Jaunty (9.10).  To get it set up in Intrepid (8.10):

See post #1 here:  [http://ubuntuforums.org/showthread.php?t=1038898](http://ubuntuforums.org/showthread.php?t=1038898)

And post #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)

Also:  [http://goatonabicycle.com/rambles/?p=74](http://goatonabicycle.com/rambles/?p=74)

And the patched linuxwacom:  [http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77](http://www.mayrhofer.eu.org/Default.aspx?pageindex=6&pageid=77)

---

### Post by R3fr4cti0n on 2009-08-17
so i just need to DL jaunty and install those drivers and my whole tx2z will work like it did on windoze?  tyvm i must have read another post wrong i thought to get all the features on the tx2z i could only use 8.10.

thanks again

---

### Post by Favux on 2009-08-17
Hi R3fr4cti0n,

Well that's basically correct.  But the deb.s aren't drivers they are patched kernels.  The kernel is the actual linux that everything is based on.  The patches are applied to the n-trig usb HID section of the linux kernel.  You can look at Ayuthia's patching the kernel HOW TO to better understand things.

And the information you had is out of date.  It was true that the TX2z would only work on 8.10 until Ayuthia applied all Rafi's patches.  Now if anything the TX2z works better in Jaunty.

---

### Post by R3fr4cti0n on 2009-08-18
Favux, 
   is this what u are talking about that i need to Dl and patch?

For those who want the deb files:

**32-bit**
[linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-image-2.6.28-14-generic_2.6.28-14.47_i386.deb")
[linux-headers-2.6.28-14-generic_2.6.28-14.47_i386.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-headers-2.6.28-14-generic_2.6.28-14.47_i386.deb")

i installed them and it said they already existed? sorry i am totaly new at this and relearning a program along with this jargan ise't going as smooth as i thought it would.. thx for all you help tho

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

Probably something to do with modules already present?  I'd need to see the exact error message.  You could ask Ayuthia.

The HP TX2z (which is what you have, right?) has dual AMD 64 cores.  You need the AMD 64 bit deb.s.  Unless you installed 32 bit Ubuntu Jaunty?

By the way there was a kernel update today.  Don't accept it.  You have to wait until Ayuthia updates his deb.s.

---

### Post by R3fr4cti0n on 2009-08-18
soi need to install the 64 bit version of what i posted above? i only did the update to jaunty via update manager is there a way to see what version i am running?
  so in the order of what i need to do do i have this right?

1 update the 64 bit deb files
2 edit xorg.conf
3 copy n past code in appendix 2 of the linc you gave me ?
4 drink a beer and smile at a great OS:

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

No, if you have 32-bit Jaunty installed you should be ok.  To check let's look at the output in a terminal of:
```
uname -a
```

1.  If you're running 32-bit then the i386.deb's should be good.  Install them.

2.  Edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```
and use the new xorg.conf as specified in Appendix 2.  At least add the Wacom stuff and "ServerLayout".  Make sure you keep your video sections if they differ.  Reboot and it should work.

3.  To get it to work better comment out the n-trig section of the 10-wacom.fdi.  I'll show you how if need be.

---

### Post by R3fr4cti0n on 2009-08-18
so do i ADD this
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSectionto the end of my xorg.conf gedit? or do i delete something?

---

### Post by R3fr4cti0n on 2009-08-18
> **R3fr4cti0n said:**
> so do i ADD this

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection

EndSectionto the end of my xorg.conf gedit? or do i delete something?

Dident get that right the first time....

---

### Post by R3fr4cti0n on 2009-08-18
so do i ADD this

code:
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "touch"        "SendCoreEvents"

EndSectionto the end of my xorg.conf gedit? or do i delete something? 

or second

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

Why don't you post your current working xorg.conf and I'll take a look.  Place the xorg.conf in the code brackets by clicking on the '#' above and to the right in Advanced mode.

---

### Post by R3fr4cti0n on 2009-08-18
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

```

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

OK, it should look like this.  Hopefully it will work for you.

By the way, you never posted 'uname -a'.  So you were 32-bit?  You've installed the right deb.s and are good to go?

---

### Post by R3fr4cti0n on 2009-08-18
```
julian@Abriella:~$ uname -a
Linux Abriella 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 i686 GNU/Linux

```

i believe so?

---

### Post by R3fr4cti0n on 2009-08-18
> **R3fr4cti0n said:**
> ```
julian@Abriella:~$ uname -a
Linux Abriella 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:54:56 UTC 2009 i686 GNU/Linux

```i believe so?

ya when i DL'ed the other one it said "Error: Wrong architecture 'amd64'"

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

Right, I guess "i686" means 32-bit because when I do it I get "x86_64".  And you're sure you have the HP TX2z Touchsmart, and not for e.g. the Dell Latitude XT?

---

### Post by R3fr4cti0n on 2009-08-18
ya i am sure code on the bottom says tiuchsmart tx2

---

### Post by R3fr4cti0n on 2009-08-18
damnit error message

/tmp/R3fr4cti0n_TX2z_Jaunty_test 1_xorg.conf.txt could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.

and was i supost to replace my current xorg with the script u posted?

---

### Post by R3fr4cti0n on 2009-08-18
got the stylist but no touch yet. gona recheck the notes

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

Right replace the entire contents of xorg.conf with the xorg.conf I posted using:
```
gksudo gedit /etc/X11/xorg.conf
```
Sounds like that's what you did and you are making progress!

---

### Post by R3fr4cti0n on 2009-08-18
was there another download needed for touch?

---

### Post by R3fr4cti0n on 2009-08-18
input this:

2.  Edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```and use the new xorg.conf as specified in Appendix 2.  At least add the Wacom stuff and "ServerLayout".  Make sure you keep your video sections if they differ.  Reboot and it should work.

and i got this

```
julian@Abriella:~$  xorg.conf (X.Org X Window System server configuration file)
bash: syntax error near unexpected token `X.Org'
julian@Abriella:~$ #
julian@Abriella:~$ # This file was generated by dexconf, the Debian X Configuration tool, using
julian@Abriella:~$ # values from the debconf database.
julian@Abriella:~$ #
julian@Abriella:~$ # Edit this file with caution, and see the xorg.conf manual page.
julian@Abriella:~$ # (Type "man xorg.conf" at the shell prompt.)
julian@Abriella:~$ #
julian@Abriella:~$ # This file is automatically updated on xserver-xorg package upgrades *only*
julian@Abriella:~$ # if it has not been modified since the last upgrade of the xserver-xorg
julian@Abriella:~$ # package.
julian@Abriella:~$ #
julian@Abriella:~$ # Note that some configuration settings that could be done previously
julian@Abriella:~$ # in this file, now are automatically configured by the server and settings
julian@Abriella:~$ # here are ignored.
julian@Abriella:~$ #
julian@Abriella:~$ # If you have edited this file but would like it to be automatically updated
julian@Abriella:~$ # again, run the following command:
julian@Abriella:~$ #   sudo dpkg-reconfigure -phigh xserver-xorg
julian@Abriella:~$ 
julian@Abriella:~$ Section "InputDevice"
bash: Section: command not found
julian@Abriella:~$ Identifier"stylus"
bash: Identifierstylus: command not found
julian@Abriella:~$ Driver"wacom"
bash: Driverwacom: command not found
julian@Abriella:~$ #   The by-path below is for the HP TX2z
julian@Abriella:~$ Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
bash: Option: command not found
julian@Abriella:~$ Option"Type""stylus"
bash: OptionTypestylus: command not found
julian@Abriella:~$ Option"USB""on"
bash: OptionUSBon: command not found
julian@Abriella:~$ Option"Button2""3"# make stylus button R mouse click
bash: OptionButton23#: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ Section "InputDevice"
bash: Section: command not found
julian@Abriella:~$ Identifier"touch"
bash: Identifiertouch: command not found
julian@Abriella:~$ Driver"wacom"
bash: Driverwacom: command not found
julian@Abriella:~$ #   The by-path below is for the HP TX2z
julian@Abriella:~$ Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
bash: Option: command not found
julian@Abriella:~$ Option"Type""touch"
bash: OptionTypetouch: command not found
julian@Abriella:~$ Option"USB""on"
bash: OptionUSBon: command not found
julian@Abriella:~$ Option"Touch""on"
bash: OptionTouchon: command not found
julian@Abriella:~$ Option"TopX""0"
bash: OptionTopX0: command not found
julian@Abriella:~$ Option"TopY""0"
bash: OptionTopY0: command not found
julian@Abriella:~$ Option"BottomX""9600"
bash: OptionBottomX9600: command not found
julian@Abriella:~$ Option"BottomY""7200"
bash: OptionBottomY7200: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ Section "Device"
bash: Section: command not found
julian@Abriella:~$     Identifier    "Configured Video Device"
bash: Identifier: command not found
julian@Abriella:~$     Driver    "fglrx"
bash: Driver: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ Section "Monitor"
bash: Section: command not found
julian@Abriella:~$     Identifier    "Configured Monitor"
bash: Identifier: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ Section "Screen"
bash: Section: command not found
julian@Abriella:~$     Identifier    "Default Screen"
bash: Identifier: command not found
julian@Abriella:~$     Monitor        "Configured Monitor"
bash: Monitor: command not found
julian@Abriella:~$     Device        "Configured Video Device"
bash: Device: command not found
julian@Abriella:~$     DefaultDepth    24
bash: DefaultDepth: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ Section "Module"
bash: Section: command not found
julian@Abriella:~$     Load    "glx"
bash: Load: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ Section "ServerLayout"
bash: Section: command not found
julian@Abriella:~$ Identifier"Default Layout"
bash: IdentifierDefault Layout: command not found
julian@Abriella:~$ Screen"Default Screen"
bash: ScreenDefault Screen: command not found
julian@Abriella:~$ #Identifier"X.org Configured"
julian@Abriella:~$ InputDevice"stylus""SendCoreEvents"
bash: InputDevicestylusSendCoreEvents: command not found
julian@Abriella:~$ InputDevice"touch""SendCoreEvents"
bash: InputDevicetouchSendCoreEvents: command not found
julian@Abriella:~$ EndSection
bash: EndSection: command not found
julian@Abriella:~$ 
julian@Abriella:~$ #   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
julian@Abriella:~$ 

```

i checked and rechecked copy n pasted where did i mess up?

---

### Post by R3fr4cti0n on 2009-08-18
thought maby i should reboot and the system crashed can seem to reinstall ubuntu from my disk as well any ideas on what happen?

---

### Post by R3fr4cti0n on 2009-08-18
crap i just ran the memcheck and searched  for a reinstall cant find anything, on it is there a code or command that i can use to run the disk?

---

### Post by Favux on 2009-08-18
Hi R3fr4cti0n,

Nope, no idea.  Never seen that before.

You were suppose to use the xorg.conf in post #18.  Using the command I gave you your xorg.conf should have opened up.  You then should have totally deleted the contents and completely replaced them with the new one or made the xorg.conf look just like the new one.  Save and close gedit.  Reboot.

Does that sound like what you did?

---

### Post by R3fr4cti0n on 2009-08-19
ya thats exactly what i did, also went over each line to make sure they were the same as what u posted. i wasn't sure if the copy n past may be glichy i had that problem before with windoze. i got ubuntu reinstalled and gotta update it to 9.04 afterthat ill start all over again

---

### Post by R3fr4cti0n on 2009-08-19
so let me see if i have this all right so i dont screw up again

1 patch my kernel with patches from Rafi Rubin to get the n-trig digitizer ready to work.which is here ----->  2.6.28-14.47 kernel deb.s on post #209 here:  [http://ubuntuforums.org/showthread.p...038898&page=21]("http://ubuntuforums.org/showthread.php?t=1038898&page=21") 

2 then i need to edit my xorg.conf, I do this by pasting 
```
gksudo gedit /etc/X11/xorg.conf
```
in my terminal

3 after my xorg opens i paste this
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

Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
#   The by-path below is for the HP TX2z
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "Type"        "stylus"
    Option        "USB"        "on"
    Option        "Button2"    "3"    # make stylus button R mouse click
EndSection

Section "InputDevice"
    Identifier    "touch"
    Driver        "wacom"
#   The by-path below is for the HP TX2z
    Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
    Option        "Type"        "touch"
    Option        "USB"        "on"
    Option        "Touch"        "on"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "9600"
    Option        "BottomY"    "7200"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
#    Identifier    "X.org Configured"
    InputDevice    "stylus"    "SendCoreEvents"
    InputDevice    "touch"        "SendCoreEvents"
EndSection

#   Developed with Ayuthia (using Rafi Rubin's Wacom sections as a starting point).
```

over my current setting which are this.
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
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

after that my stylis, screen buttons and touch screen should work right? is this all i needed to do?

---

### Post by Favux on 2009-08-19
Hi R3fr4cti0n,

That's the general idea but notice your video sections have changed.  That indicates you know longer have the proprietary ATI driver installed.

So you have to use your current video sections.  Study the difference between what you first posted and what you have now.

I would first install Ayuthia's kernel deb.s and reboot and see if things are stable.  By the way did you reinstall 32-bit?

Next decide if you want the ATI proprietary drivers.  They are in System>Administration>Hardware Drivers.  If you do install ATI reboot again and make sure things are stable.

Then we can go on to xorg.conf.

---

### Post by R3fr4cti0n on 2009-08-19
i just installed the 8.10 intrep that you send in a link from in another post since that is my only one i had bunt to cd, then i updated it to 9.04 the newest version. going to install the deb.s then reboot now

---

### Post by R3fr4cti0n on 2009-08-19
ya this is my current xorg conf. can i still use that attachment you sent me to conf it?

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

---

### Post by Favux on 2009-08-19
Hi R3fr4cti0n,

No.  The video sections are not the same.  Compare them.  You would have to change those in the xorg.conf I posted to the ones you have now.

Do you want to/have you installed the ATI drivers?  If you do reboot and make sure they are working.  Then repost your xorg.conf.

---

### Post by R3fr4cti0n on 2009-08-19
so i just need to delete the 
 DefaultDepth    24 from the code you attached right?

---

### Post by R3fr4cti0n on 2009-08-19
> **Favux said:**
> Hi R3fr4cti0n,

No.  The video sections are not the same.  Compare them.  You would have to change those in the xorg.conf I posted to the ones you have now.

Do you want to/have you installed the ATI drivers?  If you do reboot and make sure they are working.  Then repost your xorg.conf.
  i never installed any ati drivers before not on pourpose anyways and i dont know how to now.. does it matter?

---

### Post by Favux on 2009-08-19
Hi R3fr4cti0n,

Please notice that you haven't given me much detail.

Did you install the ATI drivers?  Did you decide not to do that?

Are you asking me how to update the TX2z xorg.conf for what you have now?  But which xorg.conf is your current one?

Please specify.  I want to be sure we are communicating.

---

### Post by R3fr4cti0n on 2009-08-19
sorry, i am trying to research, code and translate what i think i understand into this thread.
i never installed any ati drivers on ubuntu, not on purpose. i dont know how to, does it matter to the integraty of my computer or can i go with out it or maby do it later when i understand this os better.
As for my xorg conf this is my current one
```
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```so in order for me to correct the ati problem with the attechment you sent me i need to delete the "DefaultDepth    24" from the screen section, as it is no longer in my xorg conf.. also thankyou somuch for the 3 days worth of help

---

### Post by Favux on 2009-08-19
Hi R3fr4cti0n,

You're welcome.  Good, now we've on the same page.  Find attached the new xorg.conf.  Notice I had to remove:
```
    Driver    "fglrx"

    DefaultDepth    24

Section "Module"
    Load    "glx"
EndSection
```
The "fglrx" is the proprietary ATI driver.  And the "glx" stuff is associated with it.  So you are currently using the OSS Xorg radeon drivers.  There are pluses and minuses to either.  You are right, it's a good idea to learn more before you decide to change.

Ok, and you understand how to edit xorg.conf and to save the new contents and reboot, correct?

To back up xorg.conf enter in a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Notice we added .bak to rename it so the system doesn't see it.  Now to restore it from the command line you just reverse things like so:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
sudo makes you root, like gksudo does for graphic programs, and cp is the copy command.

Good luck!

---

### Post by R3fr4cti0n on 2009-08-19
i installed the conf txt and got the same reaction that i did last time i installed the conf txt however this time i had an option to run in "low graphix mode" i dont know what this is but my computer is running slower than the windoze, and touch still does not work when ever i touch the screen the cursor gos straight to the left top cornor and will not move unless i use mousepad. any ideas?

---

### Post by Favux on 2009-08-19
Hi R3fr4cti0n,

Well that's and improvement over X crashing anyway.

Low graphics mode means something is wrong in the xorg.conf.  Probably with video.  Let's see if we can figure it out.

The cursor going to a corner usually means Xserver/Xinput isn't getting a signal from the device.  That doesn't make sense.

On the back plate of your laptop can you give me the exact name(s), TX2 whatever.  Probably two versions.

Try changing your "ServerLayout" to:
```
Section "ServerLayout"
#	Identifier	"Default Layout"
#	Screen		"Default Screen"
	Identifier	"X.org Configured"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"touch"		"SendCoreEvents"
EndSection
```
Notice we've commented out "#" two lines and removed the comment from one.

Check in System>Administration>Synaptic Package Manager that both linuxwacom packages are installed.  Search "wacom".  The 0.8.2-2 xserver-xorg-input-wacom should be installed by default.  If not install it.  Also install wacom-tools.  Now reboot.

---

### Post by R3fr4cti0n on 2009-08-19
did all that, got same thing as last time, low graphix mode and touch still dose not work, looked for those packages one was not installed going to put the xorg back to the first attach and try that. if that doesnt work do we have any other options?

---

### Post by Favux on 2009-08-19
Hi R3fr4cti0n,

First key question:  Do you or have you had Win 7 installed on the TX2z?  (you didn't give me the names on the label as requested).  Or only Vista?

Let's not assume the xorg.conf is OK.  Post your current version.

Let's try commenting out the n-trig subsection of the '10-wacom.fdi'.  It may not do anything, but we have to do that anyway.  It is at '/usr/share/hal/fdi/policy/20thirdparty/'.  The n-trig part looks like this:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
```
Notice the section label, N-Trig Duosense etc., is bracketed by <!--  -->.  Those are the .fdi versions of comments.  Move the trailing one to after the match line where I show below:
```
    <!-- N-Trig Duosense Electromagnetic Digitizer
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match> -->
  </device>
```
Do not get the </device>, that isn't part of the section.  I just left it in to show you the trailing comment goes after the </match> and before the device.  Then reboot.

To edit it use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```

---

### Post by R3fr4cti0n on 2009-08-19
ya idk what is going on is there any way to post all my info so u might get a look and tell me what you think or maby i should DL ubuntu 9.04 in 64 bit and format then reinstall and we can start from scratch?

---

### Post by R3fr4cti0n on 2009-08-19
didnt refresh and i didnt see that last post one sec ...

---

### Post by R3fr4cti0n on 2009-08-19
ok did the " - - > " thing and rebooted with no problems, i acualy had the vista home installed however i tried to install a dual boot of vista and ubuntu and some how compleatly deleted vista. got first day of college tomorrow soo i will check on here in the morn and after school round 3 thanks again!

---

### Post by Favux on 2009-08-20
Hi R3fr4cti0n,

Good job.

So you have the Vista n-trig firmware.  That's what should be in your xorg.conf, so that's not the problem.

Please post your xorg.conf first thing tomorrow.

Have fun your first day!

---

### Post by R3fr4cti0n on 2009-08-20
this is my current conf, this is the only one it runs stable on so far and it the original. if i touch the screen now it dose not go straight to the corner as last time but gives no response 

curennt xorg.conf:```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by Favux on 2009-08-20
Hi R3fr4cti0n,

Well, you are not going to get anything from the stylus or touch without the wacom entries, so that's not surprising.  We could keep assuming it's a video problem by trying things like changing:
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```
to
```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection
```
But that doesn't make much sense.  You should be able to substitute in the video section in your post above into the the xorg.conf like I did in test 2 and it should work.

So what that leaves is a problem with the wacom sections.  Which seems to mean that you somehow have the Win 7 firmware.  So let's see if that is the case.  Try test 3 attached below.

---

### Post by R3fr4cti0n on 2009-08-20
well i used the test 3 xorg and the whole system crashed, idk what happen but i am not able even get the hp screen to the bios so i can reinstall unbuntu, hp is sending me some cd to reinstall vista however i am going to do a dual boot like i wanted to first off with ubuntu. i guess what my question is, would it be any easyer to do this with a direct burned copy of ubuntu 9.04 in 64 bit. i thought that maby the problem all along was that i made a bad copy of ubuntu 8.10 and then updated to 9.04. instead maby i should have burned a cd of ubuntu 9.04 in 64 and do the kernals and deb.s from there. what are the steps that i need to take for a 64bit  9.04 ubuntu to get the touch, buttons, stylis and magic flip working. feel free to take your time anwsering i am out a pc till tuesday. thankyou for all your help time and pataince with a compleat NOOB. lol :)

---

### Post by Favux on 2009-08-20
Hi R3fr4cti0n,

Not a problem.  You are not a complete noob anymore.  You've actually learned a fair amount already.  And this is how you learn, just jump on in.

I think your thought that there was a problem with your 8.10 install disk is a good one.  I can't think of why you've been having problems anyway.

Dual booting with Vista sounds like a good idea, it's what I do.  And going to AMD_64 also sounds good.  Remember to burn the disk slowly, not as fast as the burner will allow.  Burning too fast can give a "corrupt" disk that seems to check out OK.  And do the checksums.

I'm hoping to hear good news from you Tuesday.  We can worry about getting stuff set up then.  You already know how to get the stylus and touch working after all.  Since you'll be dual booting with Vista just don't use test 3, which has the Win 7 firmware usb by-paths.
Good luck!

---

### Post by R3fr4cti0n on 2009-08-21
thanks favux, i got a old xp disk installed for now so my wife can do her online classes untill we get her netbook back, not been a good 2 weeks for our computers (netbook's not my fault tho) will i be able to dual boot ubuntu 64 with a vista 32bit or is this going to be a problem? also when i upgrade the memory for the 64bit ubuntu to 4+gigs it should'nt make a diffrence with the vista 32bit right when i am using vist the extra 1+ gigs of mem will just not be used correct? it wont effect the integraty of both of the os right?

---

### Post by Favux on 2009-08-21
Hi R3fr4cti0n,

Should work fine.  I have 4 GB's and AMD_64 Intrepid.  The Vista is 32-bit.  I have no problems dual booting.

---

### Post by R3fr4cti0n on 2009-08-22
i reinstalled ubuntu this time in 64bit and the newest 9.04 version.
installed all the drivers, and such everything was smooth upon start, played with it a bit the styist works but when i touch the screen the pointer gos straight to the top left corner as it did before. 

i then patched the kernals ```

**64-bit**
[linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb")
[linux-headers-2.6.28-14-generic_2.6.28-14.47_amd64.deb]("http://linuxfans.keryxproject.org/packages/experimental/linux-headers-2.6.28-14-generic_2.6.28-14.47_amd64.deb")

```From  [http://ubuntuforums.org/showthread.php?t=1038898&page=21](http://ubuntuforums.org/showthread.php?t=1038898&page=21)   post #209

rebooted, no problems other than i got a popup saying i need to update some drivers whose name closley resembled the patches i just installed before the reboot

i them went to my xorg.conf and copied and pasted the "xorg.conf tx" 
from  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  post #1 appendix 2 near the bottem of page the txt i used is [IMG]http://ubuntuforums.org/images/attach/txt.gif[/IMG]     [Favux_TX2z & XT_Jaunty_xorg.conf.txt]("http://ubuntuforums.org/attachment.php?attachmentid=120392&d=1247088237") (2.6 KB, 77 views)

rebooted and got past the load screen but only got mutiple blue green and purple "ubuntu" logos at the top of screen with a black backround. and the Os would go no further this is what happed last time, i believe i will need to reinstall ubuntu to even get back to the point where i can edit. any ideas what i may have done wrong?

my xorg.conf before the copy and past of the new one ```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection
```

i don't get what the hell i am doing wrong here?!

---

### Post by Favux on 2009-08-22
Hi R3fr4cti0n,

Looks like two things.  Remember Ayuthia's deb.s are patches to the kernel.  So you are loading patched kernels.  There was a kernel update released in the last few days.  It sounds like you did the update which would have replaced Ayuthia's patched kernel with the new kernel.  And it of course would not have the n-trig patches to the HID section of the kernel.  So n-trig won't work on it.  If you want to keep the new kernel you have to either patch it yourself or wait until Ayuthia updates his deb.s with the new kernel.  Or you should be able to pick the previous kernel when you boot.  That should still have the patched kernel.  You have to remember if you are using a patched kernel to refuse any kernel related updates as they will break your n-trig functionality.  At least until you are ready for them.

I'm not sure what's going on with the xorg.conf.  Could be video, could be a firmware problem, could be the wacom entries in "ServerLayout".  Theory5 and I just went through these issues here:  [http://ubuntuforums.org/showthread.php?t=1239727](http://ubuntuforums.org/showthread.php?t=1239727)  I think once you get set up again you should follow along with the stepwise introduction of the wacom entries to the xorg.conf.  Let's see if that will localize the issue you are having.

Good luck!

---

### Post by R3fr4cti0n on 2009-08-23
i was carefull not to install the updates unless they do them auto, but i do remember declining the new ones several times, i will be going over the stepwise later this afternoon see if i can localize the problem as you said. thx

---

### Post by R3fr4cti0n on 2009-08-23
just those to patch updates i mean, the ones that said needed updated after i installed ayuthia's deb.s

---

### Post by R3fr4cti0n on 2009-08-25
favux,

ok after reveiwing theory5's post and re-reveiwing it i got it.. sorta

i commented out the n-trig

installed BOTH wacoms from synapic (they didnt both install auto after reinstall of ubuntu)

installed debs for 64 bit, rebooted and ok..

changed xorg.conf useing the conf you sent me on post 1```
Attached Files [IMG]http://ubuntuforums.org/images/attach/txt.gif[/IMG]     [R3fr4cti0n_TX2z_Jaunty_test 1_xorg.conf.txt]("http://ubuntuforums.org/attachment.php?attachmentid=125411&d=1250637840") (2.1 KB, 3 views)
```rebooted and it didn't crash!

hoewver, my touch still jumps to the left top cornor of the screen when i touchit, but pen works beautifuly, unless my hand touches screen then its force the application i am uses to scroll up and down any idea how to get this to work? or just disable it alltogether?

---

### Post by Favux on 2009-08-25
Hi R3fr4cti0n,

Good job!  You've got the stylus working!

The xorg.conf you posted looks right.  And Ayuthia's deb.s installed without a problem?  No error messages?  And the kernel you were on matched the ones the deb.s were labelled with?

I'm not sure what's wrong.  I guess I'd check very carefully the 10-wacom.fdi and make very sure you've commented out the n-trig section correctly.  That's about the only thing that could do what you are describing.

---

### Post by R3fr4cti0n on 2009-08-26
yep got the stylus working and everything installed without a problem and without any error messages, kernel and deb.s match. going to recheck when i get home from work today on the commented n-trig, the first time i commented it out my n-trig the cursor was off when i used the stylus, and still had the same problem with the touch (cursor gos to top left corner) before and after commenting, so i think the problem lies with the n-trig as well. I believe i have seen another thread with the same problem with the cursor, going to look for that later when i get home.

---

### Post by Favux on 2009-08-26
Hi R3fr4cti0n,

If that is the problem, my guess would be that you copied and pasted rather that cut and pasted the trailing:
```
-->
```
part of the comment.  So the n-trig section of the .fdi still isn't really commented out.  Just a thought.

---

### Post by R3fr4cti0n on 2009-08-26
No, i believe thats all right, i went over it again line by line and i don't see anything wrong
```
<!-- N-Trig Duosense Electromagnetic Digitizer
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match> -->
```

there is sapost to be a [space} after the last "</match> and before the --> right? idk what else it could be. dam thought i almost had it

---

### Post by Favux on 2009-08-26
I'm puzzled too.  Maybe take a break and come back and review things later?  Sometimes then you can see the problem.

---

