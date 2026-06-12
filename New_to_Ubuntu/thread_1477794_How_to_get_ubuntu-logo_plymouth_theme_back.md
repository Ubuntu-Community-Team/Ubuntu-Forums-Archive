---
title: "How to get ubuntu-logo plymouth theme back?"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by shunruo on 2010-05-09
Hi, friends, I need help.

After installed 10.04, the ubuntu-logo plymouth is all OK.
And I make the NVIDIA graphic driver active, well, the plymouth display mode was changed to 640*480,  After doing a lot of "Google...", Finally, I change the display mode to 1280*800*24 by edit /etc/default/grub, this is the very display mode that match my pc.

There the problem's come...  The plymouth theme was changed ,the logo's missing, just simple "ubuntu 10.04" was showed in the center.  Of course lot's of "google" work has been done. also  I tried the steps of the post [http://laptopny.us/ubuntu-tips/changecustom-lucid-lynx-ubuntu-10-04-splashxsplashplymouth](http://laptopny.us/ubuntu-tips/changecustom-lucid-lynx-ubuntu-10-04-splashxsplashplymouth)

there are several theme already installed, whatever I select, but the plymouth theme just the simple word "Ubuntu 10.04" was showed in the center.

How can I get the default plymouth theme back?    any help?

By the way, in the middle of fixing the "display mode problem", I used a solution from [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html) . Is that the reason lead to the later problem?

---

### Post by bwallum on 2010-05-09
Plymouth and nvidia proprietory drivers fight at the moment. Go to System>Administration>Hardware Drivers and disable any nvidia drivers you find there (so that the button alongside each driver is grey, not green).

Reboot a couple of times and see if the Ubuntu splash comes back. The Ubuntu default video drivers have been improved and you may find do everything you want. If you really need the nvidia proprietory drivers then you may have to wait for nvidia to provide a fix. You could try their web site for the latest news on nvidia linux drivers.

---

### Post by shunruo on 2010-05-09
Thx for reply.
It seems the driver is Okay. but the plymouth just run a wrong  theme.

I just don't know where is the key configuration of plymouth run a specified theme.

A few minutes ago, I updated the grub with the command:  
***sudo update-grub*** 

and,

***sudo update-alternatives --config default.plymouth*** 

change default plymouth to "ubuntu-logo"
[B]
*sudo update-initramfs -u*[/B]

-----------------------------
well, after a reboot, there display no plymouth theme,  It's all black before login window showed up.

It driven me crazy now.

---

### Post by bwallum on 2010-05-09
Have a look at this thread 

[http://ubuntuforums.org/showthread.php?p=9134802#post9134802](http://ubuntuforums.org/showthread.php?p=9134802#post9134802)

---

### Post by WinterRain on 2010-05-09
> **shunruo said:**
> 
It driven me crazy now.

Is the boot up screen important to you? It is a known fact that using the nvidia drivers will remove plymouth functionality. Perhaps be patient and wait for an update that fixes it. The boot up screen only shows for a few seconds anyway.

---

### Post by jerome1232 on 2010-05-09
Nvidia has pretty much stated they aren't going to incorporate kms into their drivers. You still get a low res splash, and yes these things are important to some of us. looks matter ;)

Unfortunately I know next to nothing about configuring plymouth. Does this thread help? 
[http://ubuntuforums.org/showthread.php?t=1440101](http://ubuntuforums.org/showthread.php?t=1440101)

---

### Post by -humanaut- on 2010-05-09
This has been a ridiculous bug that they can't seem to fix I just downloaded the updates from the "proposed updates" repository and it seems to be working right now doesn't mean it will be in an hour though.

---

### Post by -humanaut- on 2010-05-09
One boot this time! I miss Usplash.

---

### Post by vrix on 2010-05-10
hi!

that happened to me also. what i did was remove other themes using synaptic and leave one i like, then by editing /etc/default/grub, comment out this line:

#GRUB_CMDLINE_LINUX="splash vga=x" 

and this,

#GRUB_GFXMODE=640x480

then run:

$sudo update-grub2

it will restore the default splash screen.

hope this helps.

---

### Post by -humanaut- on 2010-05-10
The purposed updates installed hal and now Plymouth seems to be working this bug is getting weirder and weirder.

---

### Post by shunruo on 2010-05-11
Wow..., The bugs [bwallum]("http://ubuntuforums.org/member.php?u=249453") posted, which is exactly what I found during my first installation. 

I'll wait for the fix.

Thank U all.

---

### Post by shunruo on 2010-05-11
[URL="http://ubuntuforums.org/member.php?u=182520"]_Hi, vrix, I'll try.    thank you.:P_
[/URL]

---

### Post by shunruo on 2010-05-11
Oh, vrix, That changes nothing.  

Still burning....

---

### Post by jfreak_ on 2010-05-11
try my blog in the signature. First post links to the page that i used. Works fine for me.

---

### Post by jd65pl on 2010-05-11
Plymouth does work fine with Nvidia cards and proprietary drivers with some mild tinkering! There is no need to remove the proprietary drivers and revert to the nouveau drivers.

Look at [bug 506717]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/506717") and specifically at [this comment]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/506717/comments/80") for the fix.

My machine has a perfectly working plymouth and tty resolution:
GPU : GeForce GT 240
Nvidia driver version : 195.36.24

---

### Post by shunruo on 2010-05-13
Fixed. She's back.

Thank you all.

The tricks' simple.

1. remove all plymouth theme;
2. regenerate xorg.conf with "Nvidia X server settings"
3. reinstall ubuntu-logo theme;
4. retrieve grub file;

then , update grub and framebuffer.
---------------------------------

Thank you all ,again.

---

### Post by zer010 on 2011-02-26
> **shunruo said:**
> Fixed. She's back.

Thank you all.

The tricks' simple.

1. remove all plymouth theme;
2. regenerate xorg.conf with "Nvidia X server settings"
3. reinstall ubuntu-logo theme;
4. retrieve grub file;

then , update grub and framebuffer.
---------------------------------

Thank you all ,again.

Might you elaborate on steps 2., 4. and on updating the framebuffer? I would appreciate it as I'm having some trouple with mine: [http://ubuntuforums.org/showthread.php?t=1692742](http://ubuntuforums.org/showthread.php?t=1692742)

---

