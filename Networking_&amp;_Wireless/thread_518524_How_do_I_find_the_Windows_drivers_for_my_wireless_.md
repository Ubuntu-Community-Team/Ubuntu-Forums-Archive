---
title: "How do I find the Windows drivers for my wireless card?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by Squee3 on 2007-08-06
I can't get NDISwrapper to work, and I'm beginning to think that the files I found aren't actually my wireless card drivers.  I was never sure to begin with, but now that they don't work I'm pretty sure that they are the wrong files.  How can I find the drivers for my wireless card?

---

### Post by kevdog on 2007-08-06
First determine chipset and ID number of your wireless card:

lspci -nn

And then visit the ndiswrapper website ([http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)) and look at their list of supported wireless cards and drivers.  It more than likely will give you a link or tell you where to find the driver for your card.

---

### Post by Squee3 on 2007-08-06
the command you gave doesn't work.  are you sure that it's a command prompt command, or did you type a terminal command by mistake?

---

### Post by xyphur on 2007-08-06
lspci -nn

is a Linux terminal/console application command, which will return information about your hardware that you'd be hard-pressed to receive from Windows. What you're after is the numerical PCI Identifier of your wireless adapter, in the form of [xxxx : xxxx]. Once you have that unique number, you'll have a much easier time locating the correct windows drivers with the help of the NDISwrapper website's handy hardware listing.

---

### Post by kevdog on 2007-08-06
Do you have a wireless card or a USB dongle?  I missed that information before!

---

### Post by Squee3 on 2007-08-06
USB.  It's a Netgear WG111v2 802.11 USB2.0.  I was lucky enough to find out what drive it uses, and it is supported by ndiswrapper.  I just can't find the driver.  The link on the ndiswrapper website didn't help, and I can't find the CD that I used to install it.  I looked at the Netgear folder in Windows in Programs, but couldn't find them.  Right now I'm trying and failing to make ndiswrapper use the driver I found in the DRIVERS/Networking folder under Windows.  I have no clue if it's even the netgear driver or not, but it's the only thing I can find.

---

### Post by xyphur on 2007-08-06
I've located the drivers for you on DriverGuide.com (I have an account)

PM/e-mail me the address you'd like the entire archive I downloaded sent to.

---

### Post by xyphur on 2007-08-06
I went ahead and extracted the XP-version .sys and .inf files from the Macrovision InstallShield setup package I downloaded. Thought I'd save you some trouble messing with wine and such to get the files you need. Just plug these two files into NDISwrapper, and you should be in business.

Again, let me know your e-mail in a PM, and I'll send both files off to ya.

---

### Post by Squee3 on 2007-08-07
let me update the situation so that anyone else can help.  xyphur has sent me the drivers and I installed them.  ndiswrapper is accepting the files, and says that the drivers are installed.  my computer is still not recognizing that the card is plugged in, and it's not showing up when I go to configure the network.  only wired connection, which I don't have, and modem connection, which I also don't have.  in fact, I've completely removed the modem from my computer because it was blocking air from getting to the fan built in to my video card.  if anyone can explain why my computer recognizes the drivers, but not the USB wireless card, please help me.

---

### Post by kevdog on 2007-08-07
If this post doesnt help you, let me know, and I can delve into your problem further:
[http://ubuntuforums.org/showthread.php?t=51993](http://ubuntuforums.org/showthread.php?t=51993)

---

### Post by Squee3 on 2007-08-08
no, that post didn't help me either.  everything went perfectly until I reached the command "modprobe ndiswrapper"  that command doesn't do anything.  it says that if it works the blue light will come on.  that doesn't happen for me.

---

### Post by kevdog on 2007-08-08
Did you keep going --- and then reboot the machine??

---

### Post by Squee3 on 2007-08-08
I tried to keep going, but when I tried the commands with wlan0 it said that there was no such thing as wlan0.  so I just gave up and decided to repost saying that it didn't work.

---

### Post by xyphur on 2007-08-08
try eth1 instead of wlan0... ;)

---

### Post by kevdog on 2007-08-08
Im not sure if this command is going to work, but can you post the following:

lshw -C network

---

### Post by Squee3 on 2007-08-08
the command worked.  I tried again with eth0, btw, and it said that there was no wireless extension.
*-network
description:  Ethernet interface
product:  8256EZ 10/100 Ethernet Controller
vendor:  Intel Corporation
physical id:  8
bus info:  pci@01:08.0
logical name:  eth0
version:  02
serial  00:13:20:79:a6:b1
width:  32 bits
clock:  33 MHz
capabilities:  bus_master cap_list ethernet physical
configuration:  broadcast=yes driver=e100 driver version=3.5.1-k2-NAPI firmware=NA latency=64 maxlatency=56 mingnt=8 multicast=yes
resources:  iomemory:  fe9ff000-fe9fffff ioport:  df40-df7f irq:20

---

### Post by xyphur on 2007-08-08
...not eth0, that's your wired ethernet adapter. It may have configured the wireless adapter to eth1 as mine did when I was messing around with my Broadcom miniPCI card - mind you, I was using Debian Etch at the time, so YMMV.

I'd attempt the NDISwrapper bit again with eth1 this time instead of eth0... I'm 50% positive this is the problem. ;)

---

### Post by Squee3 on 2007-08-08
actually, I tried that before I tried eth0.  it didn't help.  I don't really know what to do now.  I'm getting tired of having to use windows for internet access.  lol.  It's all screwed up like usually and I get the blue screen of death every other time I start it.  that was the last of the problems that made me switch, actually, but yeah, I'd like to the internet working in Ubuntu so I don't have to use windows anymore.  please help me.

---

### Post by Squee3 on 2007-08-09
do you think that I should keep going with the commands even tho the  blue light on the card isn't working and it says there isn't a wireless extension?

---

### Post by Squee3 on 2007-08-09
I just now discovered something that may help.  I don't think that it is actually a WG111v2.  It just says WG111 everywhere I look.  I thought it was a WG111v2 because the ID numbers say WG111v2.  So I'm not sure which one it is.

---

