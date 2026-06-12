---
title: "Installing madwifi"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Cleanville on 2011-01-08
Installing madwifi for the atheros type wireless connection is gigantically complicated for someone who wants to be a new LINUX  user.  I have literally spent days trying to get madwifi going so that I  can connect wireless (can't go back to WINDOWS on this machine even if I  wanted to -- thanks, GRUB!!!).

Here is my question:

WHY is it so difficult to install madwifi?

Why is it not in the Software center?

Do the developers have any idea how many people are having the problems I am?

what is the deal here? 

and finally, lets be clear here:  I am not looking for instructions on how to install madwifi.  i have tried many sets of directions previously posted and none of them work.  I have gotten over some hurdles, like getting "build-essential" on my machine (impossible to do without being connected to the Internet in case you were wondering).  But that is not my question.  What I am asking here is a different question.  What I am asking here is WHY they made it so difficult to install madwifi.

---

### Post by nothingspecial on 2011-01-08
Installing the madwifi drivers is not difficult.
[B]
edit - insults removed so objections removed - edit[/B]

You shouldn`t even need to install them with the last 3/4 ubuntu versions.

What is your wireless card?

Post the output of
```

sudo lshw -C network
```Have you tried getting a wired connection and looking in System > Administration > Additional Drivers?

---

### Post by philodice on 2011-01-08
Try the distro 9.10.  Never had any problems, everything just worked.

---

### Post by Cleanville on 2011-01-08
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:99:ee:e2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.122 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:f0200000-f023ffff ioport:a000(size=128)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2c:5a:10:7c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by nothingspecial on 2011-01-08
First try updating with a wired connection. Then the additional drivers.

Then try installing the b43-fwcutter package.

---

### Post by Cleanville on 2011-01-08
> **nothingspecial said:**
> Installing the madwifi drivers is not difficult.
[B]
edit - insults removed so objections removed - edit[/B]

You shouldn`t even need to install them with the last 3/4 ubuntu versions.

What is your wireless card?

Post the output of
```

sudo lshw -C network
```Have you tried getting a wired connection and looking in System > Administration > Additional Drivers?

Thank you for the help.  After three days of struggle I am now connected wirelessly.

Before I marked this as "solved" I will attept to answer my own question (feel free to correct me if I have it wrong):

The reason that it is so difficult to connect wirelessly thru UBUNTU on a machine with an Atheros type network card is because there is a company called Broadcom that is not playing by the rules that the UBUNTU community has established.  However, Broadcom and UBUNTU have struck a compromise where the necessary software, while not available in the WUBI and .iso versions of UBUNTU, can be downloaded thru the "additional drivers" command, with appropriate cautions about the fact that Broadcom has not played by UBUNTU's rules.  This is bewildering to new users, but it is basically the fault of the executives at Broadcom and Atheros.

Is that it?

---

### Post by nothingspecial on 2011-01-08
> **Cleanville said:**
> Thank you for the help.  After three days of struggle I am now connected wirelessly.

Before I marked this as "solved" I will attept to answer my own question (feel free to correct me if I have it wrong):

The reason that it is so difficult to connect wirelessly thru UBUNTU on a machine with an Atheros type network card is because there is a company called Broadcom that is not playing by the rules that the UBUNTU community has established.  However, Broadcom and UBUNTU have struck a compromise where the necessary software, while not available in the WUBI and .iso versions of UBUNTU, can be downloaded thru the "additional drivers" command, with appropriate cautions about the fact that Broadcom has not played by UBUNTU's rules.  This is bewildering to new users, but it is basically the fault of the executives at Broadcom and Atheros.

Is that it?

Sort of.

Broadcom do better than some in that they do provide drivers for linux.

However, these drivers are not open and therefore cannot be tested or improved. So ubuntu cannot include them by default.

I hope you don`t have a lexmark printer.

---

### Post by 3rdalbum on 2011-01-08
> **Cleanville said:**
> 
WHY is it so difficult to install madwifi?

Why is it not in the Software center?

Do the developers have any idea how many people are having the problems I am?

what is the deal here?

Madwifi is a set of drivers for Atheros wifi chipsets. The developers expect that the people who make distributions like Ubuntu will install Madwifi into the distribution, so users won't have to. Indeed, Ubuntu contains Madwifi drivers. That's why it's not in the Software Center - it's included.

I don't know if the Madwifi developers think that new users are going to try and compile the drivers and have problems. I'm sure they assume that their drivers are going to be compiled by distro developers.

The deal here is that you've been trying to install a driver for an Atheros wifi device, yet you don't seem to have one. Your wifi card's chipset is made by Broadcom:

```
*-network 
description: Network controller
product: BCM4312 802.11b/g LP-PHY
vendor: Broadcom Corporation
```

(it's wifi because it mentions "b/g" which are two protocols for wifi).

You do have an Atheros networking device, but it's your Ethernet port:

```
*-network
description: Ethernet interface
product: AR8132 Fast Ethernet
vendor: Atheros Communications
```

Getting your wifi working is actually a lot easier than what you've been trying. Connect your computer to the router via an Ethernet port (or through some other means, such as a mobile broadband stick). Go to System > Administration > Synaptic Package Manager. Type your password if prompted. Click the Reload button to make sure you have the list of packages from the Ubuntu repositories.

Now close Synaptic and go to System > Administration > Additional Drivers (Hardware Drivers on 10.04 and earlier) and the program will offer to install a driver or firmware or something for you. Let it do its work, and at the end of it all you should be able to get a connection on wifi. If not, then try shutting down completely and then starting up again.

---

### Post by Cleanville on 2011-01-08
> **nothingspecial said:**
> Sort of.

Broadcom do better than some in that they do provide drivers for linux.

However, these drivers are not open and therefore cannot be tested or improved. So ubuntu cannot include them by default.

I hope you don`t have a lexmark printer.

lol.  

That is what torpedo'd my attempt to go UBUNTU back in 2007.

Back in 2002, when I attempted to go LINUX, the problem was floppy drives and monitors.

Hopefully I am on board now.

---

### Post by howefield on 2011-01-08
> **Cleanville said:**
> (can't go back to WINDOWS on this machine even if I  wanted to -- thanks, GRUB!!!).

Hi and welcome to the forums, nice to see you sorted within 30 minutes with the help of nothingspecial.

As an aside, nothing about Grub would stop you installing a different operating system. I hope you can continue to use Ubuntu and wish you well with it, but you aren't stuck with it.

---

### Post by nothingspecial on 2011-01-08
I think the problem is that, for years, compiling the madwifi drivers was the solution.

So your wireless doesn`t work and you consult uncle google.

He tells you to compile the madwifi drivers, when all you have to do is enable them in Additional Drivers.

Maybe Ubuntu should offer an option, by way of a pop up window thingy, rather than expect new users to find it.

---

### Post by Cleanville on 2011-01-08
> **howefield said:**
> Hi and welcome to the forums, nice to see you sorted within 30 minutes with the help of nothingspecial.

As an aside, nothing about Grub would stop you installing a different operating system. I hope you can continue to use Ubuntu and wish you well with it, but you aren't stuck with it.


No, technically the problem is that when doing an UBUNTU single OS install it wipes out the windows loader, which renders the ACER windows erecovery disks useless (and, yes, it was a lot of hours of work to figure that out).  yes, you can get the windows loader online, but, no it won't work with the recovery disk type reinstall.

I didn't want to do a single UBUNTU OS install, but you can't connect a Broadcom type machine wirelessly thru the WUBI installation and I thought an iso install would help (because build-essential would be on the CDROM).  Sadly the iso install would not work for dual boot as far as the partitioning, so I did an UBUNTU single OS install.  Then I couldn't "Add CDROM" anyway, so I couldn't get build-essential because the machine was not connected.  Obviously, I did eventually move the machine to a wired connection (another hour of work), but the point is that if someone tries to install UBUNTU on a Broadcom wireless card type machine, without having a wired connection, it is basically impossible.  This kind of thing is very frustrating to new users, even ones with a fair amount of computer experience.  However, I understand that it is Broadcom's fault.  I deal with Microsoft in my job in the real world and I know how these companies can be.

---

### Post by nothingspecial on 2011-01-08
The build-essential package is a meta-package that installs various packages required for building code from source.

You didn`t actually need them.

Again, and I feel sorry that you have been put in this situation, the problem is that google led you to an outdated solution. Ubuntu should address this imo.

---

### Post by Cleanville on 2011-01-08
> **nothingspecial said:**
> I think the problem is that, for years, compiling the madwifi drivers was the solution.

So your wireless doesn`t work and you consult uncle google.

He tells you to compile the madwifi drivers, when all you have to do is enable them in Additional Drivers.

Maybe Ubuntu should offer an option, by way of a pop up window thingy, rather than expect new users to find it.

The real problem is that in order to connect wirelessly with a Broadcom type wireless setup you have to be connected through a wire to get the things you need to get to connect wirelessly.

That is the answer I needed.  Not criticizing, but that is what I needed to know three days ago.

btw, I can't figure out how to mark this thd as "solved"

---

### Post by nothingspecial on 2011-01-08
> **Cleanville said:**
> The real problem is that in order to connect wirelessly with a Broadcom type wireless setup you have to be connected through a wire to get the things you need to get to connect wirelessly.


Yep, that`s it in a nutshell.

Click the thread tools thingy at the top of the page.

---

### Post by lokihound on 2012-09-05
How do I install madwifi if I can't connect hard wired.  I have no way to do this - no Ethernet card!  I have another computer - so why can't I just download something and put it on a USB or floppy?

---

### Post by lokihound on 2012-09-05
Well I was being stupid - and the interface was not exactly compliant.  I was going into Network Connections dialog box (where you can put in settings and such for all your networks), but instead should have clicked on the icon that looks like two arrows= one up and one down to access the wireless networks - and mine was there.  No need to get the madwifi thing - and am I glad as it seems way too complicated for me at this particular time!  Oh - and I'm using XUbuntu - so the interface is a bit different.

---

