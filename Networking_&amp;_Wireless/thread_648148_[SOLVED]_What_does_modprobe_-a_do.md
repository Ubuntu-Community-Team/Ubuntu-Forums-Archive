---
title: "[SOLVED] What does modprobe -a do?"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2007-12-23
Hi I'm trying to finish my NDISwrapper tutorial.  I'm writing the stage where someone needs to load the NDISwrapper module.  I have 3 questions.

```
$ echo ndiswrapper | sudo tee -a /etc/modules
$ depmod -a
$ modprobe ndiswrapper
```

**1.)**
Can I replace the first command with this?  If not then why??
```
$ echo ndiswrapper >> /etc/modules
```

**2.)**
The second command "depmod -a" is supposed to load the module automatically every time you reboot the PC right?  So that ppl won't have to run this everytime they want to start their wireless.
```
$ modprobe ndiswrapper
```

**3.**
Because "depmod -a" doesn't seem to do anything important.  Everytime I needed to make the wireless work I had to "modprobe ndiswrapper".  So can I ignore bringing up "depmod -a" in my tutorial?

---

### Post by kevdog on 2007-12-23
I think you are kind of reinventing the wheel on the ndiswrapper tutorial but here is what you need:

You can't do
echo ndiswrapper >> /etc/modules 
unless you are root.  Again only root has write permissions on the /etc/modules file.  So hence the reason for:
echo ndiswrapper | sudo tee -a /etc/modules

depmod

This checks for MODULE DEPENDENCIES.  Basically lets you know if have modules with any unmet dependencies.  In my opinion, I dont think you need this step, however it is part of the official ndiswrapper installation instructions

---

### Post by jingo811 on 2007-12-23
Then I guess I need to automate this command every time the PC does a reboot?
```
$ modprobe ndiswrapper
```

How can I accomplish that?
I know how to make things not load at startup with "/etc/modprobe.d/blacklist" but I don't know how to do the opposite.  I only know the darkside ways.

> I think you are kind of reinventing the wheel on the ndiswrapper tutorial but here is what you need:
And it shall be a much shinier wheel compared to that wooden one I had to go through when I started out once.

---

### Post by kevdog on 2007-12-23
Putting any module inside /etc/modules has the module load at boot.  I think you should have other modules loaded in this file also.  Again -- any module not originally compiled into the kernel source but added later as a dynamic modules, needs to be inserted in the /etc/modules file if you want the module loaded at boot.  If you are finding its not loading, then there is either an error, or a timing issue where a dependency which should be loaded prior to the module, is loaded after the module.

---

### Post by jingo811 on 2007-12-23
```
root@sama:~# **cat /etc/modules **
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
root@sama:~# 

```

So is there any procedures for checking what error or dependencies is causing ndiswrapper from auto loading?
Because I don't know how to make auto loading bash scripts, that would require more work and reading on my part.

---

### Post by kevdog on 2007-12-23
Are you having a problem with it loading at boot??

I would usually check dmesg to see if you have an error.  That would give more details regarding the specific error you are having.

---

### Post by jingo811 on 2007-12-24
:oops: I checked things again it seems /etc/modprobe is doing its job just fine, my bad.
My re-formulated question now is how do I automate this process?

```
sudo -s
iwconfig wlan0 essid any
iwconfig
iwconfig wlan0 essid any      ; I always need to do this command twice before my SSID gets set
iwconfig
dhclient wlan0
```

---

### Post by burbankmarc on 2007-12-24
Uhm, I'm not positive off the top of my head but should be under the /etc/network/interface file.

```

iface wlan0 inet dhcp
wireless-essid any

```

I think that should do it

---

### Post by kevdog on 2007-12-24
Stick the command in a script 
#!/bin/bash

You may need some sleep statements in between the commands just to make sure everything works appropriately.

---

### Post by jingo811 on 2007-12-26
> **burbankmarc said:**
> Uhm, I'm not positive off the top of my head but should be under the /etc/network/interface file.

```

iface wlan0 inet dhcp
wireless-essid any

```

I think that should do it

I'll be darned that was quick and easy.  Almost too easy :)
> 
gara@sama:~$** cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

[B]iface wlan0 inet dhcp
wireless-essid any[/B]
gara@sama:~$

---

