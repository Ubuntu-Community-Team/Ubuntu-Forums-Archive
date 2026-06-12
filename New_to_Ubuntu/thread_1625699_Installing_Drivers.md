---
title: "Installing Drivers"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Katana24 on 2010-11-19
Hi - just joined the Ubuntu forums - all looks good :D

Well lets get to it - I recently got hold of a computer which has Ubuntu installed as the OS. All is good there but I want to access the net. Because the fibre-optic cable is in the adjacent room and also because the room belongs to someone else I have to go with the wireless option. 

I ordered a wireless USB which came with a CD - but the computer doesn't have a CD drive. Therefore I downloaded the necessary drivers onto an external hard drive and copied the file onto the desktop of the Ubuntu computer. 

So - how do I install the driver that is on the desktop? Do I need to go to the command line?

Cheers

---

### Post by coffeecat on 2010-11-19
First thing, the driver you downloaded will be a Windows one. You may need to use it - but hopefully not. If you are lucky the device driver will already be included in your installation. So to find out, do two things:

Plug in the USB wireless device and boot up. Look for the network manager icon near the top right next to the volume icon. Left-click on it. Does it show any wireless networks? If yes, you need do no more than click on your network and type in the passkey when prompted.

If not, go to Applications > Accessories and open a terminal. Post the output of this command (with the USB stick still plugged in):

```
lsusb
```That will give us information about the wireless chipset, so we know how to proceed.

---

### Post by Tauqir Ahmad on 2010-11-19
In System Menu on top left corner you will see administrator and in administrator menu you will see your required Option of Drivers but first u'll need a disc having Ubuntu drivers or u can download its drivers from its site if they have any for Ubuntu Linux.....

---

### Post by Katana24 on 2010-11-19
Hello - after running "lsusb" in the terminal i get the following output:


camara@camarabuntu:~$ lsusb
Bus 001 Device 004: ID 0bda:8171 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 045e:0750 Microsoft Corp. 
Bus 002 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So what now?

---

### Post by coffeecat on 2010-11-20
Your wireless device has the ID number 0bda:8171. If you are using 10.10/Maverick (you don't say which version) it might  work out of the box - did you check to see if networks are visible in network manager? If you are sure you can't see networks, have a look at this thread, post #6:

[]("http://newyork.ubuntuforums.org/showthread.php?t=1511618")[http://ubuntuforums.org/showthread.php?t=1511618](http://ubuntuforums.org/showthread.php?t=1511618)

That solution was for Lucid/10.04, but if you can't see networks in Maverick it would be worth a try.

---

### Post by Katana24 on 2010-12-01
hello - cheers for that - i can now see the network :D, but Im trying to connect to it and cant seem to. The password I am entering doesn't seem to work - its a WPA personal key according to Ubuntu but it doesn't seem to want to connect?

Whats the problem?

---

