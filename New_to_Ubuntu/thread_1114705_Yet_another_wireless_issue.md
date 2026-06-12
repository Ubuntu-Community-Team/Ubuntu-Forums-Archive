---
title: "Yet another wireless issue"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by bachinaminuet on 2009-04-03
i know you guys must be getting sick of this question by now but i just can't seem to be able to figure it out!!!

I just recently installed Ubuntu onto my computer in a dual boot scenario with vista. So i am a windows person and have no idea how to use ubuntu.

So my problem is that Ubuntu recognises that i have a integrated wireless card and has tried to set up a driver to make it function properly. However something doesn't seem to be right because the little network icon thingy up on the top of the screen doesn't even pick up my wireless router in the next room. The router isn't the problem cause it works fine in vista but i can't seem to get it to work in ubuntu. Also i noticed that the little wireless network button on my computer, the one that toggles the wireless on and off, didn't even light up and that it doesn't seem to do anything.

If you guys can help i would greatly appreciate it

kind regard

rhys

---

### Post by nothingspecial on 2009-04-03
You need to post what wireless card you have.

type ```
lspci -v
``` in a terminal then post the output here.

---

### Post by hyper_ch on 2009-04-03
you might want to try an alternate "network" manager. I have this far been unhappy with the default one and have used manual configuration until I discovered WICD. WICD works fine - but has problems with roaming IMHO. However you might want to give it a try. See my sig for adding the repo.

---

### Post by Whorehay on 2009-04-03
+1 for [**_[COLOR="Red"]WICD[/COLOR]_**]("http://en.wikipedia.org/wiki/Wicd_%28Linux_Network_Manager%29").  In my experience it's been more reliable than NetworkManager.

---

### Post by porchrat on 2009-04-03
I didn't know about wicd. Thanks for the tip.

I have been having issues with getting a broadcom laptop wifi module to connect, it associated with the AP, but never seems to be able to get the ESSID from network manager. I always end up giving it the ESSID through the console and bringing it up and down repeatedly to get it to connect. This may be just the answer I was looking for.

Thanks :)

> **bachinaminuet said:**
> i know you guys must be getting sick of this question by now but i just can't seem to be able to figure it out!!!

I just recently installed Ubuntu onto my computer in a dual boot scenario with vista. So i am a windows person and have no idea how to use ubuntu.

So my problem is that Ubuntu recognises that i have a integrated wireless card and has tried to set up a driver to make it function properly. However something doesn't seem to be right because the little network icon thingy up on the top of the screen doesn't even pick up my wireless router in the next room. The router isn't the problem cause it works fine in vista but i can't seem to get it to work in ubuntu. Also i noticed that the little wireless network button on my computer, the one that toggles the wireless on and off, didn't even light up and that it doesn't seem to do anything.

If you guys can help i would greatly appreciate it

kind regard

rhys

My network light doesn't light up either, it isn't reliable to use that as an idicator of whether or not the thing is working.

I think we do need to know what network card you have. Another way to do it is to open the terminal (go to Applications --> Accessories --> Terminal) and type this into it:

```
lshw -C network
```
then copy and paste the results here for us.

You may find that the driver Ubuntu setup for you is not working, it happens sometimes.

Also another useful command is "ifconfig". If you type that into a terminal it will tell you what network devices are currently running on your machine. Even better is "iwconfig" which is a more wireless-specific command that will tell you the MAC address of the access point (router), the ESSID etc.

---

### Post by azmo35 on 2009-04-03
Hi,i don't know if this help in any way but when i install my ubuntu, this drive BROADCOM B43 WIRELESS DRIVER comes up but didin't install for my frustration and after a couple of hours i plug the cable to my laptop, in secunds i have the driver install and wireless even the light switch is working,maybe this help in any way.

---

### Post by porchrat on 2009-04-03
> **azmo35 said:**
> Hi,i don't know if this help in any way but when i install my ubuntu, this drive BROADCOM B43 WIRELESS DRIVER comes up but didin't install for my frustration and after a couple of hours i plug the cable to my laptop, in secunds i have the driver install and wireless even the light switch is working,maybe this help in any way.

Weird...I also run a B43 and I have endless trouble with it, I'm thinking of moving over to ndiswrapper as the range on my laptop with those Ubuntu drivers is shockingly bad.

Anyway let us not hijack this persons thread, there is a problem that needs to be dealt with. If my problem continues I will start a thread for my broadcom issue anyway.

---

### Post by bachinaminuet on 2009-04-06
Hey guys thanks for all the replies, i wasn't expecting so many replies so quickly...been doing anatomy study so haven't had time to respond but finished exam so now can focus on getting ubunt working properly and stop having to use vista.

I had an idea that maybe i should put the newer Ubuntu version onto the system so i removed 8.04 and put 8.10 but still didn't work! Does it make any difference which version i have and which one should i keep on?

**Anyway, i put lspci -v based on nothingspecial's request and received:**

06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 
	Subsystem: AMBIT Microsystem Corp. Device 0428 
	Flags: fast devsel, IRQ 19 
	Memory at 94100000 (64-bit, non-prefetchable) [disabled] [size=64K] 
	Capabilities: <access denied> 
	Kernel modules: ath_pci 

i pulled what looked like the wirless network part...i could be wrong though!

**I put lshw -c network based on porchrat and received**:
*-network               
       description: Ethernet interface 
       product: NetLink BCM5906M Fast Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1b:38:74:71:8f 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: f2:73:c9:9c:ad:83 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 

**and even put iwconfig and received:**
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

hope that makes more sense to you guys than to me cause i have no idea what it all means!

**and hyper_ch i can't see where in your signature it talks bout WICD, should i put the program on?**

Kind regards
rhys

---

### Post by lkraemer on 2009-04-07
bachinaminuet,
You have two ways to proceed.
1.  Install the Windows Drivers ??.inf & ??.sys with ndiswrapper,
    assuming that ndiswrapper is installed, or that you want to use 
    this method.
2.  Download the madwifi software and use it to get the Atheros AR242x
    working.

Open a Terminal window and do the following:
```

ndiswrapper -l
iwconfig
lsmod


``` 
Then post all of the output from these commands.

Next, decide what method you want to use.

You should be able to search the forum for "HOWTO: & AR242x"
and find a guide for installing your Wifi for your version
of Ubuntu.

lkraemer

---

### Post by twistedvision24 on 2009-04-07
This is right out of the Ubuntu pocket guide from the Free Beginners Guide sticky. 

TIP      If  you&#8217;re  faced  with  non&#8208;working  wireless,  you  might  try 
installing  the  linux&#8208;backports&#8208;modules&#8208;intrepid  package,  if 
using  Ubuntu  8.10,  or  linux&#8208;backports&#8208;modules&#8208;hardy,  if  using 
Ubuntu  8.04  (reboot  after  installing).  If  that  doesn&#8217;t  fix  it,  you 
might  consider  using  Ndiswrapper.  This  is  a  hardware  driver  that 
lets  you use  Windows wireless  drivers  under  Linux. I  wrote about 
Ndiswrapper  in  my  book  Ubuntu  Kung  Fu.  You  can  read  the 
relevant  extract  by  visiting  the  Ubuntu  Kung  Fu  website: 
[www.ubuntukungfu.org/ndiswrapper.html](www.ubuntukungfu.org/ndiswrapper.html).

---

### Post by clive littlewood on 2009-04-07
Hi

Just a thought, my wife's laptop has the same chipset with the Atheros wifi card.

I have had many problems trying to get wireless to work with this card over mant moths of searches (Hundreds of threads) but ended up having to revert to Vista.

Yesterday I installed Jaunty Beta and wireless worked out of the box.

Bye Bye Vista            :lolflag:

Regards

Clive

---

### Post by hyper_ch on 2009-04-07
> **bachinaminuet said:**
> **and hyper_ch i can't see where in your signature it talks bout WICD, should i put the program on?**

there's just one link in my signature ;)

---

### Post by bachinaminuet on 2009-04-07
that'll teach me to read i didn't see the word link...my bad!

i'll try loading jaunty and see if my wireless works...is there much difference between the operating systems. ie. between 8.10 and jaunty?

---

### Post by clive littlewood on 2009-04-07
Hi

I'm now jealous of my wife.s laptop (Jaunty)

It boots to desktop in about 20 secs seems much snappier than mine(Intrepid) and she,s already a convert after 2 days !!!!

I'm going to wait until the main release and then change.

Hope that your wireless is now working.

Clive

---

### Post by nothingspecial on 2009-04-07
I can tell you how to fix it in intrepid. It may look complicated but just copy and paste.

You are going to compile and install a driver (module) then tell Ubuntu to load it every time you start up.You will need a wired connection.

First get the tools necessary for compiling 

```
sudo apt-get install build-essential linux-headers-$(uname -r)

```

Then download the driver.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```

unpack it

```
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```

get inside it

```
cd madwifi-hal-0.10.5.6*/
```

compile and install it.

```
make
```
```
sudo make install
```

Load it.
```
sudo modprobe ath_pci
```

To make it load every time you boot you need to edit a file that ubuntu looks at when it starts to see which drivers it should load. Open that file with a text editor.

```
gksudo gedit /etc/modules
```

go to the end of that file and type ```
ath_pci
``` there so that it is the last line. Do not change anything else.

Save 
Close
Reboot

That`s it your done :p

Do not delete the madwifi folder. When you get a new kernel you will have to put the driver back in. Dead easy.


```
cd madwifi-hal-0.10.5.6*/
```
```
make clean
```
```
sudo make install
```

---

### Post by bachinaminuet on 2009-04-08
WHAT...NO WAY! i have working wireless internet on Ubuntu, goodbye vista!!

Thank you so much, your help was greatly appreciated. This is my first reply using ubuntu, how exciting!

thanks

---

