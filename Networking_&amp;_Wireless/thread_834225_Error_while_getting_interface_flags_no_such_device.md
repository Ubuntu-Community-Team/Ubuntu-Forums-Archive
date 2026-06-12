---
title: "Error while getting interface flags: no such device"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by chrisdl on 2008-06-19
The story is my house was hit by lightning and I lost network connections on all my wired PCs.  I don't know what I'm doing on my Linux machine so I need help.

When I type ifconfig I only get the lo link encap:local loopback.  There is no eth0.

I tried $sudo ifconfig eth0 up and got the "eth0: ERROR while getting interface flags: no such device"

When I type $lspci I see "02:0c.0 Ethernet controller: 3Com Corporation Unknown device ffff (rev 78)".  So I assume it can see my integrated LAN connection on the mobo.  Is that right?

When I use the menu and go to system|admin|network I don't have a wired connection option just a modem connection.

My machine connects to a switch which is connected to an AT&T residential gateway.  AT&T had to replace the gateway and switch after the lightning strike.

I also tried to install a new network card but that caused some Plug and Play configuration erros to appear on boot up so I took it out and cleared the BIOS.  I suppose I could try that again.  But something else seems wacky.

Can anyone help?

---

### Post by chrisdl on 2008-06-19
Ok.  I tried $lshw -C network and got this:

*-network UNCLAIMED
description: Ethernet controller
product: 3Com Corporation
vendor: 3Com Corporation
physical id: c
bus info: pci@0000:02:0c.0
version: 78
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=64 maxlatency=63 mingnt=30

Does that help anyone?  It might be that my ethernet isn't working on the mobo, but I just need someone to tell me that.  I'm a beginner at linux and don't know what I'm doing.

---

### Post by Ayuthia on 2008-06-19
I could be completely wrong, but if your card is being recognized by Linux, then it looks like that it is still somewhat working.  My wireless card just died on my laptop and now it cannot be seen anymore by lspci or lshw -C network.

The lshw -C network command shows that it is UNCLAIMED.  That can mean that it cannot find a driver for your card.  Do you recall the driver that goes with your card?

---

### Post by chrisdl on 2008-06-19
When I installed ubuntu initially the network card automatically worked.  I don't know where to find the driver.  I think I figured out the card module is 3c59x should that help me find the driver?

I should probably add this is an old Dell Precision 340 with an integrated 3Com ethernet adapter.

---

### Post by Ayuthia on 2008-06-19
> **chrisdl said:**
> When I installed ubuntu initially the network card automatically worked.  I don't know where to find the driver.  I think I figured out the card module is 3c59x should that help me find the driver?

I should probably add this is an old Dell Precision 340 with an integrated 3Com ethernet adapter.

You can check and see if that module is loaded:
```
lsmod|grep 3c59x
```
If it is not there, you can try to load it:
```
sudo modprobe 3c59x
sudo ifconfig eth0 up
```

I am not for sure if this will work.  If it does, then something is causing it to not work (sorry for pointing out the obvious).  Another thing to check is after trying the ifconfig eth0 up, is to check dmesg to see what it says.  There might be some error messages for it.

---

### Post by chrisdl on 2008-06-19
Thanks for the help.

lsmod|grep 3c59x returns
3c59x     46632   0
mii        6528   1 3c59x

the eth0 up still gives me the Error while getting interface flags: no such device.

Where is this dmesg at?

---

### Post by chrisdl on 2008-06-19
OK  I found the dmesg but I can't tell if there is an error regarding this problem.  I don't see one that jumps out.

---

### Post by Ayuthia on 2008-06-19
Do you get any lights when you plug the wire into your ethernet card?

---

### Post by whale on 2008-06-27
1. type grep eth0 /var/log/dmesg

it should give you something like that:

eth0: registered as And_Here_is_a_Name_of_NIC

the driver is corectly identified and NIC works.  go to step 3
2.if you got different message 
load apropriate module by hand 
modprobe MoDuLe_Name 
you can try to bring it up
ifconfig eth0 up

and grep it again. 
if it works go to step 3 otherwise step 4
3. remove file:
/etc/udev/rules.d/70-persistent-net.rules
and restart network 
/etc/init.d/networking restart
it should WORK if not go to step 4

4. if lighting hit your network probably your NIC is damaged. so pull out the card and test it in another computer.


this problem usually occurs when you replace network card with card that uses the same driver. mac addres of previous card is cached in this file so debian(sic ubuntu ) remebers it and gives this error.

---

### Post by Javooo on 2008-11-02
sorry didnt mean to post it here

---

