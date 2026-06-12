---
title: "Vista in dual boot --&gt; VirtualBox"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Sedative on 2009-06-09
I'm having troubles trying to get Vista into a VB because I have 3 recovery disks and I'm a moron with this stuff. 
I have Vista on a dual boot, and I'm wondering if it's possible to put that into the Virtual Box?

---

### Post by raymondh on 2009-06-09
> **Sedative said:**
> I'm having troubles trying to get Vista into a VB because I have 3 recovery disks and I'm a moron with this stuff. 
I have Vista on a dual boot, and I'm wondering if it's possible to put that into the Virtual Box?

What I did was put windows 7 RC in VB.  That way, if something crashes in VB, I still have a working Vista in my 2-boot system.

Regards.

---

### Post by Johan-Steyn on 2009-06-09
Hi

I used to have a dual-boot configuration with XP and Ubuntu.

The reason for this was to maintain a few client-based applications that could not run natively in Linux, even under wine. But having to reboot to XP six times a day was not a pleasure - until Vitual Box.

A few tips: 

Forget the Virtual Box (OSE) in the repository - no usb support. If you are going to for it, install the Version 2.2.4 (free but not open sourced) edition.

Download it from: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Choose the Jaunty i386 deb download. After downloading, install using the Gdebi package installer. After install find it Applications>System Tools menu.

Here's a tutorial: [http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/how-to-install-virtualbox-220-in-ubuntu-904-jaunty.html)

For configuration help, check out: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Bottom-line: It worked so well, I dumped XP and the dual-boot altogether. All our office computers now run it.

Regards,

JS

---

### Post by Sedative on 2009-06-09
I installed The VirtualBox, but there is no "System Tools."

---

### Post by Johan-Steyn on 2009-06-09
Hi,

Which version did you install?

The Virtualbox OSE's shortcut will be in the Applications>Accessories menu.

The Virualbox 2.2.4's shortcut ought to be in the Applications>System Tools menu.

Regards,

JS

---

### Post by Sedative on 2009-06-09
I installed the version you gave me. 

There is no Applications>System Tools.

Just:

Accessories
Games
Graphics
Internet 
Office
Sound & Video

---

### Post by run1206 on 2009-06-09
there's a discussion about running Vista in VirtualBox while dual-booting Intrepid/Vista (probably was updated recently to accomedate Jaunty).

link: [http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

i don't think they figured out the bug with the activation file needed to cancel the activation reminder in Vista; it's the only reason why i haven't virtualized Vista yet :(

good ol' days of virtualizing XP in Intrepid...
[IMG]http://i165.photobucket.com/albums/u43/run1206/Screenshot-3.png[/IMG]

---

### Post by nandemonai on 2009-06-09
Right click the applications menu and hit 'edit menus'. You may need to check that system tools is being shown.

That said, in regard to your first post, you want to run your existing real install from within virtual box? That's not going to happen I'm afraid. Different hardware (it's all virtual hardware in vbox) and I'm fairly sure you can't use a real disk for virtual box either, it must be virtual hard disk file.

This is also pretty much the reason your recovery discs will not work with virtual box, for all intensive purposes it's a 'new' machine, all be it virtual. You would need a full Windows install disc.

Edit:

Scratch that, looks like you can do it with a little work. :P

---

### Post by Sedative on 2009-06-09
Oh, that's a shame that I can't do that. 

Anyway, "System Tools" is checked in the "edit menus," but it isn't showing up.

EDIT:

Oh, good. x)

EDIT 2: 

Since I can't see System Tools, I  moved the Virtual Box to Accessories.

---

### Post by run1206 on 2009-06-09
> **nandemonai said:**
> Right click the applications menu and hit 'edit menus'. You may need to check that system tools is being shown.

That said, in regard to your first post, you want to run your existing real install from within virtual box? That's not going to happen I'm afraid. Different hardware (it's all virtual hardware in vbox) and I'm fairly sure you can't use a real disk for virtual box either, it must be virtual hard disk file.

This is also pretty much the reason your recovery discs will not work with virtual box, for all intensive purposes it's a 'new' machine, all be it virtual. You would need a full Windows install disc.

Edit:

Scratch that, looks like you can do it with a little work. :P

this is where creating a "virtual disk" comes in....
refer to the link i put up before: there's a tutorial of how to make one and run your virtualized OS from there.

---

### Post by Johan-Steyn on 2009-06-09
Hi,

Ok, lets see if you are included in the Virtual Box group.

Click on System>Administration>Users and Groups

Select your profile (user name).

When that is highlighted, click on Unlock.

Enter your user password when prompted.

Click Properties and go to User Privileges.

Make sure all tabs are selected including virtualbox at the bottom.

Click on OK.

Go to Manage Groups. Find vboxusers and click on Properties.

Make sure your name is selected. Click OK and Close.

Re-check if Virtual Box is in System Tools. Post back if still not.

Regards,

JS

---

### Post by nandemonai on 2009-06-09
> **run1206 said:**
> this is where creating a "virtual disk" comes in....
refer to the link i put up before: there's a tutorial of how to make one and run your virtualized OS from there.

Yeah I noticed just after I posted, pretty handy though I would have thought Vista would have a heart attack and die due to completely different hardware, also there is activation to consider.

---

### Post by Sedative on 2009-06-09
I'm getting really stressed. Nothing is working. I'm about to throw my computer out the window.

---

### Post by Johan-Steyn on 2009-06-09
Hi,

Throwing it out the window will not relieve your stress, it will just cost you a new HP Pavilion laptop.

What is not working?

Regards,

JS

---

### Post by Sedative on 2009-06-09
My recovery disks and the guide run1206 posted.

I know someone with a XP Pro CD that I could get tonight. Should In get that and sue it instead of going through all of this trouble with Vista?

---

### Post by run1206 on 2009-06-09
> **Sedative said:**
> My recovery disks and the guide run1206 posted.

I know someone with a XP Pro CD that I could get tonight. Should In get that and sue it instead of going through all of this trouble with Vista?

you can definitely get XP to work inside virtualBox while in Linux, i did it last year.  

the guide i posted is still in a working progress, i'm reading through it now and haven't seen anybody solve the activation problem. Most people are having hardware issues with their setups :( .

---

### Post by Johan-Steyn on 2009-06-09
Hi

It looks like installing Vista using the HP recovery discs is problematic.

Please see this post: [http://ubuntuforums.org/showthread.php?t=1123884](http://ubuntuforums.org/showthread.php?t=1123884)

I am afraid I don't have any better advice to offer you, if the instructions is canabal's guide don't work, than to suggest you obtain a full install copy of Vista and install that (which will work).

Good luck!

Regards,  

JS

---

### Post by Sedative on 2009-06-09
Well, it looks like I got a few hours, then I'll be able to run XP inside the VB.

---

