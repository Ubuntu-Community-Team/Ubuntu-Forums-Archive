---
title: "[SOLVED] Which Device Should I Use?"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by chrome307 on 2007-08-25
I have an option of two WiFi devices 

HiTech Point PCI card
3Com USB Adapter

These are details of the PCI card:

[img]http://img443.imageshack.us/img443/6237/19069002qk3.png[/img]

This is the USB adaptor:

**3Com 3CRUSB10075** - supported on the WiKi - Works on Dapper using network administration tool with no encryption (WEP not tested). Not detected by network-manager (so no WPA)

---

### Post by Steve1961 on 2007-08-25
If the internal card works go with that.  If not, you can probably still get it working with ndiswrapper.  As for the usb device, great if it works out of teh box, and you can probably get it to work with wpa as well if you go the ndiswrapper route.  see, for instance:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_0-9/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_0-9/)

---

### Post by chrome307 on 2007-08-25
Would that mean that I should downgrade to 6.06 to use the USB adapter?

Either would be great so I can finally move the PC away from the router at present as it's not particularly convenient with only a 5m  cable :lolflag:

---

### Post by Steve1961 on 2007-08-25
You shouldn't need to downgrade to dapper.  If you can only use manual network configuration use that, just make sure you uncheck the box for roaming mode so that network manager isn't used.

---

### Post by chrome307 on 2007-08-26
OK that's good news :)

I have read an old thread on the forum posted back in Dec 2006 where someone with the same adapter has made this work:

[http://ubuntuforums.org/showthread.php?t=328314&highlight=3COM+3crusb10075](http://ubuntuforums.org/showthread.php?t=328314&highlight=3COM+3crusb10075)

I have attempted to follow the steps outlined but am not able to carry out the installation.

Can anyone help?

I downloaded a file from the link below but it does not have the same file name as shown in the earlier thread.

=============================================

   1. Download the driver from [http://zd1211.ath.cx/download/zd1211-driver-r48.tgz](http://zd1211.ath.cx/download/zd1211-driver-r48.tgz).
   2. Extract the file using "tar -zxvf zd1211-driver-r48.tgz".
   3. Run "cd zd1211-driver-r48"
   4. "make"
   5. "make install"
   6. Activate driver by using "modprobe -v zd1211"


then in a terminal type 

sudo apt-get install build-essential (or use synaptic to install it)

make sure you have "build-essential" installed then

make distclean
make
sudo make install

[IMG]http://img484.imageshack.us/img484/7098/3comps9.jpg[/IMG]

---

### Post by Steve1961 on 2007-08-26
Why not just go with ndiswrapper?  You can then choose either the onboard wifi or the usb card.  Just extract the .inf and .sys file from the windows driver (you can do this with winzip in windows or cabextract in linux).  Place both in a folder in your home directory.  Install ndiswrapper and then do the foloiwng:

sudo ndiswrapper -i /home/yourname/driverfolder/abcd.inf (change the path and file name to whatever they actually are)

Check the driver is installed:

sudo ndiswrapper -l

Then load the ndiswrapper module:

sudo modprobe ndiswrapper

Check you now have an interface called wlan0 when you type iwconfig in a terminal.

Then type:

sudo ndiswrapper -m

and

sudo gedit /etc/modules

and add the word ndiswrapper to the end of the file.

You'll also find lots of ndiswrapper how tos on this forum

---

### Post by chrome307 on 2007-08-26
Thank your for your answer ..... I'm glad you outlined it for me so easily to understand.

Unfortunately I'm not sure which version of the NDISWrapper to download ..... I looked at the url you posted earlier and could not find my adapter there, but one for the next model up ( I think ).

Also to grab the INF files .... they should be on my Windows PC or available on the install CD?

Sorry about all these questions ........... too many years of Windows abuse and complacency  :(


These are the files I have on the CD

[IMG]http://i17.tinypic.com/5xnzcpt.jpg[/IMG]

[IMG]http://i17.tinypic.com/4lt600n.jpg[/IMG]

[IMG]http://i19.tinypic.com/4zu88ef.jpg[/IMG]

[IMG]http://i9.tinypic.com/4pofc76.jpg[/IMG]

[img]http://img517.imageshack.us/img517/7223/52994495as4.jpg[/img]

---

### Post by Steve1961 on 2007-08-26
> Unfortunately I'm not sure which version of the NDISWrapper to download ..... I looked at the url you posted earlier and could not find my adapter there, but one for the next model up ( I think ).

Just install ndiswrapper from the Ubuntu CD - the ndiswrapper utils and ndiswrapper-common packages
> 
Also to grab the INF files .... they should be on my Windows PC or available on the install CD?

The install cd or download them from the manufacturers websites.  Don't forget that you need the .sys and .inf files in the same directory, even though you only install the .inf.

---

### Post by chrome307 on 2007-08-26
Thanks again ..... there is a readme file contanined within the NDSWrapper which suggests I use the XP or 2K file and this is the detail of the device

[IMG]http://img205.imageshack.us/img205/2316/75607428pm8.jpg[/IMG]

Fingers crossed :)

[EDIT]

**[COLOR="Red"]Thank you again ........... it's working !!![/COLOR]**

[img]http://img480.imageshack.us/img480/2387/happyuk4.jpg[/img]

---

