---
title: "Howto: Getting your Broadcom 43xx wireless Card working in Hardy (step by step)"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by travislucas on 2008-05-30
Alright first things first, this is a how to for Ndiswrapper, and not for fwcutter. With that being said lets begin.

**1.) Getting ride of fwcutter.**
sudo aptitude remove b43-fwcutter

Alright now that we have fwcutter off the block lets work on getting Hardy ready for Ndiswrapper.

**2.) Ndiswrapper workaround for Hardy.**

sudo gedit /etc/init.d/wirelessfix.sh

and paste this:

Quote:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
into the file. Close and save it.

Next, run this:

Code:

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

and finally, this:

Code:

sudo update-rc.d wirelessfix.sh defaults

Now that we have that problem all worked out lets move on to figuring out which Broadcom card you have in your laptop!
[B]
3.) Getting the specs. on your Broadcom card![/B]

lspci | grep Broadcom\ Corporation (and) lspci -n | grep '14e4:43'


**4.) Now that you know what Broadcom wireless chip set your using go to this link and download the right drivers for you model! **[**The Link**]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") (Note: I would follow my Instructions on setting up Ndiswrapper and installing your driver. Just use this link to download the correct broadcom driver!)

**5.) Getting the Newest Ndiswrapepr ( I usually do everything in root, however if your not in root use sudo before "apt-get", going root in terminal just enter "sudo -i")**

apt-get update
apt-get install ndiswrapper-utils-1.9
apt-get install build-essential
apt-get install linux-headers-`uname -r`

Now you should have the latest Version of Ndiswrapper installed.

**6.) Removing bcm43xx **

rmmod bcm43xx
modprobe ndiswrapper

**7.) Now Extract your Broadcom wireless Driver**

unzip -a (your driver) example= "unzip -a sp33008.exe"

**8.) Now that your driver is extracted navigate to the directory your bcmwl5.inf file is and install it using these commands.**

ndiswrapper -i bcmwl5.inf
ndiswrapper -l
ndiswrapper -m
echo ndiswrapper >> /etc/modules

(note: there is no need to blacklist anything!)

Restart and enjoy using Wireless!!!

---

### Post by Ayuthia on 2008-05-31
> **travislucas said:**
> 
apt-get install build-essential
apt-get install linux-headers-`uname -r`
Just wanted to add a comment.  You don't really need to install build-essential and linux-headers-`uname -r`.  They are only needed if you are going to compile ndiswrapper.  This guide is using the repository package instead of the compiled version.

---

### Post by chimbba on 2008-07-21
Thanks for the tutorial. I got it working now.

---

### Post by Jeenyus on 2008-08-08
I get this message when I try to unzip...

root@ubuntu-3000:~# modprobe ndiswrapper
root@ubuntu-3000:~# unzip -a sp33008.exe
unzip:  cannot find or open sp33008.exe, sp33008.exe.zip or sp33008.exe.ZIP.
root@ubuntu-3000:~# ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

---

### Post by Ayuthia on 2008-08-08
> **Jeenyus said:**
> I get this message when I try to unzip...

root@ubuntu-3000:~# modprobe ndiswrapper
root@ubuntu-3000:~# unzip -a sp33008.exe
unzip:  cannot find or open sp33008.exe, sp33008.exe.zip or sp33008.exe.ZIP.
root@ubuntu-3000:~# ndiswrapper -i bcmwl5.inf
couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.

What travislucas was saying is that you will need to find the driver that works for your card.  If you have downloaded the sp33008.exe file, then you can extract the file with unzip or sometimes you might have to use cabextract. 

If you are not sure about what driver you will need, you can check out this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It has some good recommendations.

---

### Post by Jeenyus on 2008-08-09
> **Ayuthia said:**
> What travislucas was saying is that you will need to find the driver that works for your card.  If you have downloaded the sp33008.exe file, then you can extract the file with unzip or sometimes you might have to use cabextract. 

If you are not sure about what driver you will need, you can check out this link:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

It has some good recommendations.

I followed the guide to download the correct drivers (which was the sp33008.exe) but got that error when I reached that step in the guide.  However, after getting that error, I went a tried another guide I found on the forums, got a couple steps into that guide, got an error message, and just checked my wireless networks and the wireless just started working.  I have no idea why it is working, however it is so I think I'm just going to leave it alone for the time being.

---

### Post by georgefrankly on 2008-12-06
I unzipped the file to my desktop so the bcmwl5.inf is in my desktop directory.  In the terminal, I navigate to the desktop and run the line:

```
ndiswrapper -i bcmwl5.inf 
```

but get this response:
```
 couldn't create /etc/ndiswrapper/bcmwl5: Permission denied at /usr/sbin/ndiswrapper-1.9 line 194. 
```

can anyone tell me what went wrong and/or how to fix it? 

Thanks!

---

### Post by falcon61102 on 2008-12-06
You need to run ndiswrapper with the sudo command to get that working.  Try:
```
sudo ndiswrapper -i bcm15.inf
```

---

