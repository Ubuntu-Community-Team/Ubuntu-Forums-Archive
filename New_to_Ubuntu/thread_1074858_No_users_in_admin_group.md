---
title: "No users in admin group"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by animestudiogeek on 2009-02-19
**Problem:**
I have no users accessable on my computer in the admin group. Therefore, no sudo for me.

**Background Info:**
Ive got three users. One is the first I created when I first set up the computer, the second is another I created after, and the third is the root. Somehow when I created the second, I didn't add it to the admin group. I have no idea why but somewhere between there and an episode during which my miniscule HDD was filled, my main account was removed from the admin group as well. So, now, nobody but the root user has any access to admin privaledges and I can't login to that. Any help or advice?

**Some extra information:**
I've got a Dell Inspiron Mini 9 Laptop, which has only 4 GB on its HD ](*,). When that got filled,  none of the temporary folders needed for booting or even the failsafe session could be made. I'm still not sure what I did. I just continued trying to log in in various ways including failsafe GNOME and failsafe Terminal. The failsafe Terminal was the only one that worked for a while. Then I logged in to my main account and it worked so I took the chance and cleared some files. I now have an 80 gig USB drive \\:D/

---

### Post by cmnorton on 2009-02-19
It sounds like you have to boot with a live Ubuntu or recovery CD (like Knoppix) mount your drive containing /etc/group, and go edit that file, so your user is in admin.

---

### Post by animestudiogeek on 2009-02-19
I don't have a CD drive, though. Will it work if I copy the contents of the disk to a jump drive?

---

### Post by cmnorton on 2009-02-19
I believe you can boot from a jump drive, but you'll need to search for those instructions (on making a jump drive bootable). 

I don't know how old your BIOS (system) is, but you can boot from a USB CD/DVD drive, if you have one of those handy.

---

### Post by taurus on 2009-02-19
But since you already have a root (with password), can you just log in as root and edit /etc/group from there?  At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Log in as user root and password for root.  Then edit /etc/group.

```
nano -Bw /etc/group
```
<Ctrl>x to save and exit with nano text editing.

---

### Post by Peter09 on 2009-02-19
Just go to recovery mode, that will give you an admin prompt, from there add a user to the admin group.

---

### Post by animestudiogeek on 2009-02-19
> **cmnorton said:**
> I believe you can boot from a jump drive, but you'll need to search for those instructions (on making a jump drive bootable). 

I don't know how old your BIOS (system) is, but you can boot from a USB CD/DVD drive, if you have one of those handy.

I'm pretty sure you press 0 at the Dell screen to access the boot menu. And I got it for Christmas so I'm guessing the BIOS are fairly up to date. Unfortunately, I don't have a USB CD/DVD drive. I'm planning on getting one soon though.


> **taurus said:**
> But since you already have a root (with password), can you just log in as root and edit /etc/group from there?  At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Log in as user root and password for root.  Then edit /etc/group.

```
nano -Bw /etc/group
```
<Ctrl>x to save and exit with nano text editing.

Thanks I'll try that.


EDIT:
> **Peter09 said:**
> Just go to recovery mode, that will give you an admin prompt, from there add a user to the admin group.

How do you go into recovery mode?

---

### Post by Peter09 on 2009-02-19
To boot into recovery mode:
Hit the ESC key as soon as you see the grub prompt. This will stop the boot sequence. You can select recovery mode using the down arrows. Recovery mode is normally the second option of the list. Once selected hit the ENTER key and it should start to boot.

Note the command will be

```
useradd -g {group-name} username
```

---

### Post by animestudiogeek on 2009-02-19
Okay, thank you.

*EDIT:*
I can't find the option on the boot menu for Recovery Mode. There's options to boot from the hard drive, USB devices, removable devices, CD/DVD drives, and to go into Diagnostics. Also, I tried logging in from root with the prompt mentioned by Taurus. I managed to log in but it said that nano wasn't a recognized command. I noticed that most of these tips are coming from Intrepid users while I've got Hardy. Could that be a problem with any of these tips?

*EDIT:*
Apparently I didn't have nano installed. It's working again :D

---

