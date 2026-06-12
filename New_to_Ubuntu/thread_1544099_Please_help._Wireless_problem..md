---
title: "Please help. Wireless problem."
date: 2010-08-02
forum: New to Ubuntu
---

### Post by ariascarlos1990 on 2010-08-02
I can't for the life of me get the wireless to work on my Lenovo G530 444624u. I'm running Ubuntu 10.04 LTS Desktop. The card is a Broadcom BCM4312 802.11b/g. 

The card shows up in sudo lspci

I can't get internet through the Ethernet port either so Its not an option to download anything. I can transfer files from the computer i'm on right now to it via memory stick though to help get it working.

Any help would be greatly appreciated.

THANKS and have a nice day!

---

### Post by orethrius on 2010-08-02
It should be possible to address this solely from the system in question, unless firmware needs to be transferred.  Your first recourse is to do this:
```
lsmod | grep b43
```

If that returns nothing, try:
```
sudo modprobe b43
```

If you get an error inserting b43, we'll need to provide you another way to get that module.  If not, continue on:
```
ifconfig | grep wlan
```

Using the "wlanX" from above, where X is a number 0-9, we'll determine if your network is visible:
```
iwlist wlanX scanning
```

Then, from there, where NetworkName is your wireless name, and NetworkKey is... well...:
```
gksudo 'ifconfig wlanX down; sleep 2; iwconfig wlanX "NetworkName" key restricted "NetworkKey"; sleep 2; ifconfig wlanX up; sleep 2; dhclient wlanX'
```

Of course, that's sloppily coded, and only addresses WEP-based networks, but it's a starting point.

---

### Post by ariascarlos1990 on 2010-08-02
Ok I did the first command and this came up. What next? Nothing happened when I entered the command 
ifconfig | grep wlan 
[IMG]http://i125.photobucket.com/albums/p51/scooter_dude442/1280733481.png[/IMG]

---

### Post by jtarin on 2010-08-02
Then try the command ```
ifconfig -a
``` and post the results.

---

### Post by orethrius on 2010-08-02
Okay, simple enough, either the WLAN card isn't bound correctly, or it's using a different identifier.  Does anything show up as a response to **ifconfig**?

EDIT: Actually, ferb82 may have a point... can you connect to the Internet at all, from ANY system in your household?

---

### Post by ariascarlos1990 on 2010-08-02
> **jtarin said:**
> Then try the command ```
ifconfig -a
``` and post the results.

  [IMG]http://i125.photobucket.com/albums/p51/scooter_dude442/Screenshot-1-4.png[/IMG]

---

### Post by ariascarlos1990 on 2010-08-02
> **ferb82 said:**
> I think you should check your internet modem. I have the same problem and I found this solution.


Modem is good. I'm using another laptop perfectly fine on it.

---

### Post by jarviser on 2010-08-02
It's BROADCOM device.  Search on  here for "Broadcom" because Broadcom wifi card needs special drivers installed.

---

### Post by anewguy on 2010-08-02
There are a few ways to get your wireless working.  2 of the most common are:

(1) via a hard-wired connection to the access point, do a few simple commands

(2) if you have no way to hard-wire a connection to the access point you can use the Windows drivers for your adapter and 2 linux programs - ndiswrapper and its' gui'd front end ndisgtk (makes things simple).

Post back what you'd like to try and we'll go from there.  There are other options available, such as the firmware cutter, etc., but these 2 methods are the easiest to get things working.

Dave ;)

---

### Post by jtarin on 2010-08-02
Ok all your connections are visible. Do you have a hard-wired connection from your ethernet port to.......?

---

### Post by jarviser on 2010-08-02
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by ariascarlos1990 on 2010-08-02
> **anewguy said:**
> There are a few ways to get your wireless working.  2 of the most common are:

(1) via a hard-wired connection to the access point, do a few simple commands

(2) if you have no way to hard-wire a connection to the access point you can use the Windows drivers for your adapter and 2 linux programs - ndiswrapper and its' gui'd front end ndisgtk (makes things simple).

Post back what you'd like to try and we'll go from there.  There are other options available, such as the firmware cutter, etc., but these 2 methods are the easiest to get things working.

Dave ;)


I can't hook the computer directly to the modem its self but, I do have a Ethernet cord I could share internet connection through my other pc. I think that would be to difficult though so how about #2?

---

### Post by ariascarlos1990 on 2010-08-02
> **jtarin said:**
> Ok all your connections are visible. Do you have a hard-wired connection from your ethernet port to.......?

I don't 

> **jarviser said:**
> It's a Broadcom card - have you installed the driver yet?

I don't think so. This is a fresh install of ubuntu. So no??....

How do you do that?

---

### Post by orethrius on 2010-08-02
Okay, seems to be an awful lot of noise here, what do you get from:
```
iwlist wlan0 scanning
```

If your network shows up, we can go from there; if not, either there's a driver error, or simply a problem on the router's end.

---

### Post by ariascarlos1990 on 2010-08-02
> **orethrius said:**
> Okay, seems to be an awful lot of noise here, what do you get from:
```
iwlist wlan0 scanning
```If your network shows up, we can go from there; if not, either there's a driver error, or simply a problem on the router's end.

It says "Failed to read scan data: Network is down"

---

### Post by orethrius on 2010-08-02
> **ariascarlos1990 said:**
> It says "Failed to read scan data: Network is down"

Same thing if you try **sudo ifconfig wlan0 up** first?

---

### Post by jarviser on 2010-08-02
> **orethrius said:**
> Okay, seems to be an awful lot of noise here, ...

If you want the forum to yourself old chap, pray continue.

---

### Post by ariascarlos1990 on 2010-08-02
> **orethrius said:**
> Same thing if you try **sudo ifconfig wlan0 up** first?


I appreciate everybody's help! 

I figured it out.

I this little tut and it works like a charm.

**b43 - No Internet access**

 If you do not have any other means of internet access on your computer, you will have to install b43-fwcutter and setup manually (without the firmware automatically downloading and being set up). 
b43-fwcutter is located on the Ubuntu install cd under **../pool/main/b/b43-fwcutter/** or in the official repositories online.  
Double  click on the package to install or in a terminal navigate to the folder  containing the package and issue the following command:  
:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter***Step 1.** 
On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) 
**Step 2.**  
Copy  the downloaded files to your home folder and execute the following  commands consecutively in a terminal to extract and install the  firmware: 

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o**Note:** A computer restart may be required before using the wifi card. 

Again thanks everybody for you help I really appreciated it!

---

### Post by orethrius on 2010-08-02
> **jarviser said:**
> If you want the forum to yourself old chap, pray continue.

I'm sorry, do I know you?  Being as I don't, I find it difficult to interpret your meaning here.  It's moot anyways, as Carlos discovered the right course of action by simply following his instincts.  This does nothing to change the fact that fwcutter is the rare exception where software can directly affect issues with the firmware.  Switching network managers isn't helpful at best, and detrimental at the very worst.  Perhaps we should focus more on encouraging user experimentation, than on pulling them in opposing directions.

EDIT: Additionally, I find it incredibly frustrating when people decide to "call me out" when I comment on the level of noise.  When people make posts that demonstrate that they either didn't read or didn't understand the OP's first post, that is - *by definition* - noise.  If *you* meant to do so, then perhaps *you* would like the forum to yourself.  If this is not what you meant, then it would seem that I'm now overreacting.  The ball is entirely in your court. ;)

---

### Post by anewguy on 2010-08-03
I think what you would find is that if you stop being vocal about how good YOU are (Okay, seems to be an awful lot of noise here) you may find people much more receptive to your WELCOMED attempts to help.  If you had just simply omitted that, and instead said "I'm not sure if it will help or not, but let's try this...." you wouldn't have gotten flamed.  Being a little self-depricating can be a + on this forum when you are dealing with beginners or people like me - more experience, but still have plenty of questions about areas I'm not familiar with.

I agree that sometimes people reply on threads with useless information, but you know they are only trying to help and learn themselves.  I tend to give most people a lot of slack in that area.

Obviously any attempts at help are welcomed - just please be aware of your tone.

---

### Post by anewguy on 2010-08-04
> **orethrius said:**
> I'm sorry, do I know you?  Being as I don't, I find it difficult to interpret your meaning here.  It's moot anyways, as Carlos discovered the right course of action by simply following his instincts.  This does nothing to change the fact that fwcutter is the rare exception where software can directly affect issues with the firmware.  Switching network managers isn't helpful at best, and detrimental at the very worst.  Perhaps we should focus more on encouraging user experimentation, than on pulling them in opposing directions.

EDIT: Additionally, I find it incredibly frustrating when people decide to "call me out" when I comment on the level of noise.  When people make posts that demonstrate that they either didn't read or didn't understand the OP's first post, that is - *by definition* - noise.  If *you* meant to do so, then perhaps *you* would like the forum to yourself.  If this is not what you meant, then it would seem that I'm now overreacting.  The ball is entirely in your court. ;)

Let's see - Broadcom wireless that the user never installed a driver for, and looking for help on getting the wireless going.  First post seems pretty obvious to me and many others.  The solutions I would have had the OP do if they had not solved this themselves would have installed the driver and gotten the wi-fi working.  So, perhaps YOU need to read what people are writing.

Here's the deal pal - other people have been solving Broadcom "problems" for years.  You come in here, act like you're God, when in fact your advice didn't do any good.  Did the OP find the answer him/herself?  Yes.  Could the rest of us have solved this without your help?  You better believe it.

Quit with the attitude - you're simply not that good.

---

