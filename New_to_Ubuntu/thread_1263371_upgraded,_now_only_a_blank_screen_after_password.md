---
title: "upgraded, now only a blank screen after password"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by jumpingchump on 2009-09-10
Hello! 

I recently bought a new notebook -- first time I've ever had a portable computer -- and I decided to install Ubuntu/Windows to dual-boot. A friend gave me a usb key months ago with Ubuntu 8.10 on it. I tried it out on the new noteboook (booting from the key), liked it, read up on how to install with dual boot, and sucessfully installed Ubuntu 8.10. 

I then downloaded and installed all the updates that had come out since my friend loaded 8.10 onto the usb key. That took a while, but it worked. I then thought, "What the heck, I might as well upgrade to 9.04," which is where my problems began. 

The upgrade went fine, but then it reached a point where I was asked if I wanted to keep a particular setting from 8.10 or use the setting from 9.04 (the setting had something to do with one of the intitial screens that come up when logging in or booting up). I read through the text, and chose to go with the setting from 9.04. I clicked the button to proceed, and after that, some text flashed across the screen and then went completely blank. I noticed, just as this was happening, that the battery was low and the computer unplugged (okay, okay, okay, yes, I admit it -- I'm a bit of a chump when it comes to computers).

So I don't know if it was me choosing to go with the 9.04 setting or the power failing that caused it (I suspect it was probably as a result of my choice) but the situation is now this:

I can boot into Windows XP just fine. But when I boot into Ubuntu 9.04 (which is the default), after I enter my user name and password, the screen just goes completely blank. The cursor is there, as the little white arrow, and it responds to the touch pad, but the screen is a blank black space with nothing going on.

Here's some info about the machine: Toshiba NB200, CPU N280 @ 1.66GHz, 0.99GB of RAM. 

Should I download 9.04 to a usb key (there is no optical drive on the machine) and then booting from that? Any suggestions are greatly appreachiated. 

Thanks!

---

### Post by cariboo on 2009-09-10
Try starting in recovery mode, once at the menu select drop to root prompt. once at the prompt type:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Once the above command finishes, type exit, then from the menu select resume. This should get you back to your desktop, once there, go to System-->Administration-->Hardware Drivers and enable the restricted drivers for your video card.

---

### Post by jumpingchump on 2009-09-11
Hi there and thanks for taking the time to get back to me on this!

The only thing is, when I try the above steps, after I type in the code, the computer responds with:  

mv: cannot stat '/etc/Xll/xorg.conf': No such file or directory

Any suggestions? Also, the menu has an option:

xfix Try to auto repair graphic problems

Should I try that?

Thanks again, eh!

---

### Post by GMachine_24 on 2009-09-11
Hey - this is probably not going to be much help but might save you time in the long run.

I tried to "upgrade" Ubuntu once - back before 6.04 or something. It was a disaster. The computer froze; I tried to fix it but it was a waste of time.

Ever since I have just kept backups of everything (using "tar") and a separate backup of documents, files, what have you that can easily be copied to any new installation. Oh yeah I forgot to mention I just wipe the hard drive clean and install the new version fresh. I think you will save yourself much time and aggravation in the long run.

Best of luck.

GM

PS - you can even create a separate partition to keep docs and other personal stuff on so when you do upgrade your OS those remain safe.

---

### Post by Chronon on 2009-09-11
> **jumpingchump said:**
> 

mv: cannot stat '/etc/X**ll**/xorg.conf': No such file or directory

Any suggestions? Also, the menu has an option:

xfix Try to auto repair graphic problems

Should I try that?

Thanks again, eh!

Those should be ones, not lowercase Ls.

---

### Post by jumpingchump on 2009-09-11
Chronon: thanks for pointing that out, but even when I tried it with ones I get the same message, "No such files or directory."

GMachine_24: Yeah, I might just do that next time -- wipe it clean and start fresh rather than try to upgrade from one version to the next. I thought it would actually be easier to do it the way I did. But hey, I'm new to Linux, so I'm just on a steep learning curve, that's all! 

I have all my files backed up, and because I can still boot into Windows, I haven't lost anything crucial -- I just haven't managed to get to where I was hoping to get, which was a Windows-free environment. 

Any other suggestions? I'm still not getting further with Ubuntu. I am tempted to try that "xfix" command from the recovery mode menu. 

Cheers

---

### Post by R3fr4cti0n on 2009-09-11
if i was you man, i would get on XP, and burn yourself a 9.04 boot disk from Ubuntu.com and delete your old partition>reinstall i have had this happen 2 me twice... its quicker to just reinstall

---

### Post by jumpingchump on 2009-09-12
I am hesitant to uninstall and then reinstall as doing so -- if I understand the forum posts correctly -- seems to carry the potential of uninstalling grub and disabling the ability to boot into Windows. So I tried the xfix function and came back with what seems to be some good info. It says:

xserver-xorg is broken or not fully installed 

Given that I am trying (perhaps foolishly) to get this working on a notebook without an optical drive so I can't just load in the boot CD again, are there any other ways I can fix this? 

Thanks.

---

### Post by jumpingchump on 2009-09-12
Whoo-hoo! I started in recovery mode and chose the "repair damaged packets" (or words to that effect) option and yes! it now works!!!! :):o:D

excellent excellent -- I am so very happy with how this turned out!

---

### Post by Windows Nerd on 2009-09-12
Did your computer actually shut down during the installation, or just reach low battery? If it did, then your probably better off with a reinstall, as there is a possibility that the install was corrupted beyond repair because the install process was halted in the middle. 

Scott

---

### Post by jumpingchump on 2009-09-16
Hi Scott, 

To be honest, I can't remember! But it seems to be working fine now, so I'm going to just keep on going with it. 

Cheers,

Mark

---

