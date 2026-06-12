---
title: "Wireless won't work with ubuntu"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by davidwashere2003 on 2009-01-16
hello.

I'm at a loss for why my wireless isn't working.

Some background- I've been a windows user all along till vista came and turned me off windows completely. I've installed Ubuntu 8.10 to a usb hdd and am using it on my laptop because the laptop has a serious problem with the SATA drive (it crashes while trying to boot off the systems hdd). So I fixed that by using a usb drive instead of an internal one. Now the computer doesn't crash. The computer is an Acer Aspire 5520-5739.

The problem I'm having, other than my complete ignorance to linux, is that my wifi won't work or show up as an option under the networking icon on the upper right corner of the GUI.

So far I have installed ndiswrapper and got it set up so it loads on startup. I downloaded and installed drivers that are supposed to be for my specific Atheros AR242x wireless adapter. I disabled the "Support for Atheros 802.11 Wireless LAN cards." by going to System-Administration-Hardware Drivers and clicking deactivate.

I tried a bunch of different steps in the terminal from a few different forums but nothing works.

I may have accidentally setup the wrong driver to load when the computer reboots... netathwx.inf instead of netathw.inf... and I don't know how to fix this. Those two drivers came in the same download, but neither driver seems to make the wireless work anyway, I just noticed on one forum a guy with the same computer as me said the netathw file worked for him.

Any help would be greatly appreciated. I'm definitely out of my element. Here's some info that maybe makes more sense to you than it does to me...

a@a-laptop:~/driver$ ndiswrapper -l
netathw : driver installed
device (168C:001C) present (alternate driver: ath_pci)


a@a-laptop:~/driver$ lshw -c network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: MCP67 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1b:38:73:e4:93
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
*-network
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:05:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ndiswrapper latency=0 module=ndiswrapper
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 5e:13:db:ec:1b:0c
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


a@a-laptop:~/driver$ dmesg | grep -e ndis -e wlan
[ 18.010262] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[ 18.437670] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[ 18.443197] ndiswrapper (link_pe_images:603): DLL initialize failed for athwx.sys
[ 18.443257] ndiswrapper: driver netathwx (,05/20/2008,7.6.0.224) loaded
[ 18.444977] ndiswrapper 0000:05:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[ 18.444987] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver
[ 18.445105] usbcore: registered new interface driver ndiswrapper

If you need any more info let me know. Thanks!

---

### Post by nhasian on 2009-01-16
follow my instructions here for get your wifi up and running:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

---

### Post by davidwashere2003 on 2009-01-16
> **nhasian said:**
> follow my instructions here for get your wifi up and running:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

Thanks I'll try and let you know what happens

---

I am unable to get a wired connection. I have a desktop borrowing a wifi signal from a neighbor. I tried to setup internet connection sharing on my desktop and connect my laptop through a switch to my desktop, but as soon as I turn on internet connection sharing on my desktop, it kills the internet. So, is there something I can download on this computer and then transfer to the laptop via SD card or dvd?

I followed your other steps though and nothing happened... 

iwconfig shows:

lo     no wireless extensions.

eth0   no wireless extensions.

pan0   no wireless extensions.

--- 

oh, one other thing, I tried "sudo vi /etc/modprobe.d/blacklist" but this wouldn't allow me to save the edited blacklist.

I used 'sudo gedit /etc/modprobe.d/blacklist" which allowed me to save the edited list... not sure if that makes a difference.

---

### Post by davidwashere2003 on 2009-01-16
I was looking around and thought to try the *dmesg* command and see if anything interesting came up. I found:

[   18.339124] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   18.339131] ndiswrapper (load_sys_files:206): couldn't prepare driver 'netathw'
[   18.340058] ndiswrapper (load_wrap_driver:108): couldn't load driver netathw; check system log for messages from 'loadndisdriver'

Read the bad magic bit means I must have installed 32 instead of 64 bit drivers... 

How can I remove the drivers?

Also I ran a command somewhere that set up the driver so it would load when ubuntu restarts... how do I make that stop now I know that it's the wrong one?

---

### Post by SunnyRabbiera on 2009-01-16
Just be warned, some wireless is a pain in the @#% with ubuntu, its not our fault though as the manufacturers dont give us the same drivers they do MS

---

### Post by nothingspecial on 2009-01-16
Atheros drivers will work.

Try removing ndiswrapper.

Then go to system > administration > hardware drivers then disable anything in there.

Then ```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver ```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add ```
ath5k
``` To the end of the file 

save
close 
reboot

---

### Post by davidwashere2003 on 2009-01-16
> **nothingspecial said:**
> Atheros drivers will work.

Try removing ndiswrapper.

Then go to system > administration > hardware drivers then disable anything in there.

Then ```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver ```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add ```
ath5k
``` To the end of the file 

save
close 
reboot


Ok, I've run into a problem... I wasn't sure how to uninstall ndiswrapper. I've removed the two things with ndiswrapper in their names it from synaptic package manager.

The problem happens when I try running ```
sudo apt-get install linux-backports-modules-intrepid-generic
```

It comes back

E: Couldn't find package linux-backports-modules-intrepid-generic

I searched for it on the cd, but when i try to run it the box comes up with bold red letters saying:

Error: Dependency is not satisfiable: linux-backports-modules-2.6.27-7-generic

I tried downloading it off the forum and ran it again and got the same error that means nothing to me.

---

### Post by g0rd99 on 2009-01-16
My eeepc has the same wireless chip, and Ubuntu 8.10 loads the drivers in a standard installation. It shows up in both iwconfig, and ifconfig. I still haven't been able to get it to connect though. Network Manager seems to be badly messed up in this edition. Good Luck

---

### Post by davidwashere2003 on 2009-01-16
> **g0rd99 said:**
> My eeepc has the same wireless chip, and Ubuntu 8.10 loads the drivers in a standard installation. It shows up in both iwconfig, and ifconfig. I still haven't been able to get it to connect though. Network Manager seems to be badly messed up in this edition. Good Luck

Yeah still no luck. Can't figure out how I'm supposed to get linux-backports-modules-intrepid-generic to install. 

I can't even get my wireless to show up... it identifies that the hardware does exist in my system, but that's about all it does.

Good luck with your computer... since you can get it in iwconfig and ifconfig at least, you may be closer to a solution than I am.

---

### Post by nothingspecial on 2009-01-16
You need a wired connection. If you`ve not got one I can still help.

 Have you enabled everything in the third party tab in system > administration > software sources?

---

### Post by davidwashere2003 on 2009-01-16
Ok, so I went through the ubuntu cd, reinstalled ndiswrapper. 

Then I was able to install linux-backports-modules-intrepid-generic
I also installed/reinstalled just about every package relevant to my computer/hardware that I could find on the CD.

Ran sudo modprobe ath5k without any errors now.

Ran gksudo gedit /etc/modules
-inserted ath5k
-put hash mark in front of ndiswrapper to ignore it

Restarted computer.

Still no change from my original post... no mention of ath5k... seems ndiswrapper is still running the show and still no wireless even showing up except under 'sudo lshw -c network'

---

### Post by nothingspecial on 2009-01-16
Please forget about ndiswrapper. You don`t need it.

```
sudo apt-get remove --purge ndiswrapper ndisgtk
```

Reboot.

---

### Post by davidwashere2003 on 2009-01-16
> **nothingspecial said:**
> You need a wired connection. If you`ve not got one I can still help.

 Have you enabled everything in the third party tab in system > administration > software sources?

I never saw that before. Ok, so I put a check in each of the two items under Third-Party Software.

When I closed it said something about software being out of date and I need an internet connection.

I reopened it and the checks are still in the two items under Third-Party Software.

---------

I ran...

```
sudo apt-get remove --purge ndiswrapper ndisgtk
```

and the terminal returned with...

```
a@a-laptop:~$ sudo apt-get remove --purge ndiswrapper ndisgtk
[sudo] password for a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
a@a-laptop:~$ 

```

Rebooted

---

### Post by nothingspecial on 2009-01-16
****EDIT******

Some bad advice in this post - now removed

****EDIT****

Go [[COLOR="Magenta"]here[/COLOR]]("http://snapshots.madwifi-project.org/")

Download the 9th link.

Copy it to your Desktop

Extract it 


```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```

If you`ve not got the necessary compiling tools get them

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
Navigate to the madwifi directory

```
cd madwifi-hal-0.10.5.6*/
```

Compile
```

make
```
```
sudo make install
```
Load the driver
```
sudo modprobe ath_pci
```

Make it load every time```


gksudo gedit /etc/modules
```

put a # in front of ath5k 

Add this line to the end of the file

```
ath_pci
```

save
close
reboot

---

### Post by davidwashere2003 on 2009-01-16
Ok, so I followed your steps and everything seemed to work until:

sudo modprobe ath_pci

```
FATAL: Error inserting ath_pci (/lib/modules/2.6.27-7-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

So I went on to write it into startup with gedit as instructed.

Is my ath_pci broken?

---

### Post by nothingspecial on 2009-01-17
Did madwifi install because I forgot to mention to ```
cd Desktop
```first.

---

### Post by davidwashere2003 on 2009-01-17
> **nothingspecial said:**
> Atheros drivers will work.

Try removing ndiswrapper.

Then go to system > administration > hardware drivers then disable anything in there.

Then ```
sudo apt-get install linux-backports-modules-intrepid-generic
```

To load the driver ```
sudo modprobe ath5k
```

To make it load everytime you boot

```
gksudo gedit /etc/modules
```

and add ```
ath5k
``` To the end of the file 

save
close 
reboot


Hi nothingspecial, just wanted to say thank you for your help, and let you know that you're steps were effective in initializing my wireless ability. I can now connect no problems to wireless.

Just an update on the measures I had to take:

I had to format my usb hard drives ubuntu partion and reinstall Ubuntu. 

I then followed you're steps up to the post I quoted in this reply and, once I restarted the computer, my wireless was fully functional and detected wireless networks in my area.

Thanks again for you're help, wouldn't have been able to get it going otherwise! :popcorn:

[B]_A suggestion to anyone that reads this post:_

If your wireless is giving you nothing but problems, perhaps a reinstall is the only viable option. It would have saved me a day of messing around with drivers and code to have done an approximate half-hour format/reinstall.[/B]

---

### Post by jbraswell on 2009-01-31
Ugh, sorry to bring this one back up, but I just got a desktop from System76 yesterday, and I'm still having trouble with wpa wireless.  

In accordance with this thread, I've enabled the 3rd party software, disabled the two network drivers under Administration->Hardware Drivers, downloaded, built, and installed madwifi (Although, nothing really happened when I ran 'modprobe ath5k'; the shell just returned. Should I have seen something else?) I also installed linux-backports...

I then made the change to /etc/modules and rebooted.  However, every time I try to connect to the wireless network, it just tries for a long time and then asks for my password again.    

Any other ideas?  Thanks in advance for any advice.

---

### Post by nothingspecial on 2009-01-31
For madwifi  ath_pci
For linux backports ath5k

As you have both installed comment (place a # infront) of either if you have added both to /etc/modules

---

### Post by jbraswell on 2009-01-31
> **nothingspecial said:**
> For madwifi  ath_pci
For linux backports ath5k

As you have both installed comment (place a # infront) of either if you have added both to /etc/modules

Argh, sorry, I thought I had subscribed to this thread, but I hadn't.  I figured there was no response so I just made this one: [http://ubuntuforums.org/showthread.php?t=1056423](http://ubuntuforums.org/showthread.php?t=1056423)

---

