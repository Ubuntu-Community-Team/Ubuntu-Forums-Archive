---
title: "I can't believe how terrible networking is in Ubuntu !"
date: 2007-10-25
forum: Networking &amp; Wireless
---

### Post by elmerfud on 2007-10-25
I can't believe how terrible (wireless) networking is in Ubuntu.

I'm a long time Fedora user.  I installed Edgy and then upgraded to Fiesty and now Gutsy.  I've got a laptop with a Broadcom 4306 card in it.

Every time I upgrade there are issue with wireless networking.  For starters, whatever I had running previously ceases to work, even if I revert to a previous kernel.  Don't ask me how that happens.

I thought that the whole wireless driver thing was supposed to get streamlined so that Joe average could install a wireless driver.  I've got an application in my K menu called "Windows Wireless Drivers" but the application doesn't work when I run it !   

I thought that there was supposed to be a repository that had pre compiled ndiswrapper modules, but apparently there isn't, or at least I can't find them using apt-get..

It now appears that network speeds are being seriously impeared by ipv6 stuff. 

The real kicker is finding an application to manage wireless hotspots.  Right now I am using a combination of the command line (ifup, etc.) wifi-radar and wlassistant.  None of them is the complete solution.   

I don't know how to control which network I connect to with ifup.  At this stage of Linux's development, I shouldn't have to using a command line command to connect !

Wifi Radar works sometimes.  It seemed to work OK in Feisty, but not at all in Gutsy.

Wlassistant was a joke in Feisty, but it did get me connected.  It had a ton of bugs.  Its better in Gutsy, but still has several bugs.  Sometimes it reports "no networks found" when I know that I am surrounded by wireless networks.  Other times I have to connect twice to a network to get it to connect.  In Feisty it used to get the network SSIDs mixed up and try to connect to a non existing network.  In short, its terrible.  These sorts of bugs should never have shipped in the first place.  

I can't believe that these distros ship with so many wireless networking problems.   I think the problem is lack of testing.  Specifically, I think that people generally use the live CDs when testing the release candidates.  And I suspect that very few go through the trouble of setting up wireless networking during that test phase.  And thus wireless doesn't get tested.

In short, I think Ubuntu wireless support is terrible.   What can I do as a Ubuntu user to change this ?

---

### Post by Mal1024 on 2007-10-25
Broadcom wireless cards are known to be difficult to set up in Ubuntu and most other distributions. Try googling for a solution.

---

### Post by magikx21 on 2007-10-25
I setup my Broadcom wireless card in Fiesty in no time, there is a guide somewhere in the forums here that I used.

---

### Post by stevoo on 2007-10-25
You could try Wicd ...... it is better than the other that yoy have posted.

Tried Wifi Radar , but was too bugy to actually stay with it.


I have a a broadcom BCM94311 , and i am just about ready to start crying my self. It was working perfectly in 7.04 but the moment i upgrade it all hell broke loss. 

I also have Vista on mie and if i boot on Vista and do a speed test ill go up to 10 - 14 mb , but on Ubuntu it will not manage to get above 1mb ( i am on a 20mb cable) ... but on the upload the speed is just fine ! 

Constant disconnection , low speeds , disconnection , disconnection ....... you got the point 

Ive trying various things to see if i can stable my connection but nothing seems to have done the work.

Before i deactivate IPv6 the speed was even worse, so you may wanna start with that. 

As for the rest, i just hope that you are not us unlucky as me and if you find something just post it here for us :(

---

### Post by Em-Buntu on 2007-10-25
> **elmerfud said:**
> I can't believe how terrible (wireless) networking is in Ubuntu.

I'm a long time Fedora user.  I installed Edgy and then upgraded to Fiesty and now Gutsy.  I've got a laptop with a Broadcom 4306 card in it.

Every time I upgrade there are issue with wireless networking.  For starters, whatever I had running previously ceases to work, even if I revert to a previous kernel.  Don't ask me how that happens.

I thought that the whole wireless driver thing was supposed to get streamlined so that Joe average could install a wireless driver.  I've got an application in my K menu called "Windows Wireless Drivers" but the application doesn't work when I run it !   

I thought that there was supposed to be a repository that had pre compiled ndiswrapper modules, but apparently there isn't, or at least I can't find them using apt-get..

It now appears that network speeds are being seriously impeared by ipv6 stuff. 

The real kicker is finding an application to manage wireless hotspots.  Right now I am using a combination of the command line (ifup, etc.) wifi-radar and wlassistant.  None of them is the complete solution.   

I don't know how to control which network I connect to with ifup.  At this stage of Linux's development, I shouldn't have to using a command line command to connect !

Wifi Radar works sometimes.  It seemed to work OK in Feisty, but not at all in Gutsy.

Wlassistant was a joke in Feisty, but it did get me connected.  It had a ton of bugs.  Its better in Gutsy, but still has several bugs.  Sometimes it reports "no networks found" when I know that I am surrounded by wireless networks.  Other times I have to connect twice to a network to get it to connect.  In Feisty it used to get the network SSIDs mixed up and try to connect to a non existing network.  In short, its terrible.  These sorts of bugs should never have shipped in the first place.  

I can't believe that these distros ship with so many wireless networking problems.   I think the problem is lack of testing.  Specifically, I think that people generally use the live CDs when testing the release candidates.  And I suspect that very few go through the trouble of setting up wireless networking during that test phase.  And thus wireless doesn't get tested.

In short, I think Ubuntu wireless support is terrible.   What can I do as a Ubuntu user to change this ?

I agree, but it's hosed in "wired" networking also.

I fully expected some "issues" with Gutsy, but networking and browsing is something basic that I did not expect since they worked so flawlessly in Feisty. 

At this point, Gutsy is a serious step backwards in the evolution of Ubuntu. It's virtually unusable for me.
I am very disappointed with the low quality of functionality and reliabilitity of this release. It doesn't appear to be fixable without an additional release or update.

---

### Post by elmerfud on 2007-10-25
> **Mal1024 said:**
> Broadcom wireless cards are known to be difficult to set up in Ubuntu and most other distributions. Try googling for a solution.

I've been using this card/laptop for 3 years, all with Linux.  I think the first distro was FC3.  This is by far the worst.  With FC3 you knew everything had to be set up manually using ndiswrapper.  

With Gutsy its a mish mash of stuff, some manual, some automatic, some stuff that works, some that is buggy.   There is no excuse for that at this stage of the Linux life cycle.

---

### Post by Ariccanfly on 2007-10-25
I'm pretty impressed with 7.10, it installed the cutter and d/led the firmware automatically with my 
bcm94311MCG 

but as you may know the reverse engeneered drivers are still slow. like 1-3 mbit as opposed to the 24mbit maximum... 

so use ndiswrapper if you want full speed. Thats easy to install too!

I do however want a better applet than nm-manager I need to be able to disable my wirless so i can suspend to ram..

Better applet plz!
(i guess i could install KDE)

---

### Post by ive on 2007-12-20
hi guys! :)

im new with linux and i installed Kubuntu 7.10 yesterday on a Compaq nx7300 notebook.
Its the first time i use a linux OS but its goin well, i think..

The first thing i wish to make function is the wireless device** Broadcom BCM94311MCG**, cause i need to have internet connection on that computer , i think is the most important thing..

I see the device in my "Network settings" window, but if i right-click on it,and try to enable it, it takes some seconds and its the other device (ethernet) to be enabled, also if i clicked on my Wireless device.


here is the result of my ** iwconfig**

lo          no wireless extensions

eth0      no wireless extensions

eth1      IEEE 802.11b/g  ESSID:"GiNa"  Nickname:"Broadcom 4311"
             Mode:Managed  Access Point:Invalid
             RTS thr: off   Fragment thr: off
             Link quality=0/100   Signal level=-256 dBm  Noise level=-256 dBm
             Rx invalid nwid :0  Rx invalid crypt :0   Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0  Missed beacon:0


Can someone help me, explainin me as a beginner ? 

thank you, and excuse me for my bad english..im italian..

---

### Post by Edho on 2007-12-20
Give command in a terminal.

sudo lshw -C network

Post the result.

---

### Post by ive on 2007-12-20
hej, i got it ! :) 

it does function now !

---

### Post by Munga008 on 2007-12-20
I'm having the same problems, even made a thread about it [http://ubuntuforums.org/showthread.php?t=644066](http://ubuntuforums.org/showthread.php?t=644066). But I'll give the sudo network command a whirl. I'm as new as you can get to Linux so bear with me :). Will post the results in 10mins, just gotta switch over to Ubuntu.

---

### Post by Junglizer on 2007-12-20
> **elmerfud said:**
> **Every time I upgrade there are issue with wireless networking.**  For starters, whatever I had running previously ceases to work, even if I revert to a previous kernel. 
In short, I think Ubuntu wireless support is terrible.

**What can I do as a Ubuntu user to change this ?**


Looks like you answered your own question to me. Don't @#$!'ing upgrade. It isn't a patch, its a full rebuild. Wireless in all forms of *nix have been difficult for some time, however its made great bounds in the last 2 years. That aside, remember that the GUI is merely an application running on top of the system and not integrated itself, which means just b/c there are gui apps for wireless configuration, the CLI programs will have the same if not more functionality and configurabilty of your devices. I try and stress that (not to say you mentioned this but many have) Linux, and specifically Ubuntu, are not Microsoft Windows replacements. Now I'm not saying you can't use them in place of Windows, but just remember, Linux is entirely different from the ground up. Yes there is plug and play, yes most stuff does actually "just work" when you plug it in, but it is still Linux, which initially was all command line from the beginning.

---

