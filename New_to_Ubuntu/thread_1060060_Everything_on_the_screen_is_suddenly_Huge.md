---
title: "Everything on the screen is suddenly Huge"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by ellika on 2009-02-04
I am new to ubuntu and I was away for about a month. When I turned my computer on yesterday there were over a hundred updates. I did the updates and it told me to restart. I did and now everything is huge. I have to run ubuntu on the low graphics mode and that might have something to do with it. But everything is so large that when I go into the screen resolution or anywhere else to try to change stuff the boxes are so large that I cannot even get to the bottom of the boxes to change everything. I have no idea how to fix it. Any help or suggestions would be greatly appreciated.

---

### Post by Kellemora on 2009-02-04
Hi Ellika

First try this in Terminal.
```
 sudo dpkg-reconfigure-phigh xserver-xorg 
```

If that don't do it and you have the correct video driver installed, you can give the following a try.

Screen Resolution Problems?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
This document is to address Changing Screen Resolution using Preferences causes Screen to Roll horizontally, vertically or just mess up royally.  Also, only 640 x 480 resolution available in Preferences.  This fix may or may not allow you to select other available resolutions from the Preferences Option without changing MODE lines in /etc/X11/xorg.conf which I am not addressing here.
If this fix causes log-in screen obesity (HUGE SCREEN), see my other post titled Huge Log-in Screen?  Easy fix!  Which addresses that problem separately and easily.

To get started we need the Tool called Screens and Graphics.
If it is not available under Applications/Other, then RIGHT CLICK on Applications, select Edit Menu (left click) and wait for the Main Menu screen to open.  From the Main Menu, left column (Menus) select 'Other' and a new list of text will appear in the right screen (items).  Place a check mark in the box to the left of Screens and Graphics, this will automatically select 'Other' if it was NOT in your drop down list under Applications.  Close this window.
You will have to REBOOT for the change to take affect.

Once you're up and running again, left click on Applications/Other/Screens and Graphics.
A log-in screen will appear, type your Normal log-in password.  Why it don't ask for Root I don't know.

In the Screens and Graphics Preferences window select Graphics Card first just to check to make sure your correct graphics card is displayed.  Normally these entries are correct, but check them anyhow!

OK, now select the Screen Tab and get things set up to run properly.

Click on the little Monitor icon to the right of Model:  It may currently say Plug n Play.  A new (Choose Screen) window opens, from the Left window, select the Manufacturer of your Monitor.  The screen on the right will change to the models that manufacturer makes.  Scroll through the list to find your Monitors model name and number and/or identification.
If you have an .inf driver for your particular monitor and it is not listed, select add and follow the directions there.  I've not found a monitor not already in the listing yet.  Then I never have many new things either, that might not be listed long before I get it, hi hi.........  IF a Test button comes up, just IGNORE IT, because your screen will mess up royally.  After selecting your monitor, select OK!  This will bring you back to the Screen and Graphics Preferences screen.
Here you will select the desired resolution you would like your DESKTOP to run in.  The proper bandwidth should self-select, but check to make sure it's right for your monitor.  A wrong setting could damage your monitor!
Select OK and it will change and ask you if you want to Keep this setting.  If all looks OK, select YES.
This change, and all the default parameters for your selected monitor WILL be written to the /etc/X11/xorg.conf file.  Also, the Screens and Graphics window may show UNKNOWN for your monitor.  The result of this Unknown Monitor or sometimes even if the Monitor is KNOWN and displays correctly the resultant change to the xorg.conf file, may cause your log-in screen to become OBESE (HUGE) and you might not be able to see your log-in boxes.

But don't worry, you KNOW they are there! 
Just type in your log-in name, hit enter and type your password, hit enter and wait for the log-in to complete.  Your xwindow (Gnome or others) should be at the desired resolution now.

IF you did have the HUGE log-in problem, see my post on Huge Log-in Screen?  Easy fix!

TTUL
Gary/aka Kellemora

---

### Post by glotz on 2009-02-04
> **Kellemora said:**
> 
First try this in Terminal.
```
 sudo dpkg-reconfigure-phigh xserver-xorg 
```
Should be (note the extra space)
```
 sudo dpkg-reconfigure -phigh xserver-xorg 
```

---

### Post by ellika on 2009-02-04
Okay, I copy pasted both the codes into the terminal, the first didn't work and the 2nd one said this: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090204124554
no idea what that means. 

Then I tried to find the "Screens and Graphics" option under the "other" in main menu but it isn't on the part of the screen that I can see so I can't click on it to go any further. 

Any other suggestions? Thanks for the help so far.

---

### Post by glotz on 2009-02-04
That message means that there already was a xorg.conf and it was backupped to the file mentioned.

Try moving the box on screen by holding Alt and then drag & dropping the box around.

---

### Post by OffAxis on 2009-02-04
that -phigh switch stopped working for me a few years ago, and the remaining command
```
sudo dpkg-reconfigure xserver-xorg
```

just seems to be reconfiguring my keyboard for the most part.

To open the display configuration from the command line it would be:

```
sudo displayconfig-gtk
```

---

### Post by fvs on 2009-02-04
It worked great! Thanks Kellemora

---

