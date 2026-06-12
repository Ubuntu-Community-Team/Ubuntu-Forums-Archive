---
title: "Acer Wireless problem"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by rcdeacon on 2006-12-19
I have a Acer Aspire laptop 5002 WLMi which I cannot get to connect to the internet using the live cd. It has a broadcom network adapter.Can anyone assist in resolving this problem. If someone can lead me to some clear concise instructions I would appreciate it greatly.

---

### Post by dynamicdude on 2007-02-23
Can anyone this guy please so that i can help myself as well..
it is acer that sucks i wont buy any product from acer again in my life.....

---

### Post by steveferson on 2007-05-11
Hey, but of a Linux n00bie here trying to install Ubuntu 7.04.

Trying to get the wireless working on my Aspire 5002 wlmi.  I'm using the Live version to try and get everything working before I start messing about with a full-install (I still have Windows on my laptop and don't want to risk messing it up)

I read the wireless quickstart in the wiki but where it says to do lshw -C network the response I get is:

```
  ***-network:1 DISABLED**
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 02
       serial: 00:16:ce:8d:c2:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e2000000-e2001fff irq:17

```

It shows up in the Network manager but I can't make the checkbox change into a tick (it's set to a - sign)

From the readout above I'd guess the drivers are already installed.  Is there a simple solution to this or do I have to go down the ndiswrapper route?

---

### Post by steveferson on 2007-05-11
I should add that on trying to follow the advice for using the native drivers, I encounter a problem trying to use the install the fwcutter package.

If I go into the synaptic package manager and search for the fwcutter nothing is found.  If I do ```
sudo apt-get install bcm43xx-fwcutter
``` then it says it can't find the package or something like that.

---

### Post by ghostboy on 2007-05-11
> **rcdeacon said:**
> I have a Acer Aspire laptop 5002 WLMi which I cannot get to connect to the internet using the live cd. It has a broadcom network adapter.Can anyone assist in resolving this problem. If someone can lead me to some clear concise instructions I would appreciate it greatly.

Check out this thread [http://ubuntuforums.org/showthread.php?t=197102]("http://ubuntuforums.org/showthread.php?t=197102") I used these instructions to get wireless on my Acer Aspire 5050.  This thread specifically addresses the issues regarding the Broadcom wireless cards.  They are very clear and concise, and easy to follow.

---

### Post by steveferson on 2007-05-11
Thanks, I've seen that one.  I'm on step 8 at the moment:

> If you are an Acer user, you will need to use the acerhk driver.

Although from what I gather the Acerhk driver has been replaced by acer_acpi, so I'm getting installing that instead.  It takes ages to install all the linux headers or whatever they're called that it needs.

It's the step after this that worries me.

> If it doesn't work, reboot.

As I'm trying to get it going from the Live CD that's obviously not much use if it comes to that.

I've looked up one of the Ubuntu wiki pages (can't remember where it was now) which lists the supported broadcom wireless cards and the 4318 isn't listed, it gives the 4306, 4310 and 4311.  If I have any luck I'll post back but I'm not holding my breath.  Fedora 7 is out in 2 weeks though, so if all else fails I'll give that a go.

---

### Post by steveferson on 2007-05-12
IT WORKS!!

I couldn't get fwcutter to install on the live CD for some reason but I came across [this guide]("http://ubuntuforums.org/showthread.php?t=405990") where someone has taken the firmware from the Broadcom and bundled it with a script to install.  It's probably not completely legal but it seems to work!

---

