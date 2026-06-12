---
title: "[SOLVED] Portege 3500 tablet"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by littlematt on 2009-01-03
Hi
I recently installed ubuntu (Hardy Herron) on my Toshiba Portege 3500 tablet PC.

I've been trying for days now to get the stylus to work, but I can't get it to acknowledge it's existance.

I've tried altering xorg.conf using the examples here:
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
but it seems to make no difference, whatever I do.

Could anyone help me set this up?
Failing that, does anyone know of a way I can test if any raw data is being recieved from the screen?


LittleMatt

---

### Post by Favux on 2009-01-04
Hi littlematt,

Can you tell me what kind of video card you have?  ATI, nVidia, Intel?  Do you know what type of digitizer is built in.  Serial Wacom?  What capabilities?  Stylus, side button, eraser, touch?

In a terminal try:
```
lsmod | grep wacom
```
or:
```
lsmod
```
and look for wacom.  Might also try:
```
modinfo -d wacom
```

Could you post your xorg.conf as an attachment?

---

### Post by littlematt on 2009-01-05
Hi Favux

Thanks for replying. Sorry, I wasn't very helpful in my first post.

Graphics card: Trident CyberALADDiN-T Graphics accelerator

I think the digitiser is a serial wacom, but not sure about this. There's a stylus with eraser and a button on the side (gives right-click in XP)

lsmod | grep wacom returned nothing

lsmod gave a whole load of stuff, but I couldn't see wacom. Attached if this helps.

modinfo -d wacom returned:
USB Wacom Graphire and Wacom Intuos tablet driver

Also attached xorg.conf (after I've added bits about wacom and stuff, as per [http://ubuntuforums.org/showthread.php?t=1029397](http://ubuntuforums.org/showthread.php?t=1029397)


Hope this helps,
littlematt

---

### Post by Favux on 2009-01-05
Hi littlematt,

I'm pretty sure it's a serial tablet too.  To check in a terminal type:
```
dmesg | grep ttyS
```
In the return output should be "irq=4" or 5.

So given it's a serial tablet I've gone ahead and edited your xorg.conf based on what you told me you have:  stylus, side button, and eraser.  I've also taken the liberty of cleaning it up a little bit and rearranging it into a more logical (at least for me) order.  It looks like you're running two monitors.  I left your video stuff alone.

I think you have a linuxwacom module present, but it's not installed.  Go back to Loic2's wiki:
[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")
and follow the Installing the Latest Driver in Ubuntu link:
[https://help.ubuntu.com/community/Wacom/LatestDriver]("https://help.ubuntu.com/community/Wacom/LatestDriver")
and go ahead and install the kernel module and stuff again.

Actually the latest driver is 0.8.2 not 0.8.1-6, but we'll cross that bridge if we need to.

Be sure to back up your xorg.conf before doing anything to it.  Compare it side-by-side with my edited version to check out the changes, make sure you approve, and that I didn't goof.

Between the two you should get it working.

---

### Post by littlematt on 2009-01-05
Hi Favux


Thanks for the advice, I think the xorg.conf is fine, but I'm having problems installing the latest driver/kernel module thing. After sudo ./install, I get this message. I've no idea what this means, could you help?


matt@matt-laptop:~/Desktop/linuxwacom-0.8.2-1/prebuilt$ sudo ./install
Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
wacom_drv.so installed under /usr/lib/xorg/modules/input

Installing utility programs (wacdump, xidump, xsetwacom....)
Installed under /usr/local/bin

Installing wacomcpl......

Warning: wacomcpl requires tcl/tk being installed

./install: line 105: yum: command not found
./install: line 105: yum: command not found

Please install tcl/tk then run this script again

You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.

---

### Post by Favux on 2009-01-05
Hi littlematt,

Hey thanks for pointing out that the Linux Wacom Project released another linuxwacom driver version 0.8.2-1.  I'll have to see if I can install it with the tutorial I'm working on.

I don't think you need one that recent.  That's why I referred you to Loic2's wiki with 0.8.1-6.  I forget Hardy's kernel, is it 2.6.26 or 2.6.24?  Anyway typing "uname -r" in a terminal will tell you.

I think "Warning: wacomcpl requires tcl/tk being installed" means a library (or package) "tcl/tk" isn't installed.  You could hunt it down in Synaptics and try again.  But Synaptics version may not be recent enough.  It also seems to be telling you your kerenel is too old for 0.8.2-1.

I think Loic's wiki tells you how to remove installed stuff, which you probably want to do.

So to sum up you made changes to your xorg.conf using the xorg.conf I uploaded.  Your stylus still didn't work.  You went to Linux Wacom Project and started installing their latest using their HOW TO?  Or is this what you're getting from Loic2's wiki?  After all I noticed the package said it's prebuilt.

---

### Post by littlematt on 2009-01-05
Hi again

I updated teh xorg.conf as you suggested, with no effect. The wiki said "Download the latest drivers from the Linux Wacom Project," so on the wacom project site, I went straight to the download page and downloaded the top one. I guess this is "too recent" for my slightly outdated Hardy? Is that right, or have I got the wrong end of the stick?

Would it be easiest to use an older vertion of the file from the wacom project? Or will I have to try and install this tcl/tk file?


littlematt

---

### Post by Favux on 2009-01-05
Hi littlematt,

When the wiki was written the latest drivers were 0.8.1-6.  It may be that 0.8.2-1 is too recent for your kernel.  The instructions following the link to the Linux Wacom Project are all for 0.8.1-6.  So I'd download 0.8.1-6 (I think it's still available) and then continue on with the instructions.  Tip: smarter to copy and paste then type them into terminal.  There's some alternate ways/troubleshooting things listed too.  So it'd be a good idea to read through the stuff once before starting.

Good luck!

---

### Post by littlematt on 2009-01-06
Hi Favux


I've got it working at last, so thank you so much for your help!!

I followed the "Compiling the driver manually" section in [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) using the latest driver (0.8.1) and "./configure --enable-wacom --prefix=/usr" instead of just "./configure --prefix=/usr"


You've been a great help!


Cheers,
littlematt

---

### Post by Favux on 2009-01-06
Hi littlematt,

Great!  Good job.  I'm trying to get a sense of how many folks need to use the alternate configure command like you did.  Right now it seems like most tablet pc users do.  Who knows?

Could you do me a favor a post your xorg.conf as an attachment?  Do you need any help with rotation or what not?

---

### Post by littlematt on 2009-01-07
Hi agian

xorg.conf attached (though I don't think it's changed form your recomendation)

Rotation was my next goal. I was going to do some googleing first, and I'll  start a new thread if I run into problems.



Thanks agian
Matt

---

### Post by Favux on 2009-01-07
Hi littlematt,

Thanks for the xorg.conf.  The reason I asked about rotation is I have a rotation HOW TO at:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

It might be of some help.  Also if you could attach the output of:
```
xrandr -q --verbose
```
I might be able to help you with a script.  Did you say you have bezel buttons?  Do you get a keycode from them when you type xev in a terminal and then press them?

---

### Post by justind on 2009-03-21
> **littlematt said:**
> Hi agian

xorg.conf attached (though I don't think it's changed form your recomendation)

Rotation was my next goal. I was going to do some googleing first, and I'll  start a new thread if I run into problems.



Thanks agian
Matt

That xorg worked like a charm after installing the wacom drivers and tools. Thanks for posting it.

---

### Post by Favux on 2009-03-21
Hi justind,

Glad it worked for you!

If you get rotation working please let us know.  Otherwise please join us on the thread:

[http://ubuntuforums.org/showthread.php?t=1053210]("http://ubuntuforums.org/showthread.php?t=1053210")

It would be a good thing if you also posted on the bug report.  That would keep it active and show them there are users out there.  I just found some new information and posted it.

---

### Post by menephous on 2009-08-13
> **Favux said:**
> Hi littlematt,

Great!  Good job.  I'm trying to get a sense of how many folks need to use the alternate configure command like you did.  Right now it seems like most tablet pc users do.  Who knows?

Could you do me a favor a post your xorg.conf as an attachment?  Do you need any help with rotation or what not?
Hi Favux

Thanks to you I have my portege and ubuntu working with a full screen, Thank you, you are a godsend!

Grateful Jeff

---

### Post by Favux on 2009-08-13
Hi Jeff,

Welcome to Ubuntu forums!

Great!  Glad you are set up.

---

### Post by egidijus on 2009-12-16
Hi
according to the instructions given above I easily made my tablet P3500 work with a full screen with the newest wacom drivers 0.8.4-4 on ubuntu Karmic Coala by configuring wacom manually.
Thanks folk very much...

---

### Post by Favux on 2009-12-16
Hi egidijus,

Welcome to Ubuntu forums!

Good!  Another 3500 in action.

---

### Post by menephous on 2010-01-12
Hi Favux, 

I am struggling with my rotation though I have read your tutorial on how to do it. I have perhaps not understood how you accomplished these changes as I am not entirely familiar with how to manipulate Ubuntu and I have a number of cognitive handicaps. I have my stylus working fine and my screen is the correct resolution thanks to the forums. So for the most part 8.04 is working great on my Toshiba Portege 3500, but I need a little more help with the rotation. If you or someone reading this could offer more specific instruction on how to make it possible for me to rotate the screen left and right by 90 degrees and to invert it too I would be very grateful.

Thank you,
Jeff

---

### Post by Favux on 2010-01-12
Hi menephous,

You're not doing anything wrong.  The driver for the Trident video chipset hasn't supported rotation since Feisty or Gutsy.  See this launchpad bug report:  [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/162312)  The last post on it by James Le Cuirot (2009-11-29) seems to show some progress:
> Gentoo user here. I've just been trying to figure out exactly where this fails to see whether I can do something about it. I'm thinking that if it's already possible to rotate through xorg.conf, making it work through RandR can't be that hard. The request is made in XRRSetScreenConfigAndRate of libXrandr and the BadMatch reply is received here. What I can't figure out is where the request actually gets handled and where that BadMatch reply is actually generated. The request/response mechanism seems to be handled by libX11 but this doesn't have anything to do with the actual operation. It must surely be driver-specific so I've looked at xf86-video-intel and xf86-video-radeonhd and while there is RandR rotation stuff in there, I can't see anything that looks like it's dealing with such a request. I've not really hacked X before. Maybe I'll ask on a mailing list unless you guys have any ideas?
I don't know if he posted on the mailing list.  I'd suggest you also post on the bug report and help keep it alive.

We also looked at newer Tident drivers on this thread:  [http://ubuntuforums.org/showthread.php?t=1053210](http://ubuntuforums.org/showthread.php?t=1053210)

I think I may have just finally found the maintainer:  Dave Airlie <airlied@redhat.com>.  At least he's on the git repository:  [http://cgit.freedesktop.org/xorg/driver/xf86-video-trident/tag/?id=xf86-video-trident-1.3.3](http://cgit.freedesktop.org/xorg/driver/xf86-video-trident/tag/?id=xf86-video-trident-1.3.3)  which has a fairly recent date of 8-5-09.  I'll e-mail him and see if I can get a reply.

The Xorg mailing list:  [http://lists.freedesktop.org/mailman/listinfo/xorg](http://lists.freedesktop.org/mailman/listinfo/xorg)  is, I think, the proper place to ask for help.

---

### Post by menephous on 2010-01-13
Hi Favux,

Thank you for responding so fast :D. So I assume that you would not recommend that I attempt to edit the config and interface code myself ;). I have been playing around with the code to see what I can alter though I don't really know what I am doing :o. I should stop messing around with it as I keep breaking things, but it is kind of fun and I am learning a lot about Ubuntu and Debian in the process :). I will keep checking back to see if there is any progress and I will make a bug report too. Please Email (menephous@gmail.com) me if you find anything that might help me figure this rotation thing out.

Cheers,
Jeff

---

### Post by rana_mum on 2010-11-20
while the solution mentioned herein will allow Ubuntu on many a PC with
Trident CyberBlade Microsystems Ai1 (rev82) to boot with higher screen
resolution, the below mentioned script is generic one that will 
make it seem like breeze on P3500. I did not get any low graphics mode
warning at the start.

I edited my /etc/X11/xorg.conf in nano with sudo and simply typed out
the relevant portions....however, caution is recommended in backing up 
the xorg.conf

All the best to all those trying to revive their old laptops.




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

---

### Post by rana_mum on 2010-11-21
ok happy times are over.
Mathew, Pls help....
i have begun getting the low resolution message at start-up

:(

wonder where i went wrong.

---

