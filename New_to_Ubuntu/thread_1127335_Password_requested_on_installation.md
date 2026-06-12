---
title: "Password requested on installation?"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by kountryguy on 2009-04-16
It has been awhile since i have messed with Linux, too long in fact. However, after getting a copy of Ubuntu off a friend, and trying to install it, the installer is asking for a login and password. Could this be a bad copy, or is it trying to run directly off the CD?

---

### Post by BDNiner on 2009-04-16
Is it asking you to setup a login account? the live cd automatically logs in when it boots so you should not get prompted to login.

---

### Post by Elfy on 2009-04-16
Shouldn't ask for a user if it's booting from the livecd - although I have needed one when I've logged out of a livecd - user was ubuntu with no password

But - in the past generally it has seemed to be a bad burn/download. Did the friend ever get it to boot?

---

### Post by kountryguy on 2009-04-16
Yes, the friend I got it from installed it without a problem. And it isn't asking me to set up an account, which was my first thought...rather, it is assuming I already have an account set up and wants me to log in...
Thinking I may just have to download a fresh copy ... might be easier than trying to debug this thing.

---

### Post by pme 72 on 2009-04-17
I had the same problem with the 8.04 Desktop CD. Running the Live CD-trying Ubuntu without any change to your computer- I was unable to get past the login screen which should not normally appear until you actually load Ubuntu onto your hard drive. 

Your graphics card may be preventing the Live CD from running. I recently installed a new card and disabled my integrated graphics and now the 8.04 Desktop CD will run without presenting a login screen. 

I found these notes from an attempt to log in with my old graphics card:

	Reboot with the CD in your CD/DVD drive
	OK English Language
	When the "Input Signal Out of Range" message comes up cntrl-alt-F1 to bring up a terminal screen
	type "Sudo apt-get remove compiz" at the prompt >Yes
	type "Sudo apt-get remove compiz-core" >Yes
	Cntrl-alt-F7 to return to GUI
	Cntrl-Alt-backspace to restart X
	It appears to boot into the Fail Safe mode.

If this works there is a conflict between your graphics card and compiz. 

You may still be able to install the OS but you might want to try another version. I did not have the same problem with Intrepid, 8.10.

---

