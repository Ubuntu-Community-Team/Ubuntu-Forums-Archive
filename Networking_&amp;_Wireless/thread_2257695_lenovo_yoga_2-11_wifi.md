---
title: "lenovo yoga 2-11 wifi"
date: 2014-12-21
forum: Networking &amp; Wireless
---

### Post by trav9595 on 2014-12-21
This newer laptop will take a dual boot with Windows and Ubuntu but the wifi wont work in Ubuntu. I found this work around about blacklisting
some module and it apparently works. 
Here is some code that the poster offered..

A good workaround is to disable that module by blacklisting it. This worked for me with Ubuntu and Xubuntu. [This guy]("http://www.scrye.com/wordpress/nirik/2013/10/18/lenovo-yoga-2-pro-and-fedora-review/") seems to have done the same thing on fedora.
 
Make a new file for your personal blacklist
$ sudo nano /etc/modprobe.d/myownblacklist.conf and add an entry for the module
blacklist ideapad_laptop 
reboot and you are good to go!
 
 I see things like this all the time and it is NEVER made clear exactly how to do this....
Do you open a terminal and put the first line in..and then open another terminal and add the second line??? 
Why doesnt the second line have sudo in front of it?? 
please enlighten me exactly on how to do this step by step...thanks.

---

### Post by Hadaka on 2014-12-21
Hi an easy way is to COPY and paste this...
*Adds the module to a blacklist file <myownblacklist.conf
```
echo "blacklist ideapad_laptop" | sudo tee -a /etc/modprobe.d/myownblacklist.conf
```
*Deletes/removes the file
```
sudo sed -i '/ideapad_laptop/ d' /etc/modprobe.d/myownblacklist.conf
```

The sudo is needed to build the directory, useing your other method, and the second line...in the other method
is simply adding the module ideapad_laptop to the file in /etc.modprobe.d

the above method i gave you uses echo to add and sed to remove.
have fun.

---

### Post by Pilot6 on 2014-12-22
You do not need to blacklist ideapad_laptop.
The bug has been fixed in kernel 3.16.0-29.39.
It is already in proposed.

---

### Post by trav9595 on 2014-12-22
good news... so I should get this newer version of Ubuntu on USB before I install??? Will it be available before say January 15 2015??

---

### Post by Pilot6 on 2014-12-22
You do not need anything before install. You can install as it is and then install kernel debs.
If you can't access network, you can run

sudo modprobe -r ideapad_laptop

and then just update the system.

I think the 3.0.16-29.39 will be in official repos before Jan 15.

But you can download it now.

---

### Post by trav9595 on 2014-12-22
1-what is kernel debs and please say exactly what you do...

2-if someone cant access a network how can you get an update???

3-is downloading from repos a 1 clik thing like the Ubuntu site has???

---

### Post by Pilot6 on 2014-12-22
1. You can download kernel image as deb files.
2. I said how to get wifi temporarily working even with a 'bad' kernel.
3. It is not a 1 click thing.

<snip> you can wait till 14.04.2 is released in mid Feb.

---

### Post by trav9595 on 2014-12-23
sudo modprobe -r ideapad_laptop

and then just update the system.

this will temporarily allow wifi to bypass the rfkill thing?????
 
and in that same terminal box it will ask if I want to update and I say yes???

---

### Post by Pilot6 on 2014-12-23
This is in terminal, not where you are asked anything. <snip>

---

### Post by chili555 on 2014-12-23
> **trav9595 said:**
> sudo modprobe -r ideapad_laptop

and then just update the system.

this will temporarily allow wifi to bypass the rfkill thing?????
 
and in that same terminal box it will ask if I want to update and I say yes???Let's see if we can solve this thing. Please open a terminal with Ctrl+Alt+t and type in:```
sudo modprobe -r ideapad-laptop
```Press Enter.

Does your wireless come to life? If so, we will blacklist it and then work on an update.

---

### Post by trav9595 on 2014-12-23
I dont have the Yoga yet. 
Assume it comes to life....so what is the procedure to blacklist and update...???

sorry to bother you Pilot.....are you sure you want to be on a forum like this?????I think its about learning Linux..

---

### Post by chili555 on 2014-12-23
> **trav9595 said:**
> I dont have the Yoga yet. 
Assume it comes to life....so what is the procedure to blacklist and update...???

sorry to bother you Pilot.....are you sure you want to be on a forum like this?????I think its about learning Linux..If you unload the module as above and the wireless comes to life, the blacklist process is to open a terminal and type:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use kate or leafpad or nano if you haven't the text editor gedit. The text editor gedit will open up the file for editing.  There are many lines already present, but the end will look like this, approximately:```
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```You should add one more line:```
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist ideapad_laptop
```Proofread carefully, save and close the text editor.

You should be all set.

---

### Post by trav9595 on 2014-12-23
thanks  I'll be sure to be loud in the future.

---

