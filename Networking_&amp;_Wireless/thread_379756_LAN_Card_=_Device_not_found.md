---
title: "LAN Card = Device not found"
date: 2007-03-08
forum: Networking &amp; Wireless
---

### Post by Eniac on 2007-03-08
Hi, (:confused: = me <-- winN00b)

I recently managed to install Ubuntu 6.10 using the alternate release. 

and to make it short, ubuntu doesn't detect my onboard LAN card. im trying to find out to even get the drivers (is there such a thing as drivers in linux ?)

my friend told me to run the lspci command to get a listing of pci devices. well that worked but just to confirm that the eth0 device is not there.

i tried starting it just for kicks with ifconfig eth0 but no luck there.

i went in the docs to see if its documented/supported but i can't find it.

I know the card is an Nvidia chipset because that about as much as the bios will tell me (or the mobo manual for that matter)

mobo is a GeForce6100SM-M and the Network card is onboard (with video and audio)

How can i proceed to get it detected ?


thanks.

---

### Post by Eniac on 2007-03-09
I managed to get more info about the board,

here's the precise name :
Broadcom AC131 10/100 Lan Phy

here's the mobo website with all the info:
[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=685&DetailName=Specification&MenuID=1&LanID=9](http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?detailid=685&DetailName=Specification&MenuID=1&LanID=9)

Now i hate the idea of asking people to do it for me so if someone could just tell me a few directions as to where to start to make it work, I'll be glad to do the digging. I already went over the ubuntu docs but it doesn't tell me what to do to get unknown devices to work. and since im so new to linux, i lack info as to where to look for answers....

Thanks.

---

### Post by Mr. C. on 2007-03-09
Eniac,

Your motherboard vendor's site is currently down.

Please show the output of :

```
lspci
lshw

```
It is necessary to lookup drivers from information not yet provided in your post.

MrC

---

### Post by Eniac on 2007-03-09
Hi Mr. C,

do you want the output of  these command as-is or should I be adding a few switches to it ?

lspci -v ? -vn ?

im currently at work, ill post it when i get home in about 2 hours.

---

### Post by Mr. C. on 2007-03-09
As is is fine.  Its should be just cut/paste.

---

### Post by Eniac on 2007-03-09
Ok, here's the info....

I included output from 

lspci 
lshw (with elevated privileges)
dmesg

i had to zip it because dmesg was bigger than the allowed size for text files.

i took a look and even though i know what information they contain, i am unable to use them to know what to do.

---

### Post by chili555 on 2007-03-09
You know, they have some fine ethernet adapters for about $5 at Newegg... No? OK, let's press on.

Here is an interesting line from dmesg: ```
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
```

When your computer is booting, you will see a message, that only lasts about 3 seconds, that asks you to press ESC to enter the boot menu. When you see the line that looks something like this: ```
 /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
``` move your cusor into it with your arrow keys and make it: ```
 /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro *pci=routeirq* quiet splash
``` Press whatever it says to boot.

Then try the lshw and lspci commands again to see if your card is detected. If so, we can amend your /boot/grub/menu.lst to permanently include this boot option.

I understand Mr. C has a Newegg account you can use.

Let us know.

---

### Post by Eniac on 2007-03-10
Haha, its funny you suggested that, my friend, a gentoo user told me to do the same thing since its so cheap. I'm sure newegg has everything ill ever need but im not prepared to buy a new ethernet card just yet, not before i find that the one i have cannot be used.

I find this is not only about the actual ethernet card not being recognized but more about me learning how to use ubuntu and things to do to troubleshoot.

anyway, unfortunately, the pci=routeirq didn't work, I altered the command line like you suggested but without any real results.

attached is the output from lspci and lshw. I've added some parameters to make them more verbose.

---

### Post by chili555 on 2007-03-10
I have done quite a bit of Googling and have found very little, in general, about the AC131 and nothing, relative to Linux. If you get this going, you will be the first!

The next thing I suggest is ndiswrapper. Iffy, but a better shot than what we've done so far. This depends on extracting the Windows .inf and, possibly, .sys filles from the .exe on the driver disk you got with the computer, or that you can hopefully download from the computer manufacturer's website or the motherboard manufacturer's (ECS, I believe) website.

Here is a post I wrote telling how to extract a Netgear .inf. It will get you started. [http://www.ubuntuforums.org/showthread.php?t=375182&highlight=WG511](http://www.ubuntuforums.org/showthread.php?t=375182&highlight=WG511)

Then install ndiswrapper and pray.

You may have to transfer files with a USB drive. If you are dual-booting Windows, you have the .inf and .sys somewhere in there. Don't ask me where, me no speaka da window.

Remember, if you use Mr. C's Newegg account, you can charge up overnight shipping.

---

### Post by Mr. C. on 2007-03-10
I must be missing the NewEgg reference, and how my account comes into this.  Did I miss the inside joke?  :-)

I was unable yesterday and this morning to look at the data sent closely enough to determine the PCI vendor and hardare IDs.  This is more important than marketing names like AC131, as it allows us to look in the NIC drivers of the  latest source code either in the kernel, or as a download from the chipset vendor and look to see if that hardware is supported.

I'll take a look now and report back what I find.  If the OP is in need, the ndiswrapper is one approach; however, never the optimal approach.

MrC

---

### Post by Mr. C. on 2007-03-10
Eniac, I see no Ethernet device in that configuration.

Run lspci -n

An Ethernet interface would appear in column 2 as "0200", for example:

08:04.0 0200: 8086:1229 ( rev 08 )

but I see no such beast.  Do you have the device enabled in the BIOS?

MrC

---

### Post by Eniac on 2007-03-10
ah! updates!

my friend had me download gentoo minimal CD, just to check if it would detect my ethernet card.

and it did. not only did it detect it but all my other hardware too (ubuntu is missing quite a bit)

with his help, i managed to get ubuntu to see the ethernet card but i have no clue how to mount it.

Gentoo sees :
Forcedeth.c:Reverse engineered nForce ethernet driver version 0.54.

so i did a sudo modprobe forcedeth and tada...
when you do dmesg in ubuntu you can see it, same thing

but that's as far as i can go.

is that enough to mount it and get it going ? ive taken a look at lspci and the device manager after and there's no change. so there must be something im missing.

Also, if it of any interest, most of the onboard stuff seems to be running with the MCP61 chipset because it was written in the name of every single PCI item in gentoo (unknow devices in ubuntu)

i did the lspci -n thing and did not get any "0200" , i guess that's not good. but the bios says its enabled...

---

### Post by Mr. C. on 2007-03-10
I figured it must have been the forcedeth driver, as that's standard for nVidia's chipset.

There are new versions availble, and it might be worth ensuring you get the latest version, as a number of important changes have been made since .54 (current rev is .6 or .61, i forget).

From gentoo, can you get me an lspci -n listing ?

MrC

---

### Post by Eniac on 2007-03-10
woo... you wouldn't believe the trouble i had to get this (good learning xp tho)

getting the listing was a breeze. what i did not know was how to get it on my usb key, or even HD.

then i learned the mount command, took me about 30 minutes to figure it out properly (still learning the basics...)

anyhow.... here it is... the gentoo info.

let me know if it of any help, and also, thank you for spending so much time helping me...


with lspci, i did a -v -n so you would get more info. i also included the dmesg listing.

---

### Post by Mr. C. on 2007-03-11
Eniac,

It took a while, as I'm not familiar enough with the PCI Express data structures yet.  Below is the PCI configuration for your networking card; it is in the Intel PCI Express Port C0.  The device driver (module) you want is forcedeth.  The gentoo kernel you ran is version 2.6.17, but with gentoo additions.  I have not spent any time determining the difference between their kernel and the Ubuntu 2.6.17 verison, but it is clear there was an updated nvidia forcedeth driver.

If you want to use Ubuntu, you will need to update the kernel to the latest available which is 2.6.20, which you will need to build from source.

```
00:07.0 0680: 10de:03ef (rev a2)
	Subsystem: 1019:2602
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping
```

Search the forums, as a few others have done this.  Search for 2.6.20 perhaps, and nvidia.

Cheers,
MrC

---

### Post by chili555 on 2007-03-11
You can get a 2.6.20 kernel without building from source, although building from source is a fun exercise.  I am running 2.6.20 on one of my laptops pain-free. Here's how. ```
1. backup /etc/apt/sources.list
2. replace temporarily (!) all edgy with feisty in sources.list
3. apt-get update
4. apt-get install linux-headers-2.6.20-5 linux-headers-2.6.20-5-generic and linux-image-2.6.20-5-generic. Do not accept the other Feisty updates.
5. double- check /boot/grub/menu.lst, to be certain the root location is correct when compared to your 2.6.17.x kernels. (hd0,0) is mine, for example.
6. restore your /etc/apt/sources.list from step 1
7. reboot
```

The advantage here is that the 2.6.17.x kernel is still on your computer and, if something goes wrong, you can always boot into a previous kernel on startup and fix or delete your 2.6.20.

---

### Post by Eniac on 2007-03-11
Thanks guys,

I'm not sure I feel exactly ready to install a new kernel on my computer given that I know close to nothing but also because even those accustomed to linux finds it a dangerous task.

I'll do it anyway because i got nothing to lose. Either i attempt to switch from Edgy to Feisty or I install Gentoo which does scare me a lot more :) (...or i can install a new NIC card... :p)

I've been searching the forums for info about the new kernel and im still struggling just find the code to compile or the bin to install.

but that's another matter that i can investigate and solve on my own with some digging.

Thanks to both of you, that was very precious help you gave me.

---

### Post by Mr. C. on 2007-03-11
I was pretty sure there was a .20 kernel compiled somewhere; thanks for the info.

Eniac, follow chili555's assistance here.

MrC

---

### Post by Eniac on 2007-03-11
Problem solved!

The solution was to use the 2.6.20-9.16 kernel and source downloaded from Feisty.

afterward, lspci still wouldn't see a thing

but i did a sudo lsmod | grep forcedeth and it was there
then i did ifconfig -a and it was there

then i did sudo dhclient eth0 to activate it, it worked.

then i added it to the boot file

sudo gedit /etc/network/interfaces

auto eth0
iface eth0 inet dhcp


and voila... it works permanently.


i tried to boot with the .17 kernel just for kicks and try the same commands to detect the card and it did not work. so the new kernel is absolutely necessary.


A huge thanks again to Mr. C and Chili555 (whom i understand won a t-shirt for some obscure reason ...)

---

### Post by Mr. C. on 2007-03-11
That's great news Eniac.

Enjoy the new system,
MrC

---

### Post by keyunfeng on 2007-03-13
Eniac, Mr. C. & Chilli555,

I recently installed Ubuntu (kernel 2.6.17-10-generic) on a system with a Gigabyte GA-M61PM-S2 motherboard with the nVidia MCP61 chipset (nVidia GeForce 6100/nForce 430 chipset) and had the identical problem.  I followed a procedure outlined at [HTML]https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346 [/HTML]and had no success.  I spent countless hours trying to get Ubuntu to recognize my network interface card, but to no avail.  Then I found this thread, followed the procedures, and the problem is solved!!!!!

THANK YOU.

---

### Post by chili555 on 2007-03-13
Thanks for the kind comments. We aim to please!

---

### Post by Eniac on 2007-03-13
I'm glad my solution was useful to you.

Would you happen to have managed to have Ubuntu recognize all the hardware using the MCP61 chipset ? Even though my lan card is working, all of the hardware is listed as "unknown device" and that kind of bugs me.

---

### Post by Mr. C. on 2007-03-13
Nice to know it was useful - thanks for the feedback.

MrC

---

### Post by headchange on 2007-03-18
Eniac  Eniac is offline  i just gt the same mobo and had the same prob as you did, i dont know if i would suggest it but this is whut i did, i am dual booting fc6 and fiesty, they both find the onboardlan, but fc6 doesnt find the audio until you do the system updates, as of right now i think there is like 300 or so updates, takes forever.  but just wanted to let you know that fiesty has drivers in it, gl

---

### Post by headchange on 2007-03-21
i was just wondering how you got the kernel headers, did you dl them off the repos from a live cd, ad copy them to your sys partition, and then copy the menu.list in the live cd and put it into your sys menu.list editing the hd and partitions, i was just wondering because i wanted to install 6.10 so i could have a stable system instead of alpha, because fiesty finds the nic and so does fc6, but i dont really like fc6 and well as you know feisty is still in alpha thanks alot

---

### Post by chili555 on 2007-03-21
Check here: [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=edgy&release=all)
Pick the package that matches your running kernel and download it. Issue the command:```
sudo dpkg -i linux-headers   <--press TAB, the rest will fill in
```
Everything else will take care of itself.

---

### Post by kraymore on 2007-05-23
Is it safe to assume that under feisty that this motherboard including lan and sound is fully supported ?  

thank you

---

