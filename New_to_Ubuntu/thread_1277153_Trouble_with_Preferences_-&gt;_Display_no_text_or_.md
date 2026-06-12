---
title: "Trouble with Preferences -&gt; Display no text or buttons"
date: 2009-09-28
forum: New to Ubuntu
---

### Post by GiantSpider on 2009-09-28
A day or two ago I changed my resolution in Ubuntu 9.04 using System -> Preferences -> Display. Now I cannot, there is no text or buttons. To top it off I can't close the pop-up window that clicking on Display shows. The window persists and slows down the system until I reboot. 

  Has anyone else had this issue? I haven't done much to my system. Mostly I've been messing around with Wine and using a virtual desktop. That should not mess up my display options. I wanted to play Diablo II but the resolution is limited to the upper left hand corner. I wanted to use the entire screen. I was also trying to get Windows version of firefox to run better on Ubuntu. 

   I was also messing around with the terminal some. Trying to make my own .sh files. All I did was cd, I doubt a change directory command could mess up anything.

---

### Post by GiantSpider on 2009-09-28
In an attempt to fix the problem I made it worse. I started Ubuntu in recovery mode and tried to fix graphical errors I also tried to check the file system and fix packets.

  Now when Ubuntu boots it has graphical errors and the screen freezes. One of two graphical errors occur either there is two ubuntu logos with the loading bar. The logos are all fuzzy. The other error is just a black screen with green and blue pixels at the top. 

  I didn't know I could make the system worse using the recovery mode. I fixed a problem before with an error on my laptop. I had the problem computer running Ubuntu for over 2 weeks now so I doubt it was a bad download I did a check sum and everything.

edit: The only way to break the lock on my computer is to unplug or hold down power button for 10 secs. This is a dual-boot and the Windows side boots up just fine so I doubt its a hardware issue.

---

### Post by Darkwing-Duck on 2009-09-28
If you can boot back into recovery mode again try to reset XOrg with:
 
```
dpkg-reconfigure xserver-xorg
```
 
Hopefully this should get you back to a point where you can work with it again.
 
Tip for the future. When you play with settings in xorg.conf made a working copy of it so you can replace it if needed.
 
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
 
Maybe this can help you in the future.

---

### Post by GiantSpider on 2009-09-29
Thanks for the advice. Now what is XOrg exactly? I've used Windows for almost 10 years now and never had to do something so advanced. Ubuntu claims its more stable, maybe Wine makes it less stable or I did something dumb. So when exactly do I type this in? I think if I hit c or something at the right time it takes me to a command line. I know enough that I need a command line to do it.

Wait by boot back into recovery mode you mean reach the desktop? I can't reach the desktop as of yet. Though I haven't tried the 2nd set of kernel options. I've only tried the default kernel normal boot and default kernel recovery. I still can't believe the number of problems and knowledge I've learned since installing Ubuntu.

---

### Post by Darkwing-Duck on 2009-09-29
It's okay man. I remember coming from windows and being blown away. But, it's gets better with time.

In answer to your questions. You have been using windows for a while so you will remember DOS prompts. 

The terminal acts much in the same way. There are a list of terminal commands that you can find and use. To get to the terminal go to Applications > Accessories > Terminal

However, since you can't get that far I'm getting a little ahead of myself.

Do you have a live CD handy?

---

### Post by GiantSpider on 2009-09-29
Yes, I do I'm going to go boot from live cd right now and try that command.

edit:quick update put live cd in did live boot with no changes showed ubuntu screen then had graphic error for like 4 seconds then desktop came up.

edit: on second thought its late I'll wait to tommrow don't want to format the hard drive or anything by accident. Not even sure what you can/can't do booting from a live cd.

---

### Post by Darkwing-Duck on 2009-09-29
I'll keep an eye on here throughout the day. I am sure that we will be able to help you out. :)

---

### Post by GiantSpider on 2009-09-29
Ok I typed the command, needed sudo so I re-entered with sudo in front. Now I will hit yes to turn on the use kernel framebuffer device interface. Keeping keyboard layout, us. Keeping xorg keyboard rule set. 

Now I'm having trouble on the next screen it says I should enter pc104 since I'm using a keyboard with the windows key. I click ok does nothing I hit enter does nothing. It says configuring xserver -xorg in red at the top.

edit it to work. I exited and re did command and when I got stuck again I hit right arrow and it highlighted ok.

Ok I completed it, said postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf etc. I'm tired I'll see if it fixed it tommorow.

---

### Post by GiantSpider on 2009-09-30
Ok typing in the command in terminal didn't work. I typed in 
dpkg-reconfigure xserver-xorg

After I went through all the prompts it took me back to the terminal. I waited a min then closed the terminal and rebooted, normal boot. I'm going to try to get to the desktop via recovery mode.

edit: Nay using recovery mode then normal boot didn't work. Btw when I hit recovery mode it went through a screen real fast that had ok on the leftside as it checked things. The very last thing grub checked before going to the recovery mode screen was a fail in red letters. No idea what it was though because the screen immediately changed.

---

### Post by GiantSpider on 2009-10-01
Been over twenty four hours since my last post. I'm still not able to reach the desktop other than by live cd. I am going to try the command again: 
dpkg-reconfigure xserver-xorg

Other solutions: Different graphics card, I sold my old graphics card shame to uninstall a $200 card, there's no on board video so I'll have to salvage the card from another computer. 

Wipe the hard drive: ouch, overkill but should fix the problem unless the problem is bound to happen every so often because of a hardware compatibility. Can I extract files from Ubuntu that are encrypted from live cd or from vista boot? 

Google the problem and hope I find something. This solution would take the longest since I don't have an accurate description of the problem other than a generic freeze while booting.

edit: I just entered the command again, I swear its over so fast that it can't do anything. I also support the claim this command does nothing but only two lines of output in terminal. Then again changing a .sh to an executable produces no lines.

---

