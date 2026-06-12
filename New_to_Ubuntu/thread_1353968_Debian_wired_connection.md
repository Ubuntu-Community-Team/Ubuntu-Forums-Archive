---
title: "Debian wired connection"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-12-13
Hello everyone:

Im having trouble configuring my wired access to my computer.

I have built a debian server: (no GUI), and just recently hooked it into my router.

No the problem is that I can't seem to get internet.

In addition, I seem to have somehow mangled my /etc/network/interfaces file, since it cannot be read.

Here is my interfaces file.

```

auto lo
iface lo inet loopback interface
```

eth1 (the connected interface) does not start... I have to bring it up manually with ifconfig eth1 up.

Then I start receiving a ton of packets, and can ping my router (192.168.0.1), but none of the other computers on my network, or the internet.

Thanks for any help you can give me!

---

### Post by yeats on 2009-12-13
> In addition, I seem to have somehow mangled my /etc/network/interfaces file, since it cannot be read.

Here is my interfaces file.

```
auto lo
iface lo inet loopback interface
```

To fix this, just remove "interface" from the second line.

If you will, do an

```
ifconfig
```

and post the output, then we'll see a little more about what's what.  I'm mainly interested in why eth0 is not being used?  What device is eth1?

You should be able to do (as root):

```
dhclient eth1
```

and your router should grant an IP.

---

### Post by slakkie on 2009-12-13
Hi, have a look here:

[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

---

### Post by darkeye123 on 2009-12-13
eth0 is a secondary ethernet port, one which is not supported, I simply did not remove it.
 
 
Will run dhclient when I get home.

---

### Post by yeats on 2009-12-13
> eth0 is a secondary ethernet port, one which is not supported, I simply did not remove it.

Ah.. that makes sense :-)

---

### Post by darkeye123 on 2009-12-14
Alright. Dhclient set up my wired connection perfectly. I can now ping google.ca and ubuntu.com. 
 
Thanks a lot!
 
Is there someone way I can set up the computer to use eth1 and dhclient whenever I start it up?
 
The commands I use to get eth1 going:
```
su
ifconfig eth1 up
dhclient eth1
```

---

### Post by shairozan on 2009-12-14
Hey there, 

It might be easier to do everything through the /etc/network/interfaces file

To have an interface start with the system, you just issue auto <dev> or auto eth1

Here is an example setup specifically for DHCP

```
# The primary network interface
auto eth1
iface eth1 inet dhcp

```

You should be able to append that to the /etc/network/interfaces file and then issue the "/etc/init.d/network restart" command for it to take affect.

---

