---
title: "RTL8111/8168 Compilation error STRUCT NET_DEVICE"
date: 2017-08-28
forum: Networking &amp; Wireless
---

### Post by 0pc0d3 on 2017-08-28
Hello, guys!

I hope someone could help me.. I have the ETH0 as a REALTEK, this was working fine, but for some reason now i can list it just through the

lshw -C network

And it appears as "*-network UNCLAIMED"..
I did some research and I find a topic here to compile the driver and install it..

[https://ubuntuforums.org/showthread.php?t=1022411](https://ubuntuforums.org/showthread.php?t=1022411)

When I try to compile the following error happens:

> 
/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src/r8168_n.c: In function ‘rtl8168_rx_interrupt’:
/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src/r8168_n.c:25735:28: error: ‘struct net_device’ has no member named ‘last_rx’
                         dev->last_rx = jiffies;
                            ^
scripts/Makefile.build:294: recipe for target '/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src/r8168_n.o' failed
make[3]: *** [/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src/r8168_n.o] Error 1
Makefile:1492: recipe for target '_module_/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src' failed
make[2]: *** [_module_/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src] Error 2
make[2]: Leaving directory '/usr/src/linux-headers-4.11.6-041106-generic'
Makefile:95: recipe for target 'modules' failed
make[1]: *** [modules] Error 2
make[1]: Leaving directory '/home/mylnx/Downloads/Sorted/Drivers/RTL8111/r8168-8.044.02/src'
Makefile:40: recipe for target 'modules' failed
make: *** [modules] Error 2



Anyone has any ideas to help me ?

---

### Post by praseodym on 2017-08-29
Try this one

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.044.02-1_all.deb
sudo dpkg -i r8168-dkms_8.044.02-1_all.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```

---

### Post by chili555 on 2017-08-29
> Anyone has any ideas to help me ?Yes! Here's an idea: don't use a circa-2008 thread to solve a 2017 problem. We no longer use wooden wheels on our sleek, black BMWs.

How is it that you have kernel version 4.11? Did you install a mainline kernel? 

The driver r8169 is built-in to all recent Ubuntu versions. If it doesn't load automagically, something else is wrong.  What happens when you try to load it?```
sudo modprobe r8169
dmesg | grep r8169
```

---

### Post by 0pc0d3 on 2017-10-18
Thanks for your answer guys! Sorry my VERY late reply!

I did the:
```
[COLOR=#000000][FONT=&amp]sudo modprobe r8169[/FONT][/COLOR]
```

Works very well. Thanks!

I'm relatively new to linux, sorry. My version seems to be the Stable one.

What could caused this ? The other strange thing is that my apt-get upgrade isn't updating my kernel, can ask this here ? 

Thanks!

---

### Post by chili555 on 2017-10-18
> **0pc0d3 said:**
> Thanks for your answer guys! Sorry my VERY late reply!

I did the:
```
[COLOR=#000000][FONT=&amp]sudo modprobe r8169[/FONT][/COLOR]
```

Works very well. Thanks!

I'm relatively new to linux, sorry. My version seems to be the Stable one.

What could caused this ? The other strange thing is that my apt-get upgrade isn't updating my kernel, can ask this here ? 

Thanks!It could be that, in your efforts to install a better driver, you blacklisted r8169. Let's check. Please run and post:```
grep r816  /etc/modprobe.d/*
```As for your apt-get upgrade issue, did you first run:```
sudo apt-get update
```This builds an index listing the packages that are upgrade-able.

---

### Post by 0pc0d3 on 2017-10-18
> **chili555 said:**
> It could be that, in your efforts to install a better driver, you blacklisted r8169. Let's check. Please run and post:```
grep r816  /etc/modprobe.d/*
```As for your apt-get upgrade issue, did you first run:```
sudo apt-get update
```This builds an index listing the packages that are upgrade-able.

Command printed...
```

/etc/modprobe.d/r8168-dkms.conf:# settings for r8168-dkms/etc/modprobe.d/r8168-dkms.conf:# map the specific PCI IDs instead of blacklisting the whole r8169 module
/etc/modprobe.d/r8168-dkms.conf:alias	pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*	r8168
/etc/modprobe.d/r8168-dkms.conf:alias	pci:v000010ECd00008168sv*sd*bc*sc*i*	r8168
/etc/modprobe.d/r8168-dkms.conf:# to blacklist the whole r8169 module
/etc/modprobe.d/r8168-dkms.conf:#blacklist r8169

```

Indeed, I forgot about the apt-get update that refresh the list to upgrade. Thanks haha... :)

---

### Post by chili555 on 2017-10-19
Hmmm, let's also see:```
cat /etc/modprobe.d/r8168-dkms.conf
sudo dkms status
```

---

### Post by jeremy31 on 2017-10-19
Another important question, what Ubuntu version?  The 4.11.6-041106-generic kernel is not from Ubuntu so it could cause problems

---

### Post by 0pc0d3 on 2017-10-23
> **chili555 said:**
> Hmmm, let's also see:```
cat /etc/modprobe.d/r8168-dkms.conf
sudo dkms status
```

```
# settings for r8168-dkms

# map the specific PCI IDs instead of blacklisting the whole r8169 module
alias	pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*	r8168
alias	pci:v000010ECd00008168sv*sd*bc*sc*i*			r8168


# if the aliases above do not work, uncomment the following line
# to blacklist the whole r8169 module
#blacklist r8169

```

```
bbswitch, 0.8, 4.10.0-37-generic, x86_64: installedbbswitch, 0.8, 4.11.6-041106-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-97-generic, x86_64: installed
nvidia-375, 375.66, 4.10.0-37-generic, x86_64: installed
nvidia-375, 375.66, 4.11.6-041106-generic, x86_64: installed
nvidia-375, 375.66, 4.4.0-97-generic, x86_64: installed
r8168, 8.041.00, 4.4.0-97-generic, x86_64: installed

```

Can you explain your idea for me later ? Just to understand whats going on :)

> **jeremy31 said:**
> Another important question, what Ubuntu version?  The 4.11.6-041106-generic kernel is not from Ubuntu so it could cause problems

Is 16.04 LTS Xenial.


My kernel is still the same version after "apt-get update" ->"apt-get dist-upgrade" and ->"apt-get upgrade". And my ubuntu version will never update ? I mean.. I installed ubuntu in a VM and it is in version 17.

Thanks!

---

### Post by jeremy31 on 2017-10-23
Once you installed the 4.11.6 kernel Grub will load it by default as Ubuntu uses a different way of labeling kernel, 4.11.0-? is the newest from Ubuntu and Grub will always see 4.11.6 as newer than 4.11.0

---

### Post by 0pc0d3 on 2017-10-23
> **jeremy31 said:**
> Once you installed the 4.11.6 kernel Grub will load it by default as Ubuntu uses a different way of labeling kernel, 4.11.0-? is the newest from Ubuntu and Grub will always see 4.11.6 as newer than 4.11.0

But all upgrades will have the same fixes as the new major kernel updates ?
And the version 16.04 it gets update or would I have do something manually ?

---

### Post by jeremy31 on 2017-10-23
I would reboot and press/hold the shift key until the grub menu appears, then choose advanced options and scroll down to the first 4.10.0-37-generic kernel entry and boot into it.  Then remove the 4.11.6 kernel but since I don't know how you installed it, I don't know the safe way to remove it

---

### Post by 0pc0d3 on 2017-11-04
> **jeremy31 said:**
> I would reboot and press/hold the shift key until the grub menu appears, then choose advanced options and scroll down to the first 4.10.0-37-generic kernel entry and boot into it.  Then remove the 4.11.6 kernel but since I don't know how you installed it, I don't know the safe way to remove it

I downloaded from ubuntu and installed on my system. I keep updating it through apt-get.
I downloaded some days ago the ubuntu again, but this time it comes with the new version, 17.

Do you have any tutorial or How-To that I may can follow ?

---

