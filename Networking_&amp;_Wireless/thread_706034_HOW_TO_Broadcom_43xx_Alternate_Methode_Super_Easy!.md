---
title: "HOW TO: Broadcom 43xx Alternate Methode Super Easy!"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by uberlube on 2008-02-24
[COLOR="Red"]BEFORE YOU START: This guide was made for Gutsy and may not work for Hardy depending on your setup. If youve gone through  this and it doesnt work give [this ]("http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy")thread a try[/COLOR]

Of all the methods that I have come across to install the finicky bcm43xx driver, this is the quickest and easiest one to use. (In my opinion)

First get yourself ndiswrapper, either from the repositories or by typing this command into terminal:

```
sudo aptitude install ndiswrapper-utils-1.9 
```

Or just grab it from synaptic package manager.

and type these into a root terminal:

```
echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "blacklist ssb" >> /etc/modprobe.d/blacklist
echo "blacklist b43" >> /etc/modprobe.d/blacklist
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
echo "alias wlan0 ndiswrapper" >> /etc/modprobe.conf
echo "ndiswrapper" >> /etc/modules
mkdir /root/wireless_driver
cd /root/wireless_driver/
wget http://ftp.us.dell.com/network/R151517.EXE
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf
modprobe ndiswrapper
reboot

```


And there you have it! Hope this works for you as well as its worked for me :)
[COLOR="Red"]
EDIT: If you run through this one time and it does not work, don't fret. Try changing 'wlan0' to 'eth1' and this will probobally solve the problem. [/COLOR]

---

### Post by Papa-san on 2008-02-24
when I type the first command, I get:
```
sudo echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
bash: /etc/modprobe.d/blacklist: Permission denied

```

---

### Post by uberlube on 2008-02-24
In order to be able to type in these commands you must be in a terminal with root privileges:

```
sudo su
*password*

```

---

### Post by Papa-san on 2008-02-24
Well, it was worth a shot!
I still don't have wlan0 listed in the network GUI. Just eth0 and ppp0

EDIT:
After formatting and installing 7.10, I ran through this again, and it works flawlessly! (since 'iwconfig' gave me eth1 instead of wlan0, I replaced the wlan0 in your post with eth1)

Thanks!

---

### Post by uberlube on 2008-03-02
Oh ya, I forgot to specify that might need changing. Glad it worked! :)

---

### Post by Tdclarke on 2008-03-08
(Also posted [here](http://ubuntuforums.org/showpost.php?p=4475472&postcount=4))

**@Uberlube**
I tried out your guide (as well as many others on this forum) before creating this new thread. I got to where it is bold (see below), and then it could not locate the executable - Presumably because I have no connection :? Therefore could not extract the zip because it did not exist on my HDD

> echo "blacklist bcm43xx" >> /etc/modprobe.d/blacklist
echo "blacklist ssb" >> /etc/modprobe.d/blacklist
echo "blacklist b43" >> /etc/modprobe.d/blacklist
echo "alias eth1 ndiswrapper" >> /etc/modprobe.d/ndiswrapper
echo "alias eth1 ndiswrapper" >> /etc/modprobe.conf
echo "ndiswrapper" >> /etc/modules
mkdir /root/wireless_driver
cd /root/wireless_driver/
[B]wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf
modprobe ndiswrapper
reboot[/B]

So would this process work if I used network cable, and downloaded the executable that way?
Also, would I replace:
> wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
with:
> wget [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) 
As that is what [this](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/) says to use with my wireless card. (#13)
Finally, that link (acer-euro.com) comes up with this message (whilst on XP that is):
> 550/notebook/aspire_3020_5020/driver/: No such file or directory
Does that mean I will have to find it elsewhere, or is it something that may just only be accessed via ubuntu? Sorry for all the questions :?

Thanks a lot for your help :)

---

### Post by uberlube on 2008-03-09
I made this guide under the assumption that people would have their laptops hooked up through an ethernet cable to temporarily have the internet during this process. Of course you could always carry out the first few steps of my guide and then transfer the actual driver from another cpu, via CD or flash card. As long as you drop the file into the directory that you have made (wireless_driver) then you can continue. Let me also state that this HOWTO is for BROADCOM wireless devices. Although this guide is similar in some ways to what you would do with another card(belkin for instance) it may not work the same. If you would like an excelent guide for how to universally use ndiswrapper check out this link:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=574501&highlight=ndiswrapper)

Also, if anyone would like me to give them help with this guide or getting another wireless card working, just send me a PM with the link to your thread and I would be happy to help you out.

Sincerely, 
Dan

---

### Post by jd8001 on 2008-03-09
Just wanted to say this method worked for me. The only change I had to make from the original instructions was to replace wlan0 with eth1. Also, I had been screwing around with this stuff for a while, so I made sure I deleted the previous install of bcml5.inf with the command

ndiswrapper -r bmcl5.inf
 also, I was indeed connected to a hardline during the proscess.
Anyway, I'm making this post on my wifi connection. 


JD

---

### Post by icechen1 on 2008-03-22
Works for me,i had to replace wlan0 to eth1.

---

### Post by mykrob on 2008-03-26
didnt work for me. Using a Compaq Presario V5204NR laptop.

I had no problems with the instructions. When I run ndiswrapper -l, it shows the hardware present, with ssb as an alternate driver. It shows as 4311. However, rmmod-ing ssb and b43, and modprobing ndiswrapper does not activate the wireless device. I addedd the necessary lines to blacklist modules and load modules on bootup, same thing again.

iwconfig shows no wireless extensions. i have tried adding the alias for wlan0 and eth1, neither worked.

Help?

The B43 driver works, but i have to sit dead in front of my router...

-myk

---

### Post by mykrob on 2008-03-26
UPDATE:
got it working.. kinda... For some reason, the module ssb is still getting loaded, even though it is blacklisted. I have to manually rmmod ssb, then rmmod ndiswrappper, then reload ndiswrapper....

Why is this module still loading??!!!

thanks,
-myk

---

### Post by mykrob on 2008-03-27
bump

---

### Post by mykrob on 2008-03-28
bump

---

### Post by uberlube on 2008-03-29
OK easy on the bumps. What is ssb first of all, and second you said that you have it working sort of. Elaborate.

---

### Post by mykrob on 2008-03-29
Hey, thanks for the response.

Not exactly sure what the ssb module is, when i run ndiswrapper -l, it shows ssb as an alternate driver , apparently it has something to do with the bcm4311 chipset in some form or fashion.

Whatever it is, apparently some update i ran yesterday seems to have fixed the problem. I have not changed anything, but now my wifi loads up like it should.

Although i'm satisfied that it is working, i am very curious as to what was happening before..

-myk

---

### Post by mogwins on 2008-04-25
Using 8.03, I couldn't see any wireless networks, but now I see a few! Thanks a lot for the comprehensive guide (if I can follow it as a Linux newbie, it must be well put together!).

Of course, now I'm having difficulty connecting to my WEP-encrypted network, but at least I can see it - progress!

---

### Post by gerben1 on 2008-04-25
Could you perhaps also shed some light on getting wired internet working in Hardy Heron. I uninstalled b43-fwcutter (using: aptitude remove b43-fwcutter) following some tutorial to get wireless working, perhaps that has something to do with it? I already reinstalled it (downloaded b43-fwcutter_001-1_i386.deb on another computer and installed that) but I still cannot connect to the internet...

---

### Post by uberlube on 2008-04-28
> **mogwins said:**
> Using 8.03, I couldn't see any wireless networks, but now I see a few! Thanks a lot for the comprehensive guide (if I can follow it as a Linux newbie, it must be well put together!).

Of course, now I'm having difficulty connecting to my WEP-encrypted network, but at least I can see it - progress!

Thanks for the praise and Im glad that it is easy to understand for begginers as they are the ones I had in mind while creating it. As for your question, there are several types of encryptions that you can use and when accessing a network you are required to specify what type of WEP encryption you are using. Either 64 bit or 128 bit WEP. It should give you the option to specify which you are using in the same area as where you input your password. I havent used Gnome (as I am stricktly KDE) for a long time so I cant remember exactly where it is but this should help you get close enough to find it.

---

### Post by uberlube on 2008-04-28
> **gerben1 said:**
> Could you perhaps also shed some light on getting wired internet working in Hardy Heron. I uninstalled b43-fwcutter (using: aptitude remove b43-fwcutter) following some tutorial to get wireless working, perhaps that has something to do with it? I already reinstalled it (downloaded b43-fwcutter_001-1_i386.deb on another computer and installed that) but I still cannot connect to the internet...


I havent used hardy yet so I cant really tell you if this is a common problem or not but wired internet should work by default. Although it may be possible that you have to make an account in your network manager to access the internet as some distrobutions require this, but I havent seen this in ubuntu except for the xfce environment.

---

### Post by ssh001 on 2008-05-21
The procedure works for Dell xps m1330. Thank you

---

### Post by uberlube on 2008-06-25
Check OP for those of you trying to get this guide to work with hardy. I don't spend as much time online right now so sorry to those of you who have PM'd me with no response.

---

### Post by gdlx on 2008-07-14
Thank you very much! It worked perfectly.

Grady

---

