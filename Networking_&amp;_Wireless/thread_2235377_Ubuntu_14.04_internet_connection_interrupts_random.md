---
title: "Ubuntu 14.04 internet connection interrupts randomly, Lenovo Y50-70, rtl8723be driver"
date: 2014-07-20
forum: Networking &amp; Wireless
---

### Post by platokid on 2014-07-20
Hi all :)

My new laptop Lenovo Y50-70 is having some problems with the internet connection. Using Windows 8 I experienced no problems at all,
but I really need Ubuntu for my work at the university and because it is the better OS ;)

Running Ubuntu right after my login the internet is usually working, but after a random amount of time the internet connection just interrupts
although I can still receive the router's signal (and get the full "bars"). I have already tried different approaches to solve my problem:

1) as shown here: [http://ubuntuforums.org/archive/index.php/t-2199638.html](http://ubuntuforums.org/archive/index.php/t-2199638.html)
I did this right after installing Ubuntu. I tried to install the driver via
```
git clone http://github.com/lwfinger/rtl8723be
cd rtl8723be
make
```
but it wouldn't compile so I used:
```
git checkout 604aa9058fb9e5bb1cf571c99989d081f8fc8b9
make
sudo make install
sudo modprobe rtl8723be
```
and it worked until I experienced the problems stated above

2) Then I tried this: [http://ubuntuforums.org/showthread.php?t=2220933](http://ubuntuforums.org/showthread.php?t=2220933)
```
sudo gedit /etc/modprobe.d/rtl8723be.conf
```
and added the line
```
options rtl8723be fwlps=0 swlps=0
```
which should prevent the WiFi card from automatically sleeping.

At first this seemed to solve my problems. But then the problem occured again.
I may just have been lucky for a few days (as the interruptions are after random amounts of time)
but I also thought about other reasons: An Ubuntu update I installed a few days ago -
could that be it and how could I solve it? - or my migration from Germany to Switzerland / France.
Therefore I tried the following:

3) I changed the RegDomain settings: [http://ubuntuforums.org/showthread.php?t=2212404](http://ubuntuforums.org/showthread.php?t=2212404)
```
sudo iw reg set FR
iw reg get
```
but it didn't fix the problem.

4) Afterwards I tried this: [http://askubuntu.com/questions/224619/how-to-resolve-wireless-disconnect-problem-in-atheros-ath9k](http://askubuntu.com/questions/224619/how-to-resolve-wireless-disconnect-problem-in-atheros-ath9k)
```
/etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
```
but it wouldn't help.

Thinking the update might have ruined it I repeated step (1) but I got errors referring to the "ath9k.conf" file.
So I deleted the file and now Ubuntu won't even boot anymore :( :( :(
I am really really stuck at the moment and would greatly appreciate any help :)
Please have in mind that I am still kind of a "beginner" regarding Linux and Ubuntu...

---

### Post by varunendra on 2014-07-20
Welcome to the forums platokid!

There is a slight confusion in your post above. Your earlier approaches involved solutions for a realtek card, then in step 4 you tried something that only applies to atheros cards, do you have both? I doubt that. Do you know exactly which card you have and which driver it is using?

To show us a detailed report about your wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by platokid on 2014-07-21
Thank you for your quick reply.
> Do you know exactly which card you have
I am quite sure, I tried the Atheros solution because some friend of mine told me it would refer to something other than the wifi driver.
At the moment my problem is that I cannot even boot Ubuntu - I don't know why.
Can I just delete the partition of the hard disk on which I installed Ubuntu or should I try something else?
I think I'll just try to get Ubuntu running again myself and then report again if I executed your script ;)

---

### Post by varunendra on 2014-07-21
If it is a UEFI based installation (thus booting win8/ubuntu from EFI menu), you can safely remove the Ubuntu partition if you wish so. The only (obvious) problem will be that you'll get some error if tried to boot Ubuntu from EFI menu after deleting the partition.

If it is a legacy installation (not likely with Win8) where grub is booting both Ubuntu and Win8, deleting the partition will render both OS unbootable, because the grub configuration files would also be deleted with Ubuntu partition.

---

### Post by platokid on 2014-07-21
It's grub unfortunately...

---

### Post by varunendra on 2014-07-21
Was Win8 pre-installed or you installed it yourself later (in legacy/MBR mode)?

The preinstalled Win8 systems are all UEFI based installations as far as I know. Changing the BIOS to legacy mode later would render Win8 unbootable if originally installed in EFI mode.

---

### Post by platokid on 2014-07-21
It was preinstalled, but I everytime I boot my laptop I get the grub task menu. So would you say it is UEFI based?

---

### Post by dmmo on 2014-07-21
Dear all,
I have the same problem with the same computer. In contrast to platokid, mine was bought w/o win 8 and then Ubuntu 14.04 64 bit was installed. The wireless card is the following one:

 description: Wireless interface       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 90:48:9a:c7:2f:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:4000(size=256) memory:d1600000-d1603fff

Do you know what could be the reason of such a misbehavior? 

Kind regards,
Dmitry

---

### Post by varunendra on 2014-07-21
> **platokid said:**
> It was preinstalled, but I everytime I boot my laptop I get the grub task menu. So would you say it is UEFI based?
Unless it was changed in the BIOS setup later, yes, I still think it should be a UEFI based installation. I have no personal experience with EFI booting, so can't comment anything with confidence, but I think it is possible that one of the OSes (currently Ubuntu) is set as default in EFI boot menu, and booting Ubuntu from there chainloads grub2 on its partition, which then provides the menu you get.

Whether UEFI is enabled or not should be easily verifiable in BIOS setup though. Besides, I think this problem/discussion deserves a separate thread, we are taking the thread offtopic. :p

> **dmmo said:**
> Dear all,
I have the same problem with the same computer. In contrast to platokid, mine was bought w/o win 8 and then Ubuntu 14.04 64 bit was installed. The wireless card is the following one:

 description: Wireless interface       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 90:48:9a:c7:2f:d3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-32-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:4000(size=256) memory:d1600000-d1603fff

Do you know what could be the reason of such a misbehavior? 

Kind regards,
Dmitry

Hello Dmitry,

As you can see we are stuck here on a different problem now, so I suggest you post a separate thread to avoid confusion, and post the details of your problem along with the wireless_script I linked to in my first post here. You can link this thread as reference to your problem if you wish, and post a link to your thread here so we can follow.

---

### Post by dmmo on 2014-07-21
Sorry, I will do it now.

The link is here: [http://ubuntuforums.org/showthread.php?t=2235493&p=13078945#post13078945](http://ubuntuforums.org/showthread.php?t=2235493&p=13078945#post13078945)

---

### Post by varunendra on 2014-07-21
Nothing to be sorry about, was just a better option that I suggested :)

---

### Post by Balach on 2014-08-19
I just got me a y50-70 and have the same problem i.e. After a random amount of time the wifi drops, and no amount of modprobing gets it back. I have to reboot to get it working again, and wait till it drops again. At this point I'ld be happy if I can find something to reset it without rebooting, and hope for a permanent solution later.. 

Returning user to linux after many years, know where the terminal is and how to run commands; don't know how to do magic with kernel and stuff

---

### Post by varunendra on 2014-08-19
Welcome to Ubuntu Forums Balach!

Like suggested in post #9, it would be much better for you to start a new thread instead of posting in this old one. Along with a description to the problem, please also post the report generated by 'wireless_script' in it : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

You can then post a link to your thread here (in a new post, else we won't be able to notice that you posted the link), so we can follow.

---

