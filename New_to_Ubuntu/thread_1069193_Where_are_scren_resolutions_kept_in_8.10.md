---
title: "Where are scren resolutions kept in 8.10?"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by jmckean on 2009-02-13
I have a Dell Studio Hybrid running 8.10.  It has a digital flat panel.

I set my monitor to an apparently unsupported resolution.  The system blanked and never returned. (I am used to the system resetting from a bad resolution as long as I wait patiently, but it did not work this time.)  I have tried rebooting into recovery mode and rolling back my xorg.conf file, but that trick no longer works.

Is there another config file somewhere I can edit to restore my settings?  Where are the video configurations kept?  For that matter, where is the driver defined?

 I really don't want to reinstall.

---

### Post by RomeReactor on 2009-02-13
Hi. Did you try XFIX while in recovery mode?

---

### Post by jmckean on 2009-02-16
I have now.  No joy.

---

### Post by stalkingwolf on 2009-02-16
from the recovery root command try displayconfig-gtk.  in the regular terminal and sudo at the beginning.

---

### Post by superprash2003 on 2009-02-16
although this is not quite related to your issue, you could give this a try [http://www.prash-babu.com/2008/11/how-to-fix-no-screen-found-error-in.html](http://www.prash-babu.com/2008/11/how-to-fix-no-screen-found-error-in.html)

---

### Post by kimikrishna on 2009-02-16
i once had the same problem..

our staff mr.overdrank helped me.. wait.. i am quoting his reply here..

---

### Post by kimikrishna on 2009-02-16
try this first in root command prompt :
> sudo dpkg-reconfigure xserver-xorg

---

### Post by kimikrishna on 2009-02-16
if this did not help , try this one by one 

step 1 : > sudo /etc/init.d/gdm stop

step 2 : > sudo dpkg-reconfigure -phigh xserver-xorg

step 3 : > sudo /etc/init.d/gdm start


Hopefully this will return you to the desktop.

---

### Post by kimikrishna on 2009-02-16
try these and reply a success shout !

---

### Post by jmckean on 2009-02-16
I am not finding displayconfig-gtk in 8.10, and getting no hits apt-get.  Is there a package that needs to be installed?

---

### Post by durand on 2009-02-16
You should try posting this in the Dell forum: [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

I read a while back that Studio Hybrids don't work properly in ubuntu. This may have changed; you should look through that link.

---

### Post by RomeReactor on 2009-02-16
> **jmckean said:**
> I am not finding displayconfig-gtk in 8.10, and getting no hits apt-get.  Is there a package that needs to be installed?

displayconfig-gtk was discontinued for Intrepid. And now, the X server relies more on autoconfiguration at startup, so modifying xorg.conf may not work.

What video card does the system have? Try booting into a previous kernel and see if you get your display back.

---

### Post by malathion on 2009-02-16
Not sure if the OP's problem is related, but is a problem several users have been having recently with ATI drivers. I myself have, with apparent randomness, started experiencing it as of today. See the other recent threads for more information about it, though I haven't yet found a solution. It is clear that xfix will cause the monitor to display in the correct resolution but that compiz is still broken. More here:

[http://ubuntuforums.org/showthread.php?p=6745511#post6745511](http://ubuntuforums.org/showthread.php?p=6745511#post6745511)

---

### Post by jmckean on 2009-02-17
The driver is intel.  It uses one of the embedded intel graphics chips.

---

### Post by jmckean on 2009-02-17
Whoops, not true, the driver is i915.

---

### Post by jmckean on 2009-02-17
Sorry, no joy.

---

### Post by linux_tech on 2009-02-17
first step is to get a driver that works and get card to work
Then if you want to see available resolutions in terminal type 
```
xrandr
```
if driver is correct then resolutions should be there
If desired resolutions are listed, then you can switch to them using xrandr also.
You may also check your xorg.conf in /etc/X11/

---

### Post by jmckean on 2009-02-17
Thanks for everyone's help.  I cannot let this go on any longer.  I did a backup of \home last nite and will reinstall today.

But I would like to learn more about how this new video thing works.  I can see it is related to hotplug, but I don't really understand how.

It seems like they/we have abandoned the linux model of simple editable configuration files for some kind of obscure "it just works unless it doesn't" auto magic thingie.  And instead the "do one thing well" model, it looks like the goal is to suck all connected devices into it.

I would love to see some concept documentation that a user or mid-level administrator could understand.  I get the impression is does not exist.  I guess that means I should offer to help create it.

---

### Post by RomeReactor on 2009-02-17
It looks like you *can* [install displayconfig-gtk in Intrepid]("http://ubuntuforums.org/showpost.php?p=6175368&postcount=5") after all, even though it' not available for it. You need to install **guidance-backends** ([i386]("http://mirrors.xmission.com/ubuntu/pool/main/k/kde-guidance/guidance-backends_0.8.0svn20080103-0ubuntu16_i386.deb") or [AMD64]("http://mirrors.xmission.com/ubuntu/pool/main/k/kde-guidance/guidance-backends_0.8.0svn20080103-0ubuntu16_amd64.deb")), and then [this displayconfig-gtk]("http://mirrors.xmission.com/ubuntu/pool/main/d/displayconfig-gtk/displayconfig-gtk_0.3.10_all.deb") package. I just tried it, and it works. It might help you with your problem.

---

### Post by stalkingwolf on 2009-02-17
> **jmckean said:**
> I am not finding displayconfig-gtk in 8.10, and getting no hits apt-get.  Is there a package that needs to be installed?

If you are running from your desktop terminal you will need to use

```
sudo displayconfig-gtk
```

I do some checking for 8.10 something may have changed.

I get command not found when I tried it.  I seem to remember they "fixed something or changed it"  I will try
to locate the new command.

---

### Post by lukjad on 2009-02-17
@jmckean 

There is a hidden folder in your **/home/[username]/** folder called **.config**. If you rename/move this folder, you should be able to log in and view everything. The best way to do this would be to boot to the Ubuntu LiveCD and access your hard drive(s). Drill your way down to the /home/[YourUserName] and then press Ctrl+H. This will display the hidden files. Then look for the **.config** folder and rename it to something like **[DOT]config** or **backup.config**. You can also move it to another folder. Then reboot into Ubuntu, log in and all should be fine. 

If, however, you do not have the Ubuntu LiveCD, or any other, there is another way to doing it.

Boot to the login screen and press Ctrl+Alt+F1.

You should then see the virtual terminal prompting you for a username. Log in using your username and password. From there, drill your way to the /home/[YourUserName] folder on your hard drive. Then type:
```
rename .config bak.config
```

This should rename that folder. Then press Ctrl+Alt+F7 and log in normally. All should work.

Hope this helps!

(Please note that this has only been tested on Intrepid Ibex. It may or may not work with Hardy Heron.)

---

### Post by stalkingwolf on 2009-02-19
The only fix I have been able to find ( and it is not 100%) is to copy the
X11 file from an install that works Or the Live Cd if it works .  Then
remove the file in your install and replace it with the working one.

---

### Post by zevans on 2009-02-19
Good or bad, the version of X in Intrepid likes to figure things out itself and then lets the user choose between the resolutions it has guessed.

If you want to add a particular resolution / refresh combination you have to use xrandr now.

(For instance, I'm on an older CRT that isn't quite solid at 1024x768 / 85 which is what X picks for me - but 1024x768 / 80 is rock steady. So I used 
```
$ cvt 1024 768 80
# 1024x768 79.73 Hz (CVT) hsync: 64.34 kHz; pclk: 87.50 MHz
Modeline "1024x768_80.00"   87.50  1024 1088 1192 1360  768 771 775 807 -hsync +vsync
```

(cvt is a command line tool to calculate this string of gibberish for you.)

Then you have to tell the X server this is a new mode - cut and paste the output above...

```
xrandr --newmode "1024x768_80.00"   87.50  1024 1088 1192 1360  768 771 775 807 -hsync +vsync
```

Then you have to switch X to this mode on your display:
```
xrandr --output VGA --mode 1024x768_80.00
```

(or it should appear in the list of modes now in krandrtray or whatever the GNOME equivalent is.)

I have no idea how to make this sticky "properly", so for now I have put it all in a script that runs when I log in - anyone here know how you make xrandr remember the "default" mode if it isn't one that X finds automatically?

There are a lot of features missing from xrandr 1.2 - next release due in March I believe, so I am not even sure it will make it into Jaunty. Seems like Ubuntu has let go of the Xorg.conf branch slightly before the xrandr branch was ready to bear our weight properly - oh well!

---

### Post by jmckean on 2009-02-19
That xrandr trick actually sounds like it might work.  Thanks.  I went ahead and reinstalled, and I have just gotten everything back to where it was -- so I hope you will forgive me if I don't try it until I have to.

---

### Post by jessejazza on 2009-05-14
> **RomeReactor said:**
> displayconfig-gtk was discontinued for Intrepid. And now, the X server relies more on autoconfiguration at startup, so modifying xorg.conf may not work.

What video card does the system have? Try booting into a previous kernel and see if you get your display back.

I've read this thread through with interest. I thought the displayconfig-gtk was good for those that wanted to run an electronic whiteboard along with their normal monitor. One could have two monitors and graphic cards working nice and easily.

NOW what is one supposed to do. I followed the tip of attempting to install displayconfig-gtk along with the aother app from debian repo... my screen went blank. I ended up reinstalling 8.10... then went back to 8.04

How is the deprecation of displayconfig-gtk a step forward?

---

### Post by RomeReactor on 2009-05-14
> **jessejazza said:**
> I've read this thread through with interest. I thought the displayconfig-gtk was good for those that wanted to run an electronic whiteboard along with their normal monitor. One could have two monitors and graphic cards working nice and easily.

NOW what is one supposed to do. I followed the tip of attempting to install displayconfig-gtk along with the aother app from debian repo... my screen went blank. I ended up reinstalling 8.10... then went back to 8.04

How is the deprecation of displayconfig-gtk a step forward?

I don't know why displayconfig-gtk was dropped, though it could be due to having similar functionality to the gnome-display-properties application in 'System->Preferences->Screen Resolution'. If you have an ATI or nVidia card with the corresponding proprietary driver, you can change resolution and set up multiple displays with their respective control programs--Catalyst Control Center or nVidia Settings (disclaimer: I've always used a single monitor).

Last time I tried to install displayconfig-gtk in Intrepid it installed correctly, using the packages mentioned [here]("http://ubuntuforums.org/showpost.php?p=6748304&postcount=19") *after* the first link.

---

### Post by jessejazza on 2009-05-17
Thanks for your reply. Each release i wonder what steps forward ubuntu make... they seem to do the odd one in reverse! Earlier today i spent a while looking at other distros seeing what they are like.

I still think ubuntu is best but they certainly seem to do some odd things. When i tried 8.10 and attempted to set the resolution to 1024 x 768 it couldn't be done. I've found they seem to try new things in the october release and then redo for April - so i stay with April releases.

---

### Post by jessejazza on 2009-06-22
Just been looking at Xubuntu 9.04 and Fedora 11 this w/e.

In both i could change resolutions and all would work perfectly. Tried ubuntu 9.04 and still the same problem. So it does seem to be a ubuntu problem to me.

They'd do well to go back to displayconfig-gtk imho.

---

