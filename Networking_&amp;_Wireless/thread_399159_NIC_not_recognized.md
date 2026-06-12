---
title: "NIC not recognized"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by dave43daytona on 2007-04-01
howdy ya'll,

new to ubuntu and linux, and really would like some help. i installed ubuntu, but have no internet as my nic is not recognized. i've found the linux drivers for my nic on the web, but have not got the first clue about how to install the drivers and configure etc

i read an article that mentioed finding out which kernel module it needs to load the nic, how would i find this info ?

does someone have a step by step process aimed at newbies, for how to install a new driver (it's in .tar format) and configure in ubuntu 6.10 ?

'preciate it 

@Dave

---

### Post by Floppyjoe on 2007-04-02
What is the chipset of your wireless card?
Open a Terminal by clicking on Applications/Accessories/Terminal and enter the following commands:
For a PCI card:
```
lspci
```
For a USB card
```
lsusb
```

---

### Post by dave43daytona on 2007-04-06
hey Joe,

it's not a wireless card, it's the built in ethernet port on the back of my notebook PC

It's a Yukon 32-bit Gigabit Ethernet Controller, listed on the following page:

[http://www.marvell.com/drivers/driverDisplay.do?dId=115&pId=30](http://www.marvell.com/drivers/driverDisplay.do?dId=115&pId=30)

Driver FileName: yukonuw_v10.0.5.3.pck.tgz

I'm really struggling here. Anyone ?

---

