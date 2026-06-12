---
title: "upgrade broke wireless driver"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by zero7404 on 2008-10-15
i'm running 8.1, and i went ahead and did a 'sudo apt-get upgrade' after a fresh installation of ubuntu. after the restart i cannot use the wireless anymore, not sure if there is a command i need to use to activate the driver. under the network icon in the panel, it does not show any wireless networks.

when i do an 'lshw -C network' i find that the network device that used to be my wireless connection is listed as disabled.

if you need me to post more info, let me know and i will boot up into ubuntu to get it and post back here.

anyone else have this problem as well ?

---

### Post by Mattias Mirhagen on 2008-10-16
I also get this...

  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a3:a1:cb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

Kind of annoying, really. Anyone knows how to fix this?

---

### Post by Santtu Pikkarainen on 2008-10-16
I have exactly the same problem. Yesterday I dropped Windows and installed Ubuntu 8. WLAN worked fine at first shot, but after the upgrade and a reboot no more WLAN.... I wonder how to solve it.

---

### Post by K.Mandla on 2008-10-16
> **zero7404 said:**
> i'm running 8.1, and i went ahead and did a 'sudo apt-get upgrade' after a fresh installation of ubuntu. after the restart i cannot use the wireless anymore, not sure if there is a command i need to use to activate the driver. under the network icon in the panel, it does not show any wireless networks.

when i do an 'lshw -C network' i find that the network device that used to be my wireless connection is listed as disabled.

if you need me to post more info, let me know and i will boot up into ubuntu to get it and post back here.

anyone else have this problem as well ?
When you say Ubuntu 8.1, do you mean Ubuntu 8.10? If so, then you're using incomplete software that is likely to break. 

Can you confirm which version of Ubuntu you're using?

---

### Post by jahLux on 2008-10-16
> **zero7404 said:**
> i'm running 8.1, and i went ahead and did a 'sudo apt-get upgrade' after a fresh installation of ubuntu. after the restart i cannot use the wireless anymore, not sure if there is a command i need to use to activate the driver. under the network icon in the panel, it does not show any wireless networks.

when i do an 'lshw -C network' i find that the network device that used to be my wireless connection is listed as disabled.

if you need me to post more info, let me know and i will boot up into ubuntu to get it and post back here.

anyone else have this problem as well ?
Automatic wireless connectivity has been 'broken' in the latest update. 
My suggestion - use a wired connection until the next upgrade offering and see then if it's corrected.
Welcome to the world of BETA software.

---

### Post by Jackie999 on 2008-10-16
Not sure if this is any help at all..having said that...I've been running intrepid for a few weeks now.  With every kernel update I have to remake the driver, since the driver for my usb antenna (rt2870) isn't native.

Each update I do these steps in the driver folder:
1) sudo make clean
2) sudo make
3) sudo make install
4) sudo modprobe <drivername>
I give it a few minutes and it asks me for my keyring pw and I'm back online.

I wasn't sure from your post if your driver is native or not.  I would think if it's a native drive these steps aren't necessary.

Also, if you're running intrepid (8.10), you should post in the intrepid forum.

---

### Post by zero7404 on 2008-10-16
> **jahLux said:**
> Automatic wireless connectivity has been 'broken' in the latest update. 
My suggestion - use a wired connection until the next upgrade offering and see then if it's corrected.
Welcome to the world of BETA software.

this is what i figured. but i think i will wait around until 8.10 becomes an official release before i choose to reinstall it. until then, ubuntu has been banished from my system....

i know that installing and administering linux systems on a desktop require both an interest and desire to work in a different manner than windows or os x, which is entertaining to some extent....until i get lost in the nonsense that different commands have different formats and different switches. you cannot apply a logic or commonality between 2 different command line commands (as you can in MS-Dos).

let's see what happens @ the end of the month....

---

### Post by coolbrook on 2008-10-16
I just updated my kernel from 2.6.24-19 to 2.6.24-21 and my wireless broke.  So I went into synaptic and removed instances of 2.6.24-21-generic, rebooted and went into the old kernel.  I had wireless again.

I went into synaptic and downloaded the "restricted modules" for 2.6.24-21 and then also re-installed the removed instances.  I rebooted and my wireless is working with my update.

> **jahLux said:**
> Automatic wireless connectivity has been 'broken' in the latest update.

That's news to me. One of my system's wireless worked out of the box with the beta while it needed ndiswrapper and the windows driver to work in the past.

---

### Post by zero7404 on 2008-10-16
> **K.Mandla said:**
> When you say Ubuntu 8.1, do you mean Ubuntu 8.10? If so, then you're using incomplete software that is likely to break. 

Can you confirm which version of Ubuntu you're using?

the beta i downloaded last week and created an image with it.
to varying degrees, i've seen both stability and kernel panic, before and after updates and upgrades.

i've also experienced loud beeping and weird screens during some boot ups, i've also seen screen color flashed on shut down. not sure what all that's about....

i do respect that linux is a machine language that can be tailored to anything, but it's still got quite a bit of catching up to do before it can be reliably installed onto most desktops by novices.

perhaps there is a power-user manual or doc online that will take me thru the steps i can use to manually and individually install the contents of the OS ? this might help me understand it better...

---

### Post by K.Mandla on 2008-10-18
> **zero7404 said:**
> the beta i downloaded last week and created an image with it.
to varying degrees, i've seen both stability and kernel panic, before and after updates and upgrades.

i've also experienced loud beeping and weird screens during some boot ups, i've also seen screen color flashed on shut down. not sure what all that's about....

i do respect that linux is a machine language that can be tailored to anything, but it's still got quite a bit of catching up to do before it can be reliably installed onto most desktops by novices.

perhaps there is a power-user manual or doc online that will take me thru the steps i can use to manually and individually install the contents of the OS ? this might help me understand it better...
You might start with a stable and complete version before you pronounce it uninstallable by newcomers. My mother installed Ubuntu 8.04 on a laptop by herself, and she is by no stretch of the imagination a computer genius. But then again, she didn't grab an incomplete version and suddenly decide Ubuntu has some "catching up to do." 

Try again with a complete release, or wait a week for 8.10 to be finalized. In the mean time, expect incomplete software to have incomplete results. But please don't tell us it's unusable, because you're judging it before it's ready.

---

### Post by pelm on 2008-10-18
#coolbrook

What 'instances' did you remove and reinstall? Curious because even my wireless broke when updating to the new kernel (2.6.24-21). As in this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284308"). With the old kernel it works as usual.

---

### Post by zero7404 on 2008-10-18
> **K.Mandla said:**
> You might start with a stable and complete version before you pronounce it uninstallable by newcomers. My mother installed Ubuntu 8.04 on a laptop by herself, and she is by no stretch of the imagination a computer genius. But then again, she didn't grab an incomplete version and suddenly decide Ubuntu has some "catching up to do." 

Try again with a complete release, or wait a week for 8.10 to be finalized. In the mean time, expect incomplete software to have incomplete results. But please don't tell us it's unusable, because you're judging it before it's ready.

thanks for the kind words....
betas have their drawbacks, but also contain the latest modules. this is why i started with the beta.

---

### Post by JustTCO on 2008-10-18
> **Mattias Mirhagen said:**
> I also get this...

  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:a3:a1:cb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg

Kind of annoying, really. Anyone knows how to fix this?


hi, i didn't read all the post but this interested me, because a run the command and to me that show:
```

  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=24 mingnt=3

```
UNCLAIMED!?!?! how??

So the history is like this... i update ubuntu from kernel 2.6.24-19-generic to  2.6.24-21-generic... after the upgrade change menu.lst i saw that a still have instaled old kernel so i search in cache for the name linux imagem to know the correct name to remove it. At this time i saw the linux-image-2.6.24-21-386 and install it.. after that my sound card and my wireless card became disabled... the sound card is already reinstaled... but the wireless can't...

so someone could help me?:confused::confused:

---

### Post by zero7404 on 2008-10-21
> **pelm said:**
> #coolbrook

What 'instances' did you remove and reinstall? Curious because even my wireless broke when updating to the new kernel (2.6.24-21). As in this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284308"). With the old kernel it works as usual.

sorry i missed your question, i went into synaptic and removed the network manager framework and tried to reinstall it, but unsuccessful. i decided to start with a clean slate and reinstall ubuntu.

but it looks like the wireless is still buggy even after today's updates installed. rarely it connects automatically on the first  attempt...

i noticed that under network connections, it created an 'Auto dlink07' which is my network. i delete that and try establishing a connection again and it seems to work.

how do i stop ubuntu from remembering my network and auto-connecting to it when i start up ?

---

### Post by karlatsaic on 2008-10-21
My iwl3945 driver works perfectly on a Dell l XPS M1330, under ubuntu 8.04. That release is supported for 2.5 more years. I will wait until Intrepid settles in and browse the forums for bugs before I even consider moving away from 8.04, or until 8.10 has something I really need. I would recommend not putting a beta version on anything other than a machine you may wish to play around with - and certainly would not advise any newcomer to even consider a pre-release 8.10. The reason ubuntu is so great is its stability, as long as you grab a stable release.

[EDIT: also, information for newecomers, is that LTS versions such as 8.04 continue with upgrades to all major software components. As an example, a daily update to my 8.04 base also installed the 2.6.24-21 kernel. And nothing broke - my iwl3945 wifi connections are still solid.]

---

### Post by karlatsaic on 2008-10-21
> **zero7404 said:**
> ... i decided to start with a clean slate and reinstall ubuntu. but it looks like the wireless is still buggy even after today's updates installed. rarely it connects automatically on the first  attempt...

If you're willing to do a clean install, why not try a clean install of 8.04? Note that you will get the latest kernel and modules after you run an update (above you said you wanted the beta because you want the latest modules). This way you will get the latest linux kernel and ubuntu-supplied modules, which are more likely to work with the stable Hardy LTS release (8.04).

---

### Post by zero7404 on 2008-10-22
> **karlatsaic said:**
> If you're willing to do a clean install, why not try a clean install of 8.04? Note that you will get the latest kernel and modules after you run an update (above you said you wanted the beta because you want the latest modules). This way you will get the latest linux kernel and ubuntu-supplied modules, which are more likely to work with the stable Hardy LTS release (8.04).

it's because in a week or so, 8.1 will be finalized, so what's the use of downloading and burning an image of the previous version OS....either way it will get patched to the latest version, so i thought starting with the newer platform would be better. despite the bugs.

---

### Post by rienk on 2008-10-22
Hi there,

Reading this thread, because having the same issue.
Only for me my wireless worked with 8.10 until kernel 2.6.27-6-generic.
After updat to 2.6.27-7 it stopped working.
Read something in launchpad, that sometimes if you have a partial update it stops working. when doing "aptitude update && aptitude full-upgrade"
it worked again. (Bug #284089).[https://bugs.launchpad.net/ubuntu/+bug/284089]("https://bugs.launchpad.net/ubuntu/+bug/284089")

/Rienk

---

### Post by coolbrook on 2008-10-23
> **pelm said:**
> #coolbrook

What 'instances' did you remove and reinstall? Curious because even my wireless broke when updating to the new kernel (2.6.24-21). As in this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/284308"). With the old kernel it works as usual.
Anything that had both "2.6.24-21" and "generic" in the same filename.  In my case I have the generic kernel to handle my SMP system.

---

### Post by zero7404 on 2008-10-27
one thing i should note is that when this connection issue happens to me, the password window pops up again asking for the network key, however it's not the same key that i input, it's longer and doesn't match with my key. sometimes this works fine, other times it doesn't.

weird.

---

