---
title: "installing b43-fwcutter"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by freewheelinguy on 2009-01-02
My present problem is I can't detect my wireless card. What I have gathered from the forums help is to download fwcutter which is used to extract from the driver.  I have it in a folder on the desktop and now I want to install it. First I need to know how to install fwcutter.  I also have the driver .sys file on the desktop.
I'm working in the terminal window and would like to know how to install fwcutter and then extract what I need from the licensed driver (bcmwl5.sys).  According to the tutorial I should type:  sudo aptitude install bcm43xx-fwcutter.  This gives me several lines of info, but in the center of this info it states: can't find any package....."bcm43-fwcutter".  I guess aptitude isn't looking for the file on my desktop, so I need to know how it will detect it.  The tutorial says once I get this I should probably move it to /lib/firmware.  I typed dir and see the various dir including lib but don't know how to access.  

This is what I need. 
1. How to install fwcutter.
2. Extract what I need.
3. Where or how to move it to where it is suppose to reside.

Hopefully these questions are making sense and someone can show me where I'm going wrong.

Len

---

### Post by Moop on 2009-01-02
It can't find the file because you need to change directories to your desktop. In the teminal type ```
cd Desktop
``` Make sure you use "Desktop" and not "desktop" Then you should be able to run your command. 

Then you can run gksudo nautilus and navigate to the lib/firmware directory and drag your file into it.

---

### Post by wolfen69 on 2009-01-02
no need to extract anything or go into directories.

go to system>administration>software sources and check off all the repos. also go to the tab marked "third party" and check off the partner repo. close window and reload when asked.

then go to synaptic package manager and search for bcm43-fwcutter. it should show up now. install.

---

### Post by freewheelinguy on 2009-01-02
neither of these worked.

Moop - at freewheelinguy@ubuntu: /$ cd Desktop
came back with
bash: cd: Desktop: No such file or dir.

Wolfen69 - when I hit reload received error message:
The info about avail. sw is out of date.
To install sw and updates from newly added or changed sources, you have to reload the info about available sw.
You need a working internet connection to con't.

Len

---

### Post by Kevbert on 2009-01-02
If you have a Broadcom wireless adapter, take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13"), it includes the firmware you need.

---

### Post by freewheelinguy on 2009-01-02
That worked.  I did it a little differently though.  I put the zip file on the desktop. Set terminal to Desktop prompt and moved drivers to  /lib... dir.  Not sure why cd ~/firmware wouldn't work.

I also tried to drag and drop using GUI file manager, but wouldn't let me (files on Desktop - into home directory.

At least I learned a little about using the terminal and moving through directories.  Every little bit helps.  I've been trying for three days now trying to connect to internet.  This was great.  Still don't understand how this worked using the complete driver.  Thought we could only extract what we needed.  That's why I was trying to use fwcutter.  Thanks for your help.  It is greatly appreciated and also to the other two (wolfen69, moop) who have responded to my request.

---

### Post by andrew.46 on 2009-01-02
Hi freewheelinguy,

The package name you tried is not quite right:

```
andrew@skamandros:~$ apt-cache search fwcutter | grep b43
b43-fwcutter - Utility for extracting Broadcom 43xx firmware

```

And if you go this road you will find a nice script installed as well that will download and install the appropriate firmware for your Broadcom:

```
$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware
```

This is the method I use on my own bcm card and it works perfectly. My chip is:

```
andrew@skamandros:~$ lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

```

All the best,

 Andrew

---

### Post by azmike on 2009-04-02
Thank You so much, this is what worked for me after trying many other suggested solutions.

---

### Post by aeproberts on 2009-08-06
Hi, Please help. 

Getting UBUNTU to recognize this card is killing me. 

I follow the instructions above and am fine until I get to the command below. 

$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware

then I get this error

sudo: /usr/share/b43-fwcutter/install_bcm43xx_firmware: command not found

What am I doing wrong? I just need UBUNTU to recognize my wireless card.

---

