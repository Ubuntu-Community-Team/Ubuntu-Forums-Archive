---
title: "PDA kills internet connection"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by BlakeM on 2009-01-15
A friend of mine has a i-mate JasJar which is having some battery issues. She's lent it to me to see if I can fix the issue. While I have the PDA  I'd like to see if I could use such a device effectively with Ubuntu.

Unfortunately, so far I haven't been so lucky. When I plug the JasJar into my laptop via USB cable, I lose my internet connection. nm-applet registers a new "point-to-point" connection and seems to ignore the selected wireless connection I'd like it to use.

I'm pretty new to Ubuntu and I'm not really sure how to go about fixing this issue. Any ideas from the Ubuntu community would be greatly appreciated.

Thanks in advance for your time and your help.

---

### Post by cmnorton on 2009-01-17
How do you connect to the internet, wired/wireless, and what kind of device is it?

---

### Post by BlakeM on 2009-01-17
> **cmnorton said:**
> How do you connect to the internet, wired/wireless, and what kind of device is it?

I connect wirelessly but I figured out what the issue was. When you connect a PDA in Ubuntu the Network Manager (nm-applet) will automatically setup your device as the default internet connection. Which is exactly what was happening in my situation.

This seems a rather bizarre setting, but I'm sure they had their reasons. Here's where I found my solution: [http://www.synce.org/moin/SynceWithUbuntu]("http://www.synce.org/moin/SynceWithUbuntu")

Thanks for your help :).

---

### Post by BlakeM on 2009-01-17
Oh, I should also add that the solution to the problem is also at that link.

I'll do a brief tutorial based on what I did to fix my problem. I'm using a i-mate JasJar running Windows Mobile 5 (Build 14847.2.0.0).

Basically you have to make sure the Network Manager ignores your pocket PC. To do that:

[LIST=1]
[*]First, check what device name was given to your pocket PC. To find the device name connect your pocket PC and execute the following command:
```
/sbin/ifconfig -a | grep 80:00:60:0f:e8:00  | cut -d " " -f 1

```
eth2 was the device name given to my i-mate JasJar. Depending on your network setup, it may be something else. The output of the command will be something like this:
>  /sbin/ifconfig -a | grep 80:00:60:0f:e8:00  | cut -d " " -f 1
[COLOR="Red"]eth2[/COLOR]
[*]Remember the device name given to your pocket PC and open your network interfaces file by issuing the following command in Terminal
```
sudo gedit /etc/network/interfaces
```
If you're using roaming mode in Network Manager the file will contain the following two lines:
> auto lo
iface lo inet loopback

[*]To make Network Manager ignore your device, add the following line to your network interface file:
```
iface <interface/name of your device> inet dhcp

```
[*]Save and exit your network interfaces file.
[/LIST]

The next time you connect your device, Network Manager should ignore your Pocket PC and continue using your current default network connection.

---

