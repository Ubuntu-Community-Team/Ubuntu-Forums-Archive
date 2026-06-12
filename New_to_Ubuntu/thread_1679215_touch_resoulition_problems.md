---
title: "touch resoulition problems?"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Toxicstupidity on 2011-01-31
Hey guys,
Im new to linux over all so i figured this would be a good place to post incase i have to do anything in the terminal, if not i apologize.

Okay, so i recieved a Toshiba Portage 3500 from somone who was throwing it away. I needed to do a fresh install of the operating system so i decided to put ubuntu on it because i have used it before and like what it has to offer. The Portege 3500 is a tablet laptop (not touch, only pen) so i figured id have to install some drivers for the touchscreen (something along the lines of [http://ubuntuforums.org/showthread.php?t=1029397](http://ubuntuforums.org/showthread.php?t=1029397)) But to my suprise the touch screen worked "out of the box." 

But the resolution is wrong, its too small (centered). When i go to the display settings the largest setting is 800 X 600 and the display is "Unknown" I wouldnt mind this as much if it didnt change the accucery of the stylis. Center, the curser is right on but as i move out, because the res is too small the curser moves away. So please help me out if you can... i need this tablet for school.

---

### Post by Favux on 2011-01-31
Hi Toxicstupidity,

Welcome to Ubuntu forums!

It looks like we need to add a xorg.conf for you with the Trident video card configured along the lines of:  [http://ubuntuforums.org/showpost.php?p=10141649&postcount=22](http://ubuntuforums.org/showpost.php?p=10141649&postcount=22)

First check in Synaptic Package Manager that you have the Trident driver installed.  Search trident.  It'll be called something like xserver-xorg-video-trident.  If not install it and reboot.

Then lets check on your exact card, entering in a terminal:
```
lspci | grep VGA
```

---

### Post by Toxicstupidity on 2011-01-31
> **Favux said:**
> Hi Toxicstupidity,

Welcome to Ubuntu forums!

It looks like we need to add a xorg.conf for you with the Trident video card configured along the lines of:  [http://ubuntuforums.org/showpost.php?p=10141649&postcount=22](http://ubuntuforums.org/showpost.php?p=10141649&postcount=22)

First check in Synaptic Package Manager that you have the Trident driver installed.  Search trident.  It'll be called something like xserver-xorg-video-trident.  If not install it and reboot.

Then lets check on your exact card, entering in a terminal:
```
lspci | grep VGA
```

First thanks for helping!

Seccond i do have the xserver-xorg-video-trident driver installed and when i typed that into the terminal it came up with

"VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)"

---

### Post by Favux on 2011-01-31
Ok there's several xorg.conf's now floating around for the Trident.  Let's try the one I linked to.  I have some questions about it, but he says it works.  You could probably whittle away at it, there may be some cruft.

I'm assuming you're in Maverick.  So use:
```
gksudo gedit /etc/X11/xorg.conf
```
You are creating a xorg.conf, which isn't necessarily present anymore.  Then copy and paste the following in it:
```
Section "Device"
    Identifier "Configured Video Device"
    Boardname "Trident CyberBlade (generic)"
    Busid "PCI:1:0:0"
    Driver "trident"
    Screen 0
    Vendorname "Trident"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
    Vendorname "Generic LCD Display"
    Modelname "LCD Panel 1024x768"
    Horizsync 31.5-48.0
    Vertrefresh 56.0 - 65.0
    Modeline "1024x768@60" 63.5 1024 1072 1176 1328 768 771 775 798 -Hsync +Vsync
    Option "PreferredMode" "1024x768@60"
    Gamma 1.0
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    Defaultdepth 24
    SubSection "Display"
        Depth 24
        Virtual 1024 768
        Modes "1024x768@60"
    EndSubSection
EndSection
```
Save, Close, and reboot with your fingers crossed.

Since you don't have a xorg.conf you can just remove it from the command line if it breaks X:
```
sudo rm /etc/X11/xorg.conf
```
And reboot and be back to where you started.

---

### Post by Toxicstupidity on 2011-02-01
so once i rebooted the ubuntu logo was off, not centered. So i figured it didnt work, once it got to the login screen it was perfect. So i was happy and logged in. But once i logged in it swithced back, so i went through the display settings and found 1024x763 and it works perfectly! Thanks a lot!:p

Now what can we do about screen rotation when i fold it closed? And the buttons on the pen?

---

### Post by Favux on 2011-02-01
Hi Toxicstupidity,

Good.  So just to be absolutely clear you used the xorg.conf exactly as I posted, rebooted, and went into System > Preferences > Display and set it to 1024x768 at 60 Hz and everything is good?
> Now what can we do about screen rotation when i fold it closed?
Rotation has been broken for a while.  See this launchpad bug:  [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312)  Progress has been made because it's been triaged to confirmed and added to the wishlist.  You can see by the last post by James that the fix should actually be pretty simple.  Please keep the bug report alive by posting on it!

So you'll have to use it in landscape when in tablet mode, no portrait orientation available for you.
> And the buttons on the pen?
That should be easy.  You have a stylus with two buttons on it?  But no eraser on the back end of the stylus, correct?

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> 
That should be easy.  You have a stylus with two buttons on it?  But no eraser on the back end of the stylus, correct?

not exactly, it has one button on the side (for right click) and one on the end (im guessing is the eraser, it tracks the cursor and clicks when i push down)


also SDcard slot isnt reading my 1gig sd card and my 8gig SDHC card?

Also is their something i can download for linux that rotates it manually?

---

### Post by Favux on 2011-02-01
OK, let's make a xsetwacom script to give you control of the stylus and eraser.  To get tablet coordinates I need to see your Xorg.0.log.  It's located in /var/log.  It's big so you can compress it with a right click Create Archive and then attach it to your next post with Manage Attachments below.

Don't know about the SD card.  Do you see it in 'lspci' or 'lsusb'?  Do you know the name?  You could also look in Applications > System Tools > Device Manager.  And google for it:
```
site:ubuntuforums.org SD card
```
or whatever the appropriate keywords would be.

---

### Post by Toxicstupidity on 2011-02-01
I cannot connect the tablet to the internet or network (admin's choice) Is their anything else i can do or do i NEED to attach that?

---

### Post by Favux on 2011-02-01
Sure, open the Xorg.0.log in gedit and use Find to search for wacom.  In those highlighted lines will be something like:
```
[    88.920] (--) Wacom BambooPT 2FG 4x5 Pen stylus: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=1016 resol Y=1016
```
That's what we're looking for.  Post that line or at least the top X&Y and bottom X&Y, resolution is optional.

---

### Post by sandyd on 2011-02-01
> **Toxicstupidity said:**
> I cannot connect the tablet to the internet or network (admin's choice) Is their anything else i can do or do i NEED to attach that?
usbdriveit

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> Sure, open the Xorg.0.log in gedit and use Find to search for wacom.  In those highlighted lines will be something like:
```
[    88.920] (--) Wacom BambooPT 2FG 4x5 Pen stylus: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=1016 resol Y=1016
```That's what we're looking for.  Post that line or at least the top X&Y and bottom X&Y, resolution is optional.


```
 Wacom device "wacom Serial Tablet PC Pen Tablet/Digitizer" top x=0 top y=0 bottom X=24576 bottom Y=18432 resol x=2540 resol y= 2540 
```

but i also see things like 

```
 (**) Wacom Serial Tablet PC Pen Table/digitizer eraser: Forcing TabletPC ISD V4 protocol 
```

i dont know if thats important but it keeps mentioning the eraser


one othr thing, the laptop has a windows button, this is prob really easy but can i make that button pop the ubuntu menu up?

---

### Post by Favux on 2011-02-01
Good.  And post the output of:
```
xinput --list
```
in a terminal.

I'd think you could use Keyboard Shortcuts.  I have a dock.

---

### Post by Toxicstupidity on 2011-02-01
> **sandyd said:**
> usbdriveit

i will if needed

---

### Post by Toxicstupidity on 2011-02-01
```
 "Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"    id=2    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"    id=3    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Power Button"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=7    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AlpsPS/2 ALPS GlidePoint"    id=8    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 767
        Resolution is 1
"PS/2 Mouse"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Macintosh mouse button emulation"    id=10    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1


```

---

### Post by Favux on 2011-02-01
Alright, try the attached script below.

To set it up to auto-start, download the attached file, and rename it .xsetwacom.sh (or whatever you want) and place it in your home/username directory. Remember it will be a hidden file because of the . in front. To enable the xsetwacom commands in the .xsetwacom.sh file to apply to Xserver through a reboot you enter in a terminal:
```
chmod +x ~/.xsetwacom.sh
```
or you could right click on the file and in Properties, in the Permission tab, check Execute as program. Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh" (without the quotes). You can also change your settings on the fly using the xsetwacom parameters in a terminal. They only apply during the current session.

Once the script is executable you can double click on it to apply it's settings or reboot to check the auto-start set up.

In the example script below "Device name" is used, but you could use ID #. Be sure to check for yours using 'xinput --list' (without the quotes) in a terminal and use them. When you use a xorg.conf the "Device names" will be stylus, and eraser. If you are hot plugging into your tablet pc other devices be sure to use "Device name" as the ID # can change.

---

### Post by Toxicstupidity on 2011-02-01
Okay so before i do this let me know if i understand it right

(I downloaded it to a usb drive)

Move the file to "Home"
Rename it (now it should be hidden)
Open terminal
Type your posted code
Double click it (it should be an executable)

?

---

### Post by Favux on 2011-02-01
Yep.  And you can see it by checking View hidden files in Nautilus/Places.  It'll let you tweak things.

---

### Post by Toxicstupidity on 2011-02-01
and that will give me eraser functions and right clicking from the stylus?

---

### Post by Toxicstupidity on 2011-02-01
okay it wont let me drag into "home" because i am not "the owner of this computer" Even though i was the first and only acount made....

---

### Post by Favux on 2011-02-01
In Places on the left there will be your username.  Drop it on that.  That's /home/yourusername

Eraser only works in programs that support it like Gimp, Inkscape, Xournal etc.  For instructions see near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

You'll want Xournal, CellWriter, and maybe EasyStroke at least.

---

### Post by Toxicstupidity on 2011-02-01
okay so i did everything you said and nothing happened.
I opened up the file you gave me (with open office) and it was blank....

---

### Post by Favux on 2011-02-01
Just downloaded it myself and it's there.  You can see it's not blank on the attachment because it says it has 3.2 kb or whatever.  So I'm not sure what you did.

---

### Post by Toxicstupidity on 2011-02-01
hmm let me try again

---

### Post by Toxicstupidity on 2011-02-01
i did all the way up to 

> **Favux said:**
> Then go to System->Preferences->Startup Applications and click on add and for the command write "sh /home/yourusername/.xsetwacom.sh"

But it doesnt show up as an exe?

is it not suppost to? the stylus doesnt appear to be doing anything different

---

### Post by Toxicstupidity on 2011-02-01
ok i rebooted but nothing

---

### Post by Favux on 2011-02-01
.exe's are Windows, don't have them in linux.

The settings are mostly at the defaults.  Your stylus button should be a right click and pressure is a little softer than default for stylus and eraser and now you can control it and the other available settings.  For example if your calibration is a little off you can use the coordinates.

There used to be a gui configuration wacomcpl (Wacom Control Panel) but we lost it going from linuxwacom to xf86-input-wacom for the X driver.  But it used a xsetwacom script for its settings just like the one you now have anyway.

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> Your stylus button should be a right click and pressure is a little softer than default for stylus and eraser and now you can control it and the other available settings.

yeah it should but it literally did nothing...

---

### Post by Favux on 2011-02-01
Sounds like xsetwacom isn't working on your system.  Let's see what:
```
xsetwacom list
```
in a terminal shows us in its output.

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> Sounds like xsetwacom isn't working on your system.  Let's see what:
```
xsetwacom list
```in a terminal shows us in its output.

```
 The program "xsetwacom" is currently not installed. You can install it by typing g:
sudo apt-get install wacom-tools
xsetwacom: command not found

```

if  i have to install it i will see about getting internet to the tablet.... if not what do i have to do?

---

### Post by Favux on 2011-02-01
You never told me what version of Ubuntu you are using.  I assume you have the live CD.  What is it Lucid (10.04) or Maverick (10.10)?

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> You never told me what version of Ubuntu you are using.  I assume you have the live CD.  What is it Lucid (10.04) or Maverick (10.10)?

im not exactly suree, the CD they sent me doesnt say, i cant find it on the case either...   9.10 anyway

---

### Post by Favux on 2011-02-01
Makes a huge difference.  Let's see what kernel you have:
```
uname -r
```
and Xserver:
```
Xorg -version
```

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> Makes a huge difference.  Let's see what kernel you have:
```
uname -r
```and Xserver:
```
Xorg -version
```

2.6.31-14 generic 

X.Org X server 1.6.4

---

### Post by Favux on 2011-02-01
Aright, that's the Karmic kernel and X server so you have Karmic (9.10).  Your kernel is dated, so if you can get an internet connection and udate that would be good.

The good news is you should still have wacomcpl available, since Karmic uses linuxwacom's X driver not xf86-input-wacoms.  What you need to do is install wacom-tools through Synaptic Package Manager.  It should be on your CD.  Then reboot.

The bad news is you don't need the xsetwacom script we just installed although it should work as is.  If you want to use wacomcpl instead make a backup copy of it or inactivate it by renaming it .xsetwacom.sh.bak and remove it from your startup app.s.

Then to get the Wacom Control Panel just enter in a terminal:
```
wacomcpl
```
and it will pop up.  It may not work for you because the default version in Karmic expects to see the old names stylus & eraser, but a minor modification of your wacom.fdi will fix that.

---

### Post by Toxicstupidity on 2011-02-01
> **Favux said:**
> Aright, that's the Karmic kernel and X server so you have Karmic (9.10).  Your kernel is dated, so if you can get an internet connection and udate that would be good.

The good news is you should still have wacomcpl available, since Karmic uses linuxwacom's X driver not xf86-input-wacoms.  What you need to do is install wacom-tools through Synaptic Package Manager.  It should be on your CD.  Then reboot.

The bad news is you don't need the xsetwacom script we just installed although it should work as is.  If you want to use wacomcpl instead make a backup copy of it or inactivate it by renaming it .xsetwacom.sh.bak and remove it from your startup app.s.

Then to get the Wacom Control Panel just enter in a terminal:
```
wacomcpl
```and it will pop up.  It may not work for you because the default version in Karmic expects to see the old names stylus & eraser, but a minor modification of your wacom.fdi will fix that.


i need an internet connection to install wacom-tools right?

---

### Post by Favux on 2011-02-01
I'd think its on the CD.  I'm just not sure how you install it from the CD, never tried that except to reinstall Grub2.  Although it may not be there in which case you'd need the deb and then put it on a usb stick and then install it.  So getting it connected would help a lot.

---

