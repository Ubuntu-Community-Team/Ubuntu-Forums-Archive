---
title: "How to install wusb54g v1?"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by Senojelyk on 2007-03-29
Okay, so i got ubuntu installed on my old computer (windows xp on this one still) its the Intel x86 edition. I really have no clue what im doing, but i need to get internet access and i can figure the rest out from there. In order to do that i need to install the adapter, and i have no idea how to do that. The pinned guide is for dapper drake?, i have no idea what that is, and mine isnt v4. I dont really know where to get the driver or what not for it. any ideas??  

Thanks a ton,
Kyle Jones

---

### Post by Floppyjoe on 2007-03-29
> **Senojelyk said:**
> Okay, so i got ubuntu installed on my old computer (windows xp on this one still) its the Intel x86 edition. I really have no clue what im doing, but i need to get internet access and i can figure the rest out from there. In order to do that i need to install the adapter, and i have no idea how to do that. The pinned guide is for dapper drake?, i have no idea what that is, and mine isnt v4. I dont really know where to get the driver or what not for it. any ideas??  

Thanks a ton,
Kyle Jones

This is from the ndiswrapper site:
> Card: Linksys #[WUSB54Gv1], 802.11b/g, USB 2.0 -- [link here|List#WUSB54G]

    * Chipset: Prism54
    * usbid: 5041:2234
    * Driver: Linksys Windows XP driver [174]
    * Other: Works smoothly, of course ;) - this is the device the USB extension was originally developed for. WEP is running, WPA is supported using wpa_supplicant 0.2.5. No problems with both 1.1 and 2.0 host controllers. As with many other USB devices, no success with 2.4 kernels so far. Try to use 2.6.7 or better. There is a native driver for Prism54 that is working on USB support. View its status at Prism54.org
    * Other: Works with latest Windows Driver from linksys.com. No success with 2.4 kernels (even with 8k stack). Works with kernel 2.6.11 and 2.6.12. Works smoothly with 2.6.12 and ndiswrapper 1.14.
    * Other: Driver from Linksys is old. Alternate driver for Sitecom WL-125 driver at [175] is newer version. With this, the card doesn't disconnect. Tested with card with usbid 1915:2234. 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#L)

---

### Post by Senojelyk on 2007-03-29
how exactly does ndiswrapper work? ive seen it around on here but i dont know what it is really..

---

### Post by Floppyjoe on 2007-03-29
> **Senojelyk said:**
> how exactly does ndiswrapper work? ive seen it around on here but i dont know what it is really..
For me it's like my car. I don't know exactly how everything works but I can still use it even if I don't know that.
It has something to do with wrapping something around the windows drivers to make them work in Linux.

There also was a suggestion of a native driver on that site.

---

### Post by Senojelyk on 2007-03-29
lol, interesting analogy, but i got it downloaded along with the windows driver, so i'll put it on my linux and see what happens. 

thanks

---

### Post by Senojelyk on 2007-03-29
Okay, i extracted ndiswrapper on my desktop, now how do i install the windows driver with it?

---

### Post by Floppyjoe on 2007-03-29
> **Senojelyk said:**
> Okay, i extracted ndiswrapper on my desktop, now how do i install the windows driver with it?
Probably the easiest way to install ndiswrapper on your computer is to click on System/Administration/Synaptic Package Manager.
Then click on Edit/Add Cdrom. Then follow the directions using your Ubuntu install Disk.
Then click reload.
Then search for ndiswrapper-utils-1.8 and ndiswrapper-common and install these two files.
Then you need to move your windows drivers to your home folder.
Then open a terminal and enter:
```
sudo ndiswrapper -i drivername.inf
```
Where drivername.inf is replaced with the actual driverfilename.inf.
Then check to see if it worked and your hardware is recognized.
```
ndiswrapper -l
```
If all is okay and the driver and hardware are present then:
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```
```
sudo ndiswrapper -m
```
```
sudo gedit /etc/modules
```
add the word ndiswrapper and save and exit this file.

---

### Post by Senojelyk on 2007-03-30
I added the cd rom, hit reload then did the search and it didnt come up with any files. I have my extracted ndiswrapper folder in my home folder as well as the windows driver. Any idea what im doing wrong?

---

### Post by Floppyjoe on 2007-03-30
> **Senojelyk said:**
> I added the cd rom, hit reload then did the search and it didnt come up with any files. I have my extracted ndiswrapper folder in my home folder as well as the windows driver. Any idea what im doing wrong?
Try just searching for the word ndiswrapper

---

### Post by Senojelyk on 2007-03-30
Nothing. Is there a specific place i was supposed to extract the ndis folder to?

---

### Post by Floppyjoe on 2007-03-30
If you downloaded the ndiswrapper file from sourceforge.net you will need to install build-essential and linux-headers-`uname -r` otherwise you won't be able to install it.

Unfortunately if you can't find them on your Ubuntu Install Disk then you won't be able to install them unless you have internet access another way on the computer in question.

---

### Post by Senojelyk on 2007-03-30
Okay, how would i go about installing those? And i dont have internet access on the linux PC at the moment, only on my windows one right now, but i have a cd-rw if that helps? 

thanks for all the help :)

---

### Post by Floppyjoe on 2007-03-30
> **Senojelyk said:**
> Okay, how would i go about installing those? And i dont have internet access on the linux PC at the moment, only on my windows one right now, but i have a cd-rw if that helps? 

thanks for all the help :)
I suggest the same method as for the other files mentioned above. If that doesn't work then you are probably out of luck. It would take forever to hunt down dependencies for those files some other way so I don't want to go there.

---

### Post by Senojelyk on 2007-03-30
Okay those are both installed successfully, still nothing is showing up when i search ndiswrapper.

---

### Post by Floppyjoe on 2007-03-30
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)
This is a guide for installing ndiswrapper

---

### Post by Senojelyk on 2007-03-30
Okay i'll do that and i suppose if i cant get it, i'll hit amazon and find a Linux ready wireless device. One quick question for you tho, when i try to log in as root from the main login page, it just clears out the entry and goes back to user name, i fixed the password, or so i thought. Any idea why its doin this?

Thanks a million :)

---

### Post by Floppyjoe on 2007-03-30
I'm not sure but it is probably a security thing. It is probably not wise to login as root and do stuff you would normally do as another user.
The root login in my tutorial is in the Terminal and not the main login page.

---

### Post by Senojelyk on 2007-03-30
Still not working for me, not sure why. Probably something im doing, but you know of any wireless adapters that are fairly easy to install on ubuntu? Easy for somebody new to this, like me. Even if its internal, it'll help. thanks again!

---

### Post by Floppyjoe on 2007-03-30
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by archaggie828 on 2007-05-17
sorry, more questions from inexperienced users . . .

i was following the instructions posted here, and when i got to: sudo modprobe ndiswrapper
i got an error message:

tiffany@trslinuxbox:~$ sudo modprobe ndiswrapper
Password:
FATAL: Module ndiswrapper not found.

 . . . and now i'm suck. what do i do from here???

does it have something to do with the fact that it doesn't show hardware present??

tiffany@trslinuxbox:~$ ndiswrapper -l 
wlanuig : driver installed 

i have spent weeks trying to use ndiswrapper to make my wifi work, with no luck so far.  i've installed in the terminal and using the synaptic package manager.  i don't think either works right. one, the driver doesn't show up as installed in the gui, but when i try to install it again an error message tells me that it's already installed. two, i have no option for a wireless connection in my network settings. and, my device manager has the usb hardware listed as unknown.  

currently i am running feisty ubuntu 7.04 kernel 2.6.20-15-generic for x86_64 and my wireless device is the linksys wusb54g (i think v1) lsusb shows 1915:2234

please help!!! i just want my wifi to work . . . 

- thanks -

---

### Post by GrantShoe on 2007-05-17
> **archaggie828 said:**
> sorry, more questions from inexperienced users . . .

i was following the instructions posted here, and when i got to: sudo modprobe ndiswrapper
i got an error message:

tiffany@trslinuxbox:~$ sudo modprobe ndiswrapper
Password:
FATAL: Module ndiswrapper not found.

 . . . and now i'm suck. what do i do from here???

does it have something to do with the fact that it doesn't show hardware present??

tiffany@trslinuxbox:~$ ndiswrapper -l 
wlanuig : driver installed 

i have spent weeks trying to use ndiswrapper to make my wifi work, with no luck so far.  i've installed in the terminal and using the synaptic package manager.  i don't think either works right. one, the driver doesn't show up as installed in the gui, but when i try to install it again an error message tells me that it's already installed. two, i have no option for a wireless connection in my network settings. and, my device manager has the usb hardware listed as unknown.  

currently i am running feisty ubuntu 7.04 kernel 2.6.20-15-generic for x86_64 and my wireless device is the linksys wusb54g (i think v1) lsusb shows 1915:2234

please help!!! i just want my wifi to work . . . 

- thanks -

I'm in the exact same situation.  Unfortunately, i became used to linux at school and now that i'm home and i need wireless to work in my house, i have to abandon linux and i'm back to my xp laptop because of this error.

I ran everything according to 
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21)
and
[http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)
yet i'm on Feisty
but i keep on getting that FATAL error when i'm modprobing (i have no idea what modprobe is) and i've researched and researched but it seems as though a lot of people don't know what to do with this error.  
[http://groups.google.com/group/alt.os.linux.mandriva/browse_thread/thread/cff7bcfe561fa797/4fecdfbfa0fd7a6a?lnk=st&q=%22Module+ndiswrapper+not+found.%22&rnum=4&hl=en#4fecdfbfa0fd7a6a](http://groups.google.com/group/alt.os.linux.mandriva/browse_thread/thread/cff7bcfe561fa797/4fecdfbfa0fd7a6a?lnk=st&q=%22Module+ndiswrapper+not+found.%22&rnum=4&hl=en#4fecdfbfa0fd7a6a)
that is the closest i could get to a fix but i couldn't follow the conversation and i think he ended up using madwifi instead?

---

### Post by archaggie828 on 2007-05-18
ok, so i just got back from the store with my linksys wmp54g pci wireless-g adapter, plugged it into the motherboard, booted up, and enabled the wireless network under system>network and poof it all worked automagicly!!! yay!!! the hell with the stupid usb thing. i want to pull an office space with the damn fax machine on it!! but i might give it to charity. anyhow, onboard wifi = good!!  usb wifi = crap . . . 

so how to fix that problem, i dunno, but i have wifi now, yay!!

---

### Post by GrantShoe on 2007-05-18
> **archaggie828 said:**
> ok, so i just got back from the store with my linksys wmp54g pci wireless-g adapter, plugged it into the motherboard, booted up, and enabled the wireless network under system>network and poof it all worked automagicly!!! yay!!! the hell with the stupid usb thing. i want to pull an office space with the damn fax machine on it!! but i might give it to charity. anyhow, onboard wifi = good!!  usb wifi = crap . . . 

so how to fix that problem, i dunno, but i have wifi now, yay!!

i hate to take the easy way out like that but perhaps it'd be a lot easier.  How much do those run for?

---

### Post by archaggie828 on 2007-05-19
well, i had been working on it for weeks, and wasn't making any progress. then when i installed 7.04 on my best friends desktop it worked right away with that wireless card, granted she has a 32 bit system, but everything i have read shows much more support for pci cards than usb. and at fry's they run for $49.99. i think they are better quality anyhow. i had gotten the usb one for like $20 about 2 years ago now, for school, so the upgrade was worth it to me.

---

