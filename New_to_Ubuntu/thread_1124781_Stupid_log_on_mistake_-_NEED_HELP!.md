---
title: "Stupid log on mistake - NEED HELP!"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by paraven on 2009-04-13
Hi - I am not new to computers but got my first Ubuntu system today on a Dell Netbook and am really looking forward to it!

I made a stupid mistake!  After signing in with my first user name, I thought I would just make ROOT the administrator and not have any other admins.  So, I took away MY admin privileges too.  But then I couldn't use the ROOT as admin, so now I have NO ADMIN!  I have tried playing around with the terminal to delete the user or fix it, but I just don't know how to get myself logged off and use ROOT alone to eliminate (or fix) the problem.

If I knew how to do a full system restore, I would do that because I haven't done a thing on the computer yet except mess it up!

Can you help me??

---

### Post by taurus on 2009-04-13
Can you boot your machine to recovery mode from GRUB menu?  You can add your username name back to group admin in /etc/group to give you root privilege again.

---

### Post by halitech on 2009-04-13
enabling the root account is not a good idea and against forum support policy for the very reason you have just demonstrated :D

you might want to read here: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

do you have an install cd that you can boot from? I believe you basically need to either boot from the install cd or when GRUB comes up, boot into single user mode to resolve your issue.

---

### Post by Jakey_TheSnake on 2009-04-13
Type in:

sudo gedit /etc/group

Then where it says "admin" add your name.

edit: this was assuming you could boot at all, argh I didn't read properly before posting. Too tired, it's almost 11:30pm, night guys -_-

---

### Post by paraven on 2009-04-13
How do I get to GRUBB?

---

### Post by halitech on 2009-04-13
when you start the computer, you should get a list of OSes that are installed, select single user mode (or safe mode) and that will take you in as root

---

### Post by paraven on 2009-04-13
I don't get a list of OSes.  I have the choice of pressing 2 to get to the BIOS or 0 which then does nothing and I can't even get the keyboard to work when it does get to the login screen.  Still not making any progress here...

I am very thankful for all of your input however!

> **halitech said:**
> when you start the computer, you should get a list of OSes that are installed, select single user mode (or safe mode) and that will take you in as root

---

### Post by halitech on 2009-04-13
it will be after the BIOS setup menu. Not sure but maybe you need to hit ESC to show the GRUB menu when you boot.

---

### Post by paraven on 2009-04-13
What does the GRUBB look like?  Is it a black screen with a prompt?  I get to something but it doesn't allow me to type anything.

Can't I just restore the system to its original configuration?

---

### Post by halitech on 2009-04-13
it will be a black screen but you should have alist of versions installed plus memtest86  and single user modes.

only way I know to restore a system is by reinstalling because linux doesn't have a restore feautre like windows because as someones tagline said, linux assumes you know what you are doing.

---

### Post by paraven on 2009-04-13
ok - so how do I reinstall Ubuntu on a netbook without an optical drive - is there a way to hook it to my laptop or desktop and just run the restore CD there?

---

### Post by Jakey_TheSnake on 2009-04-14
GRUB should look something like this: [http://tugulab.files.wordpress.com/2008/02/grub_prima.png](http://tugulab.files.wordpress.com/2008/02/grub_prima.png)

[SIZE="3"]_Attempted Fix_[/SIZE]

Boot laptop off of a LiveCD, type in:

```
sudo gedit /etc/group
```

Then where it says "admin" append your name, for example mine looks like this: 

> admin:x:121:jake

Then reboot and see if you can log in as your user and have admin privileges. 

[SIZE="3"]_To Reinstall_[/SIZE]

Download a Ubuntu.iso disk image to one of your other computers (I am assuming they run Windows), then boot off of a LiveCD and go to System > Administration > USB Startup Disc Creator, then find the USB on your Windows partition. In the navigation menu on the left hand side, it will be in "160GB Media" for example, then if it was on your desktop Documents and Settings > Username > Desktop. 

Then insert a USB drive of capacity greater than 1GB, press continue and wait. 

You can now boot from that USB pen drive, so put it in your computer. If it does not, you will need to go into your BIOS settings and move the "USB HDD" (it may even have your USB stick's name here, if it is plugged in at ths point) or similar option above "HDD0" or "IDE0" (this is your hard-drive). 

Continue with the installation prompts to reinstall. 

NB - I believe the USB creator comes with the LiveCD, if not go to System > Administration > Synaptic Package Manager, search for "usb-creator" and install it.

---

### Post by nandemonai on 2009-04-14
On systems with only Ubuntu installed grub will only show for a second before booting. You have to hit <esc> to get to the grub menu.

Next time don't remove your first user from the admin group ;)

Root is disabled on Ubuntu for good reason. Create your first admin user then if you wish add another user without admin access for daily use.

Good luck getting it reinstalled. USB would likely be your best bet.

---

### Post by paraven on 2009-04-14
OKAY!  I finally got it last night by going into the Terminal and doing the FIX that Jake suggested.  I added myself back in on all the lines that root was at.  It worked!  Thank you all so much for your help.  I didn't have to do a reinstall - this fix was much better once I figured it out.  I guess I have a lot to learn.

---

