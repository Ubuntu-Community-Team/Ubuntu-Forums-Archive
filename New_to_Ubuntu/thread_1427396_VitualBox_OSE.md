---
title: "VitualBox OSE"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by Joe_Ib on 2010-03-11
Is there a way to make the screen in the vitualbox take up your whole monitor screen?  

When I hit the maximize button it makes the vitualbox take up the screen but the xp screen is still a small square that does not. 

I will be back on in about 2 hrs and 20mins to try any suggestions.

Thanks in advanced.

---

### Post by halitech on 2010-03-11
did you install the virtualbox addons and adjust the XP screen resolution?

---

### Post by r-senior on 2010-03-11
Yes, you need the additions I think. It's also worth checking the video memory allocated to the VM to make sure there's enough to display the size you would like.

The default keyboard shortcut to toggle fullscreen is to hold down the right Ctrl and f. Works fine for me with a Windows 2000 VM. Windows screen resolution changes dynamically, although some applications aren't always that happy about it.

---

### Post by blur xc on 2010-03-11
> **halitech said:**
> did you install the virtualbox addons and adjust the XP screen resolution?

You mean virtualbox guest additions...  You install them on the guest os- to my layman's way of understanding, they are like the device drivers for your virtual hardware.

BM

---

### Post by halitech on 2010-03-11
> **blur xc said:**
> You mean virtualbox guest additions...  You install them on the guest os- to my layman's way of understanding, they are like the device drivers for your virtual hardware.

BM

got the wrong term but thats what I meant.

---

### Post by MSich on 2010-03-11
I had to load the PEUL version from the Virtual box website and then load the newer guest additions before it worked for me.  It's worth the upgrade, better graphics, usb support and automatic mouse capture.

---

### Post by Joe_Ib on 2010-03-11
So how do I install the add ons sorry but All I can really do in Ubuntu right now is open firefox and virtual box.

---

### Post by Dayofswords on 2010-03-11
i thought there was a fullscreen option in the top menu

(havent used the OSE for a while)

---

### Post by NightwishFan on 2010-03-11
Click this link and hit ok to install the guest editions ISO. This will only work if you are on Karmic (9.10)
[apt://virtualbox-guest-additions]("apt://virtualbox-guest-additions")

When in virtualbox go to where you add CD images, and add /usr/share/virtualbox/guest-additions-iso (Something like that)

Start the virtual windows and hold f8 to get a menu. Choose safe mode. Mount the guest additions iso in Windows. While in safe mode run the Windows installer in the CD. Then reboot to normal boot.

---

### Post by diablo75 on 2010-03-11
To install the Guest Additions, you first start your VM up.  Once that's open, there's a menu at the top of the Window.  By the way, if you haven't installed them yet, your mouse will lock itself inside the VM when you click in it, and you have to press the Right-CTRL key to unlock it and give it back to Ubuntu.

Anyway, you'll see a menu at the top that says "Machine" "Device" "Help"

You'll want to click "Devices" and then at the bottom of that menu click "Install Guest Additions".

This will mount a virtual CD inside the VM and Windows XP should auto play it.  If it doesn't, browse to your My Computer to open the disk and run the Setup utility.  This will install some features that will let your mouse freely move in and out of the VM without having to hit that CTRL key anymore, improve graphic performance, change the screen resolution.

Often times what I have to do when I want the VM resolution to fill the window is maximize the Window.  If it's already maximized, I'll just un-maximize it then remaximize it and it should work.  If it doesn't, check your "Machine" menu to make sure that "Auto-Resize Guest Display" is checked.

---

### Post by Joe_Ib on 2010-03-11
Okay Thanks I got it now but one thing accidentally hit seamless mode and dont know how to get it out of that mode.

---

### Post by diablo75 on 2010-03-11
> **Joe_Ib said:**
> Okay Thanks I got it now but one thing accidentally hit seamless mode and dont know how to get it out of that mode.

RightCTRL+L

---

### Post by QIII on 2010-03-11
By the way...

The full-on VirtualBox is free -- for personal use if you agree to the PUEL.

You can download it from [www.virtualbox.org](www.virtualbox.org).

The consideration here is that it's not in the repos as OSE is, so you'd have to reinstall it if you did a fresh installation of Ubuntu.

But your virtual disks would still be in your /home partition if you put them there and saved your /home partition before reinstalling/upgrading.

---

