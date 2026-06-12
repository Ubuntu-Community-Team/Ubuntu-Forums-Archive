---
title: "agere lucent winmodem cant edit grub?"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2006-12-16
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
Following these I ran scanModem and I have an agere supported chipset.

However I can not make changes to files. I cant put the line KERNEL="tty etc....
into rules.d folder
I can not edit grub, it comes up as read only. 
I can not log in from the login page as 'root', it says I cant login there as administrator.
I dont know how to get around this.
This is my own computer and I am apparently locked out from making the changes the web site says I have to make. 
I checked my own user priveleges and they are checked off. 
So how do you do this? 
for the 10-local.rules, I go to the folder area and see it but cant copy my text file in there.
For grub I am clicking on the menu.1st file to open it.
perhaps this is very basic to some of you, but not to me.

---

### Post by tbroderick on 2006-12-16
Run your text editor as sudo for nano or gksu for gedit. So, open a terminal and type;

sudo nano -w /path/to/file   or,
gksu gedit /path/to/file

---

### Post by sdowney717 on 2006-12-17
ok.
I did manage to login as root by changing the setting under login preferences to allow root login.
Then I edited files. However I am missing out on how to setup my modem. 
I just cant do it. I tried the martian. Put it in root directory on the desktop.
Run make all from the root directory, it starts compile and has many many errors.

I also tried to setup using instructions
DialupModemHowto/Lucent

[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

 but seem to be missing ARCH according to synaptic, I dont see ARC installed even though it is supposed to be installed by default. 

'(To check that the necessary package is installed, use your package manager, e.g. Synaptic or Adept. You need to look for a package, which is called linux-restricted-modules-ARCH, where ARCH is the last part of the $ uname -r output, i.e. your kernel flavor. If it is not installed yet, install it there.)'

Ok, I dont have, where do you get it??

The Ubuntu is a bought CD PC edition, not the DVD. Would the DVD have this and the CD not have it?
Where do you get this package linux-resticted-modules-ARCH ?


Dont you think it is still to 'geeky'. I have talked to a senior programmer and according to him, if I want to run linux I should use Fedora. 
How much stuff is available for Ubuntu as binary compiled and ready to install pacakges?
If I cant figure out how to compile, how many others are in the same position as me.

---

