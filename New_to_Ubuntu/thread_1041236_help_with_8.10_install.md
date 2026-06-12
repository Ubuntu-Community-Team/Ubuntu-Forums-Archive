---
title: "help with 8.10 install"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by angliski on 2009-01-16
I have just installed Ubuntu 8.10 from the downloaded iso file.

I am unable to activate the restricted driver to run my display and also ubuntu will not let me load my wireless network

I am running it on a partitioned disk, on it's own partition on an Acer 5520 laptop.

The machine came with windows vista pre-installed and has fittedan Nvidia GeForce 7000M/nforce610m video card and an Atheros AR5007EG Wireless Network adaptor

The chip is an  64x2 Dual core processor TK 55.

I have phoned Acer who say that they do not support dual booting on their machines, (great help)

Can anyone tell me how to get my graphics card and wireless card working properly please.

Many thanks

Steve

---

### Post by Melk79 on 2009-01-16
It looks like your Atheros wireless chip may have a problem with Intrepid, but the release notes offer a [suggestion]("http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default").

As far as your Nvidia chip, this [link]("https://help.ubuntu.com/community/NvidiaManual") may help, but it looks a bit involved.  Not sure how comfortable you are with some of those tasks.  My 8400M has always worked great, but that doesn't help you.  Perhaps this link could help [http://www.nvnews.net/vbulletin/showthread.php?t=105392](http://www.nvnews.net/vbulletin/showthread.php?t=105392).  Let us know.

---

### Post by angliski on 2009-01-17
Thanks for the suggestions. I have tried to find linux-backports, but to no effect. They do not seem to have been installed on my computer and I cannot find them on the disk.
I have also tried to sort out the blacklists as suggested elewhere in this forum, but cannot find the ath5k module typying grep -r "ath5k" .etc/modprobe.d/ , did not give any results.

I am not too good at Linux and tend to rely on the disc having all I need. I can do basic editing using terminal if the commands are simple.

I downloaded my version of 8.10 onto a windows drive from the Ubuntu site and burned it to DVD from there.

I am wondering if Kubuntu might work better.

Cheers and thanks for your help

Steve

---

### Post by gettinoriginal on 2009-01-17
Hope these two help, the first is for Nvidia, and second for wireless:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by angliski on 2009-01-20
Dear Gettinoriginal

Many thanks for your post. The steps seem very clear and I have managed to follow the first couple of them.

Let me explain, that I have Ubuntu 8.10 installed on my computer, but cannot get either wireless or the Nvidia graphics card to work.

As far as the wireless card Atheros AR5007EG is concerned, my installation of Ubuntu, downloaded via windows and burnt to a DVD, does not show my wireless card at all.

I followed your instructions and typed lshw -C network into the terminal and got the following.

(sorry I cannot send the output, but as I have no working wireless in Ubuntu, I have to print the output and then write it.

"steve@steve-laptop: ~$ lshw -C network
WARNING: you should run this program as super-user.
*network
description: Ethernet interface
product: MCP67 ethernet
vendor nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
versio: a2
serial: 00:1b:38:25:7d:f5
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driver version=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

*network UNCLAIMED
description Ethernet controller
product AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@05:00.0
version: 01

I hope that you can make some sense of this, because it's all Greek to me.

I am trying to get the wireless card running first, before I try for the nVidia graphics card, so that at least I will have access to the internet and don't have to keep shutting Linux down and restarting windows in order to report what I am doing and what is happening.

Maybe I am wrong, but it seems to me that Linux cannot see my Atheros card. I have tried to find it but cannot see it in any Linux files.

When I go into hardware manager, it shows me restricted files, but will not activate them. I wonder if downloading the iso file to windows is to blame.

I have run Linux before, (Ubuntu feisty,hardy 8.04 and 8.10) on another laptop which was very similar to this one. The two main differences were, a Broadcom wireless driver and I downloaded the drivers and eventually managed to install them, after which Ubuntu worked perfectly. That computer used Window XP and not Vista.

Thank you so much for taking the time to help. I am sure that once I can get this problem sorted, I will be able to pass on your knowledge to the other people on the Isle of wight, who would love to get away from windows, but find Linux a bit daunting, (as I do)

Once again, many thanks for your time

Steve

---

### Post by gettinoriginal on 2009-01-20
I know it is a pain to not have internet access, so I am copy/pasting what I found.  But if you have internet through windows, you can go to:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) and print the whole page.

Atheros ath5k wireless driver not enabled by default

The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. **While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. **
Please note the area in bold. :D

---

### Post by redseventyseven on 2009-01-20
> **gettinoriginal said:**
> I know it is a pain to not have internet access, so I am copy/pasting what I found.  But if you have internet through windows, you can go to:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810) and print the whole page.

Atheros ath5k wireless driver not enabled by default

The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. **While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. **
Please note the area in bold. :D

Umm... if I were just starting out with Linux and Ubuntu, then I'd be somewhat mystified as to what that means!

Steve (angliski) - welcome to the world of Ubuntu and Linux!

I'm not sure how much you know already about "package management" yet - I'll assume none at all. Forgive me if that's an underestimation.

The system of package management is central to the idea of Linux. It's one of the things that makes, in my opinion, Linux superior to Windows. However, it also makes Linux different from Windows, which means it causes confusion when you first come across it.

Packages come from large collections of software maintained by Ubuntu (or other developers) called repositories. Most of these are accessed using the internet - once you get your network card working you'll be using these all the time to get new software and drivers for your computer. However, a few key packages, like the linux-backports-modules-intrepid-generic package, are on your installation CD.

To access them, you can use a program called Synaptic Package Manager - you should be able to find it somewhere in the Administration menu (I use a slightly different flavour of Linux so I'm not sure exactly where). Search for linux-backports-modules-intrepid-generic in the Package Manager and you should be able to install it - first, mark it for installation, then click "Apply".

See how you get on with that - hope it helps!

---

### Post by redseventyseven on 2009-01-20
> Maybe I am wrong, but it seems to me that Linux cannot see my Atheros card. I have tried to find it but cannot see it in any Linux files.


Don't worry - Linux *can* see your network card - you can see it listed in the output of the lshw -C command.

To cut a long story short, essentially the interpretation of that output is that Ubuntu can see your wireless card loud and clear, but it doesn't have the drivers installed to be able to use it yet.

---

### Post by angliski on 2009-01-21
I found synaptic with no problem. however when searching for linux-backports-modules-intrepid-generic, I was unable to find the file.The name did come up in the left hand box where all the different groups are, but not in the package list and i was not able to install it. In desperation, I redownloaded 8.10 and installed it, but to no avail.

I have no idea what to do next, unless i can somehow run a long long cable to my router and try for a wired connection.

Thanks all for your help so far.

steve

---

### Post by cjv8888 on 2009-01-21
Did you click add CD-Rom at the Software Sources?
Try searching only for linux-backports

---

### Post by angliski on 2009-01-21
Ladies and gentlemen.

I write to you today, courtesy of my atheros wireless card, using my Linux operating system.

Many thanks to all of you for all the help, especially CJV, who's suggestion to turn on the CD search did the trick.

Now to sort out the bloody video card.

Many many thanks peeps. I am over the moon.

Cheers

steve

---

### Post by angliski on 2009-01-21
Ladies and Gentlemen,
I come to you courtesy of my wireless network. Up and finally running on Ubuntu. Many thanks to you all especially CJV for the suggestion of enabling the CD search.

Many many thanks

Steve.

PS, I have also rebooted and it still works

---

### Post by angliski on 2009-01-21
Oh S**t. 2hours of bliss in Ubuntu and I saw a little package manager sign telling me that there were upgrades---so i let the machine install them and now my wireless card doesn't work anymore.

I went into the restricted driver menu and it says that both the driver for Atheros 5xxx cards and the driver for atheros 802.11 lan cards are activated, but no internet. The output from lshw -C networks again shows one inclaimed and one disabled wireless card.

I tried searching in synaptic package manager snd reinstalling Linux-backports-modules-intrepid-generic, but no good.

What on earth have I done? My graphics card is working fine now and everything else seems OK, but no wireless.

Any ideas?

Steve

---

### Post by angliski on 2009-01-21
Got it all back, thanks to a complete reinstall. I won't be updating any packages until I know what I'm doing!!

Many thanks all problem solved 

Steve

---

### Post by Mazza558 on 2009-01-21
By the way, did you ever get the Nvidia drivers working?

---

### Post by cjv8888 on 2009-01-21
Congratulations.

When you update in future, may be an idea not to update anything that has got to do with that linux-backports-modules-intrepid-generic package.

---

### Post by angliski on 2009-01-22
Good idea cjv.
Yes Mazza, once I got the internet working, Iwent to the add/remove section of applications,then into system tools and found the nvidia restricted driver and downloaded it.

Hope this helps.

Steve:p

---

