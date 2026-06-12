---
title: "MY THIRD THREAD: Please help me. Can't connect to wifi..."
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by Soglad on 2007-11-04
Hello everyone, this is my third thread about this problem and NOBODY has bothered helping me. I'm really frustrated with this problem as I really need this wifi and I can't find anything on how to fix it...

I'm using a Compaq Presario c700 with Broadcom 4311 wifi drivers.

I have the drivers installed and the wifi is showing as being on. I have tried multiple way to connect to a local wifi connection to no avail! I've tried roaming, I've tried multiple ways in manual mode.

when I try connecting ANY way I only get the two dots trying to connect forever.

When I do a "sudo iwlist scan", I get:

```
phil@belkin54g:~$ sudo iwlist scan
[sudo] password for phil:
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      No scan results

```

Anyone know what the friggin' problem is?! Thanks!

:D

---

### Post by Martje_001 on 2007-11-04
Hmmm.. I can't help you here, but why you're not connecting with a cable?

---

### Post by Soglad on 2007-11-04
I am using cable now, but very inconvenient for the people I live with to have wire going trough house.

Need wifi big time.

---

### Post by Soglad on 2007-11-04
bump

---

### Post by abh83 on 2007-11-04
I'm no pro but what do u see when typing this command in the terminal: "lshw -C network" ?

---

### Post by Soglad on 2007-11-04
I get:

[B]phil@belkin54g:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:00:00:1a:73:98
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 10
       serial: 00:1b:38:7a:f8:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.5 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
[/B]

---

### Post by abh83 on 2007-11-04
Looks fine to me. Its actually quite identical to mine accept for the fact that I use a different wifi card. One thing is certain though, Ubuntu recognises your wifi card! But as I said I'm no pro. I've gained a bit of experience trying to fix my own network issues this past week. There seems to be some network bug in gutsy. You might want to install ur own wifi drivers via ndiswrapper. I found this to help quite often! You'll find plenty of HowTos on this forum.

---

### Post by abh83 on 2007-11-04
This might be of use:

[http://ubuntuforums.org/showthread.php?t=563547&highlight=howto+ndiswrapper](http://ubuntuforums.org/showthread.php?t=563547&highlight=howto+ndiswrapper)

[http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+ndiswrapper](http://ubuntuforums.org/showthread.php?t=405990&highlight=howto+ndiswrapper)

---

### Post by Soglad on 2007-11-04
I do have drivers that are with this laptop, but I'm not sure how to manually install them...any ideas?

---

### Post by kevdog on 2007-11-04
You can use the bcm43xx restricted drivers, if you want buy you need additional files to use this driver.  so you either need the following:

#1 - A wired ethernet connection to download and install the additional files

#2 - Download the firmware:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

And install it with the bcm43xx cutter tool
[http://linuxwireless.org/download/bcm43xx/fwcutter/bcm43xx-fwcutter.tar.bz2](http://linuxwireless.org/download/bcm43xx/fwcutter/bcm43xx-fwcutter.tar.bz2)

I obtained these drivers from the following site:
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by Soglad on 2007-11-04
I've done all that...

The driver are working...the light's turning on and off etc.

I just can't seem to connect to anything....any way..

---

### Post by kevdog on 2007-11-04
What shows with

iwlist scan

---

### Post by Soglad on 2007-11-04
What I posted at the start, which is:

```
phil@belkin54g:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      No scan results

```

---

### Post by kevdog on 2007-11-04
Are you sure you installed the restricted bcm43xx drivers appropriately??

lsmod | grep bcm

---

### Post by abh83 on 2007-11-04
> **Soglad said:**
> I do have drivers that are with this laptop, but I'm not sure how to manually install them...any ideas?

didn't u get a driver cd along with ur system?

btw. i seemed to have solved my network issues by simply assigning a new (internal) ip address to my computer. You might wanna check ur router's settings (if u use one that is:D )

---

### Post by compwiz18 on 2007-11-04
What does ```
sudo iwlist scan
``` give you?

---

### Post by Soglad on 2007-11-04
I've posted what that gives me twice now if you read the thread.

"lsmod | grep bcm" gives me:

```
phil@belkin54g:~$ lsmod | grep bcm
bcm43xx               127336  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              35656  2 bcm43xx,ieee80211softmac

```

---

### Post by fvds on 2007-11-04
Is your notebook equipped with a switch to turn wlan on and off? Is it in the on position?

---

### Post by kevdog on 2007-11-04
You have a revision 2 4311 chipset -- Look at your lshw -C network statement.  This is what is states directly on the bcm43xx website:

> supported

    * bcm4303 (802.11b-only chips)
    * bcm4306
          o all newer revisions supported (built after about Jan 2005)
          o old revisions partially supported. Lacks some features like hw-crypto. 
    * bcm4311 rev 1 / bcm4312
    * bcm4318 

unsupported

    * The 802.11a part of the 4309 and 4312 is not supported.
    * bcm4311 rev 2
    * There is no support for any Draft 802.11n features.

Obviously ubuntu isnt smart enough to figure out your chipset is not supported

May want to try another approach -- bail on the bcm43 driver and go with ndiswrapper.  Thats your only available option.

---

### Post by Soglad on 2007-11-04
> **kevdog said:**
> You have a revision 2 4311 chipset -- Look at your lshw -C network statement.  This is what is states directly on the bcm43xx website:



Obviously ubuntu isnt smart enough to figure out your chipset is not supported

May want to try another approach -- bail on the bcm43 driver and go with ndiswrapper.  Thats your only available option.

Ok thanks!

Any links or howtos? I'm really out of my league here!

---

### Post by kevdog on 2007-11-04
Look at the bottom of the thread in my signature dealing with command line connection.  I think Jame Jackson has written a good tutorial.  There is a link at the bottom of that thread.

---

### Post by Soglad on 2007-11-04
Erm, that HowTo for the Ndiswrapper is asking for .sys and .inf files....I've only .exe drivers......what's going on here?

---

### Post by kevdog on 2007-11-04
Read the thread - The .exe is probably a self extracting cab file or zip file.  Its probably easiest to open the .exe file on windows and then copy the .sys and .inf files and transfer them to ubuntu.  There are other methods.

Or you could download the winxp drivers from the manufacture's website (probably the preferred solution since you get the latest drivers).

---

### Post by drs305 on 2007-11-04
Soglad,

I am in the exact situation as you. I have the 4311 rev 2 Broadcom card with the same symptoms. I just went to the link kevdog provided and got my card working in just a few minutes.

thanks kevdog.

No offense, but I thought giving you the link you really need to go to would be easier than tracking it down in another link. Here it is:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)   Then click on the "BCM43xx HowTo" Link. Giving you this link will let you take the poll.

Good luck!

---

### Post by Soglad on 2007-11-04
> **drs305 said:**
> Soglad,

I am in the exact situation as you. I have the 4311 rev 2 Broadcom card with the same symptoms. I just went to the link kevdog provided and got my card working in just a few minutes.

thanks kevdog.

No offense, but I thought giving you the link you really need to go to would be easier than tracking it down in another link. Here it is:
[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)   Then click on the "BCM43xx HowTo" Link. Giving you this link will let you take the poll.

Good luck!

Woohoo!!! That worked straight away!!

THANK YOU!!!!

I love you and want to have your babies!!

haha

Thanks again!

Dav.

---

