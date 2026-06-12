---
title: "help with failed mount in pyneighborhood"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by gjbnh1701 on 2007-04-26
I love feisty! But 'm having a problem with pyneighborhood. I can see the windows shares on my network, but when I try to browse them, I receive an error "failed to mount." I am kinda at a loss; can someone help me. I googled this and found only one post on this, and wasn't sure how ld it was, and couldn't do it anyways; there is no general tab in my preferences. Thanks!

---

### Post by gjbnh1701 on 2007-04-29
Problem solved! Going to the a root terminal resulted in providing me with more info, which I then "googled" Apparently pyNeigherborhood needs midnight commander (mc) installed. Apparently the default install of feisty does not install this. After installing it I can now see, and browse my smb shares without problem.  I share this in case anyone else is having this problem.

---

### Post by Spam Banjo on 2007-07-19
Can I just give you a pat on the back sir?!?

Recently I have been getting proper frustrated at people in forums... with less than 10 posts next to their name, asking questions, then posting the very next post, about 10 mins later, saying... "Problem Solved".

Most of them can't be bothered to share the solution.
Which is why I offer my thanks!!!

You are a role model for other forum users!!! lmao!

---

### Post by jjj_uk on 2008-02-07
Just had this problem in hardy and mc solved it for me too. Thanks!

---

### Post by toomuchcomputertime on 2008-02-14
Same problem, thank you.

---

### Post by chris2028 on 2008-02-23
Install -----------------
midnight commander - a powerful file manager
[http://packages.ubuntu.com/feisty/utils/mc](http://packages.ubuntu.com/feisty/utils/mc)
depend on your system 64bit / 32bit ........




if you scan host fail !!!
check preference------
check and make sure un-click on always use anonymous logins (if your windows share request password, is likely error here)

if still not able to mount
The problem is that regular users do not have permission to mount shares. 
From the command line run 

gksudo pyNeighborhood


and for people who use language other the English
please put the following under preference  tab CIFS in Options:
OTPIONS&#65306; codepage=cp866,iocharset=utf8

There are a few preliminary actions we need to take before we can start mounting using cifs.
Although cifs installs right alongside smbfs, smbfs is not installed by default. So, if you have smbfs already installed, you also already have cifs installed. But if you have not installed smbfs, you will need to do so now.

sudo aptitude install smbfs


sudo aptitude install winbind


If you can mount the network drive with SMB but not CIFS
you may have problems with windows share on a DHCP network which is likely thenetbios name
Edit your nsswitch file
sudo nano /etc/nsswitch.conf

find the 
hosts: files dns

and replace it with
hosts: files wins dns




other reference page
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

ALL THE BEST --------------- SHARE inside UBUNTU.

---

### Post by ergosteur on 2008-05-21
Thanks, never would have thought of that.

I also had to change the default mount folder to /home/myUSERNAME/SOMEPATH for the mounting to work as a regular user.

Using Hardy.

---

### Post by das280zx on 2008-05-31
I can't get this to work at all.  I have tried all of the above.  In searching around I have found references to a file, smbmnt, which i apparently do not have on my system.  It is supposed to be in /usr/bin but it is not there.  I can't find it anywhere.  I have smbmount, but apparently it needs smbmnt to work, and I don't have it, how can this be?

---

### Post by ergosteur on 2008-06-02
> **das280zx said:**
> I can't get this to work at all.  I have tried all of the above.  In searching around I have found references to a file, smbmnt, which i apparently do not have on my system.  It is supposed to be in /usr/bin but it is not there.  I can't find it anywhere.  I have smbmount, but apparently it needs smbmnt to work, and I don't have it, how can this be?

do you have smbfs installed?

never mind, this was said above.

---

