---
title: "[SOLVED] Plz help wireless recognized, but no connect"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by WFGeppetto on 2008-02-06
I've been trying to get my wireless working for a few days now.  I am a new linux user, and have been using Ubuntu on dualboot w/vista (thanx to wubi installer) I have 15G for ubuntu, 1.5G ram, Gateway Turion64X2 TL-50
Broadcom dell 1390

mkay, now then, it took me forever to simply get my wireless networks to show up.  Finally, after making a mistake trying to change my network manager, and killing it, and losing all internet connectivity, I reinstalled and followed the directions here:

[http://ubuntuforums.org/showthread.php?t=427498](http://ubuntuforums.org/showthread.php?t=427498)

to simplify, I'll repost the directions:

1. download the windows-driver from dell.

2. install ndiswrapper

Code:

sudo apt-get install ndiswrapper-utils-1.9

3. unload bcm43xx
Code:

sudo modprobe -r bcm43xx

4. install unzip and - only if you want to identifiy the firmware-version - bcm43xx-fwcutter

5. go to the download directory and run
Code:

unzip R151517.EXE

6. go to the created subdirectory "DRIVER"
Code:

cd DRIVER

7. if you want to identify the firmware version run (not really neccessary)
Code:

bcm43xx-fwcutter -i bcmwl564.sys

the output should be
Code:

filename   :  bcmwl564.sys
  version    :  4.100.15.5

8. install the driver with
Code:

sudo ndiswrapper -i bcmwl5.inf

9. load the ndiswrapper module
Code:

sudo modprobe ndiswrapper

10. blacklist the bcm43xx
Code:

sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist

11. make the ndiswrapper load at boot time
Code:

sudo echo ndiswrapper >> /etc/modules

now you should see your wireless network by typing
Code:

iwlist eth1 scan

____________________________________________________
so, that's what I did, up to number 10... i

lines 10 and 11 when code entered return:
bash: /etc/modprobe.d/blacklist: Permission denied

So I think that means that I cannot make it boot the program? something like that.

Anyway, after all this, finally, I can see the available networks, but I cannot log onto one.  Considering the problems I've read of concerning wpa (which I had set up on my router), I reset my router, and am currently running unprotected, with no encryption at all, but I still cannot connect.  I am using ethernet.  Were this my desktop, I'd just go hardwired, but it's my laptop, and I want the wireless freedom, and besides, I'd like to learn WTF I'm doing.

help plz.

---

### Post by Andrew Stone on 2008-02-06
Did you remember the "sudo"?  You don't have permissions to modify the file.
Do:
ls -l /etc/modprobe.d/blacklist

to check permissions.  Also, you can use "sudo -i" to get to an "interactive" sudo session, so you don't have to keep sudo-ing.  BTW, this probably is not why you cannot connect to the wireless network.

Did you try clicking on the network icon on the panel, looking at your wireless connection, and selecting "roaming" mode?

---

### Post by WFGeppetto on 2008-02-06
Thanks!!!  Actually, I looked up in the sticky, and followed the directions for the 3rd or 4th time.

I must have had the case wrong on a line, or indeed missed sudo somewhere.

I am connected!  Yay!  wireless!  Now...

It's not encrypted, and I'd like it to be, also, i still can't get any of the blacklist functions to work, and I run across "permission denied" a few times, so (while I don't know what I am saying:) I suppose my ndiswrapper won't 'stick'?  

rrr, I'll keep reading stickies, but I don't understand the "permission denied" stuff.  I have yet to reboot, so I don't know if it will stick or not.  I suppose I should, I can reconnect w/ ether...

any suggestions? oh, and btw, I noticed the "thanked" thing...how do I thank?

---

### Post by WFGeppetto on 2008-02-06
k, I tired your permissions thing:

wfgeppetto@ubuntu:~$ ls -l /etc/modprobe.d/blacklist
-rw-r--r-- 1 root root 840 2007-04-03 09:03 /etc/modprobe.d/blacklist
wfgeppetto@ubuntu:~$ sudo echo ndiswrapper >> /etc/modules
bash: /etc/modules: Permission denied
wfgeppetto@ubuntu:~$ 


so, that didn't seem to work.

Thanks, and I'll try to keep from booting, until I think I have it nailed down...

edit:  I went here:  [http://ubuntuforums.org/showthread.php?t=689179&highlight=permission](http://ubuntuforums.org/showthread.php?t=689179&highlight=permission)

and so, I did this:

wfgeppetto@ubuntu:~$ ls -l /etc/modprobe.d/blacklist
-rw-r--r-- 1 root root 840 2007-04-03 09:03 /etc/modprobe.d/blacklist
wfgeppetto@ubuntu:~$ sudo chmod a+wx /etc/modprobe.d/blacklist #
Password:
wfgeppetto@ubuntu:~$ sudo chmod a+wx /etc/modules #
wfgeppetto@ubuntu:~$ sudo echo blacklist >> /etc/modprobe.d/blacklist
wfgeppetto@ubuntu:~$ sudo echo ndiswrapper >> /etc/modules
wfgeppetto@ubuntu:~$ 


looks like it worked.  Now only to worry about encryption I suppose.

this is a bit scary, screwing with permissions, when I don't know what I'm doing, but it's fun getting my code legs back...hope I don't screw up.

---

### Post by WFGeppetto on 2008-02-06
well, crap.

I just rebooted, and all of my efforts apear to be undone.  My wireless doesn't recognize any networks (but there are 5 in my neighborhood).  I can reinstall the driver, and redo all the ndiswrapper crap, and then redo the manual configuration to get back onto my unsecured network, but I don't know how to make it all stay!

Until I figure this out, I'll have to do all that crap just to get wireless.  Why can't I make any of it stay after a boot?

---

### Post by Andrew Stone on 2008-02-07
> -rw-r--r-- 1 root root 840 2007-04-03 09:03 /etc/modprobe.d/blacklist

Its strange that the sudo echo... line did not work because blacklist is marked as having write permissions for "root".

You know, what those sudo echo... lines do is append the line to the file.  That is, 
sudo echo ndiswrapper >> /etc/modules

appends the word "ndiswrapper" to the end of the file /etc/modules, which is the file that tells Linux what drivers to load. 

The point of these 2 lines is to 
1. add ndiswrapper into the list of drivers to load on bootup.
2. remove bcm43xx from the list of drivers to load (because you are using ndiswrapper and the windows driver)

I noticed in the cut and paste that you did not do it right.  You did:
sudo echo blacklist >> /etc/modprobe.d/blacklist

You were supposed to do:
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist

Now you probably have the word "blacklist" at the end of the blacklist file.  Not sure what that will do, so you're going to have to load that file up in a text editor and fix that.
"sudo gedit /etc/modules"

While you are at it, you might as well load up /etc/modules and make sure it looks good too.

For example, my file looks like this.  Don't put all of my drivers in your file though, since obviously my drivers are specific to my system.  If you get stuck. "cat" these two files and paste them in a message.

$ cat /etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper


# Generated by sensors-detect on Tue Jan 29 11:39:33 2008
# Chip drivers
w83627ehf
coretemp


To thank, use the little golden star on the bottom right next to "Quote".

---

### Post by WFGeppetto on 2008-03-08
Wow, that was helpful, but Ironically, I have a pretty good reason for not coming back to this until now.

Sorry, btw, I should have followed up sooner, so that the thread didn't stay open ended.

I crashed it messing with all that, and it was a wubi install anyway, no partitioned.  When I crashed my ubuntu, I fresh installed my entire system after backing up windows.  Instead of using wubi, after the reinstall, I got a Gutsy 7.10 live disk, and did a proper dual boot install.

Gutsy has all this crap in place already, and I like it much better.

Thank you very much Andrew.  I appreciate your taking the time, and I'm sorry I didn't reply earlier.  I hope you didn't follow up too much and get frustrated, I won't abandon my own thread again.

---

