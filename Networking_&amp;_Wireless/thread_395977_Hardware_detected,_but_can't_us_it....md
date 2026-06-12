---
title: "Hardware detected, but can't us it..."
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by Lost_Soldier on 2007-03-28
I am kinda new to ubuntu and would appreciate some help with my problem.

I have a Linksys wireless-g speedbooster USB device (wusbg sv2 on bottom of adapter).
I have ndiswrapper v1.18 and ndisgtk

I successfully installed the drivers and checked "ndiswrapper -l" in the terminal and got

Installed drivers:
wusb54gsv2              driver installed, hardware present 

And ndisgtk claims that it is installed correctly as well. I then downloaded Wicd, but it can't detect my adapter and obviously can't use it. If you require any other information, then ask and I will do my best to supply an answer.

"iwconfig" reveals:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

If it matters, I am able to connect through a wired connection on a netgear ethernet card. (Would have to tear open case to look at model, if you need it, then just ask). My wireless adapter lights (Power, Link) remain off and flash briefly when I plug it back in.

What am I doing wrong? This will be my last attempt at this for a while or possibly forever and I will have to turn back to Windows XP. If anyone can help, then please do. 

After this falls off the front page and no solution is found, I will disappear back into the hell that is Windows XP.

---

### Post by Lost_Soldier on 2007-03-28
This will be my only "bump" for this thread. I am going to switch to my XP partition for the time being. I will continue to watch this thread till it slides off the front page. After it slips off the front, I format the Ubuntu partition and wave Linux a possibly permanent goodbye. :(

---

### Post by Floppyjoe on 2007-03-28
I found this on the ndiswrapper-list site at sourceforge.net:
> Card: Linksys #[WUSB54GSv2], 802.11b/g, USB 2.0 -- [link here|List#WUSB54GSV2]

    * Chipset: Broadcom - BCM4320SKFBG
    * usbid: 13b1:0014
    * Driver: You can install this driver by either of the following two methods.
          o Method1: The driver for this RNDIS card doesn't include two .sys files required (usb8023k.sys and rndismpk.sys or usb8023x.sys and rndismpx.sys), as they are part of Windows installation and don't need to be installed in Windows. However, other drivers for different cards based on RNDIS include these .sys files. One is Belkin F5D7051uk at [181]. You can install this driver with BCMRNDIS.INF, then, copy sys files with 'cp USB8023K.sys /etc/ndiswrapper/bcmrndis/usb8023k.sys; cp RNDISMPK.SYS /etc/ndiswrapper/bcmrndis/rndismpk.sys'. You then need to inform ndiswrapper that this driver, bcmrndis, should be used for usbid of WUSB54GSv2 (13b1:0014), by executing 'ndiswrapper -d 13b1:0014 bcmrndis'
          o Method2: Used the inf file from the CD, and the .SYS files from usr5420 available at [www.usr.com](www.usr.com) [182]. Used snapshot from 13/02/2006, along with the usr system files that i had to install on a windows machine to extract. Then copied the wusb54gs.inf and wusb54gsv2.inf to the folder with the sys files - the wusb54gs.inf worked seamlessly with my device on the snapshot.! 
    * With 2.6.16 kernels and later, you also need to configure udev; see entry for USR5421 below for details. 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L)

---

### Post by Mr. C. on 2007-03-29
> **Lost_Soldier said:**
> This will be my only "bump" for this thread. I am going to switch to my XP partition for the time being. I will continue to watch this thread till it slides off the front page. After it slips off the front, I format the Ubuntu partition and wave Linux a possibly permanent goodbye. :(

Your presence will be sorely missed.

---

### Post by JengaBlocks on 2007-03-29
Linux is a learning experience and trying to figure stuff out yourself is part of the process. If you aren't willing to put in the time and energy, then you will ultimately fail. Whether it is school,  your job, your family - it all applies and its called one thing:

P-E-R-S-E-V-E-R-E-N-C-E

Challenge and frustration is part of learning Linux! If not, go back to Windows!

Did Thomas Edison whine and complain while he was inventing the light bulb? Did Linus Torvalds threaten to walk out if he didn't get Linux to work?  Does your auto mechanic pout and bolt his job if he can't fix your brakes?

If you want help, then ask for it. But stop the silly spoiled child act because its not going to get you any sympathy here.

---

### Post by Lost_Soldier on 2007-03-29
To: JengaBlocks
Do not assume that I haven't tried, I have spent the better part of two weeks trying to figure this out. I could not have gotten this far without "Trying". And I didn't come here for sympathy, I came here for help in a problem, not to be insulted by some jackass.

To Floppyjoe:
I thank you for your advice, but I have tried both of those methods. Method 1 and another tutorial got me as far as I am now. The only solution I can come up with is trying to find a newer version of Ndiswrapper and trying again. (1.39 is the newest I think). I have tried the package located on their site, but compiling the file is quite a pain and fails everytime. I think a debian package might be out there (My updater on Ubuntu didn't seem to catch it), if anyone does by chance have the link, please share it.

---

### Post by Lost_Soldier on 2007-03-29
Well, I found Ndiswrapper 1.40 and managed to install it, my new info is the same, I went a head and ran "lsusb" and got:

Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 13b1:0014 Linksys 
Bus 002 Device 001: ID 0000:0000  

I have no idea what to do and can't find a tutorial that matches this problem at all :(

---

### Post by Mr. C. on 2007-03-29
And herein lies the problem using threats and insults.  Help just isn't going to be forthcoming.

MrC

---

### Post by Lost_Soldier on 2007-03-29
> **Mr. C. said:**
> And herein lies the problem using threats and insults.  Help just isn't going to be forthcoming.

MrC

I do not mean to be hostile, I just don't like being insulted.

---

### Post by Mr. C. on 2007-03-29
If you come in threatening, be prepared for negative feedback.  You came in threatening.  Threats are hostile.

Nobody here owes you anything; and we do this to help others, in our own spare time.  If the response pace is not fast enough for you, then you perhaps might be more suited for another environment.

MrC

---

### Post by Lost_Soldier on 2007-03-29
> **Mr. C. said:**
> If you come in threatening, be prepared for negative feedback.  You came in threatening.  Threats are hostile.

Nobody here owes you anything; and we do this to help others, in our own spare time.  If the response pace is not fast enough for you, then you perhaps might be more suited for another environment.

MrC

I never claimed you or anyone else owed me anything. I basically said, "I am about to give up, I can't seem to solve the problem, maybe you can" I didn't come out and say "I demand that you help me or else i will shoot your dog" or something like that

---

### Post by handaxe on 2007-03-30
Hi,

Lets move to constructive mode pleeease...

Not that I can necessarily help but we can try to generate relevant info. Post the outputs of ```
dmesg | grep ndis 
```(this will check the ndis loading)

```
sudo iwconfig
```

```
sudo ifconfig
```

HA

---

