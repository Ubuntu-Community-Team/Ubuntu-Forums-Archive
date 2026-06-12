---
title: "WiFi Installation Issue"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by voltage on 2007-02-05
Hi,

    Currently I were using Aztech WL230 USB dongle. Fortunedly Aztech have provide the driver for support for Linux Kernel 2.4x / 2.6.x. 

    From the following is the step that I try to install the dongle : -

          1 ) copy the file ***program***.tar.gz to a temporary file call /temp
          2 ) tar xvzf ***program***.tar.gz
          3 ) cd ***program/***
          4 ) ./configure

    After the step 4, the command line were complain some like "file not found". So due to these issue ... do any expert can tell me what should do ??

Please Advice. Thanks
Rg,
Frank Ong

---

### Post by Ryan450 on 2007-02-05
can you post up the error messages here for us as it appears in your terminal?

---

### Post by voltage on 2007-02-05
> **Ryan450 said:**
> can you post up the error messages here for us as it appears in your terminal?

The error from the terminal is "-bash: ./configure: No such file or directory"

---

### Post by Ryan450 on 2007-02-05
ah you dont have the compiling stuff needed to do this. pretty simple fix for that. 

in terminal 

sudo apt-get install build-essential

---

### Post by voltage on 2007-02-05
> **Ryan450 said:**
> ah you dont have the compiling stuff needed to do this. pretty simple fix for that. 

in terminal 

sudo apt-get install build-essential


OIC... but unfortunately, my pc is difficultly to connected to internet to doing the download.. so do you have any good solution to help me to get the "build-essential" package ??

---

### Post by Ryan450 on 2007-02-05
yea, use the synaptic package manager, enable the cd as a repository then you can get it from there. or you could go into your /etc/apt/sources.list uncomment it there and run the apt-get install command should be able to grab it from cd as well.

---

### Post by voltage on 2007-02-05
> **Ryan450 said:**
> yea, use the synaptic package manager, enable the cd as a repository then you can get it from there. or you could go into your /etc/apt/sources.list uncomment it there and run the apt-get install command should be able to grab it from cd as well.

Hi, Could you please show me the step by step how to download and burn those package to the cd and what which line of command i have to uncomment then the the system will grab it from cd to doing the installation... 

Thanks:confused:

---

### Post by Ryan450 on 2007-02-05
sure I'll do that when I get back home, killing some time here at work intill things pick up.

---

### Post by voltage on 2007-02-05
> **Ryan450 said:**
> sure I'll do that when I get back home, killing some time here at work intill things pick up.

OK ... anyway .. thanks in advance ..

---

### Post by Ryan450 on 2007-02-05
If I were you I would double check to make sure that ubuntu has not already detected and set up your wireless card with its generic stuff, it does a good job, picked up my ahteros based chipset which I normally need to run ndiswrapper to get up and running. To double check type in ifconfig. 

ETH0 is normally the hardwired nic that most computers come standard. my wireless card shows up as Ath0, and lo is the local loopback. 

Alright, first step is to boot into ubuntu then insert your ubuntu cd and mount it. I'll post all my terminal commands step by step for ya in a code window below. 

```
mount /cdrom
```

then you'll want to install the build-essential from it. 

```
sudo dpkg -i /cdrom/pool/main/b/build-essential/build-essential_11.3_i386.deb

```

this is the easiest way to do it, and my apologies I made the assumption that the cdrom repository was listed in apt/sources.list

after you install that package you should be able to compile your driver.

---

