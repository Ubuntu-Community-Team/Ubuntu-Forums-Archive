---
title: "Change from DHCP to Static IP with out reboot"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by garyvdm on 2007-12-26
Hi

I'm using xubuntu gusty.

I move my laptop from my home network to my work network and back regularly. At work, I need to use DHCP. At home, I must enter a static address. I can't work out how to do this with out a reboot.

Lets say I am coming from home. It's currently set to use a static ip address (192.168.0.2). Through the Network Settings, I change eth0 to use DHCP. Now if I run ifconfig, I can see that eth0 has a new address from the DHCP server. 

Now if I ping google.com, I get unknown host google.com. If I ping 10.0.0.2 (a machine on the lan) I get ping: sendmsg: Operaion not permitted. 

I have tried to do the following, but the results are the same:
```
$ sudo /etc/init.d/networking restart
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 up
```

After a reboot, everything works as expected. How can I get it to work without a reboot?

Gary

---

### Post by dnvikram on 2007-12-26
Try this sequence and let Me know:

1) **sudo ifdown eth0**
2) **sudo ifconfig eth0 192.168.x.yy netmask 255.255.255.0 up**
3) **sudo ifup eth0**
4 )** sudo /etc/init.d/networking restart**

Assuming you are on dhcp now,the 2nd step will setup your static ip to eth0 temporarily and you should be able to access the internet using this new static ip.Hopefully you shouldnt be needing a reboot.

Just as a precaution,before you proceed to step 4:Remove the dhcp entry from the /etc/network/interfaces file.The line should be something like below.Just remove the dhcp word:

iface eth0 inet **dhcp**

---

### Post by garyvdm on 2007-12-26
> Just as a precaution,before you proceed to step 4:Remove the dhcp entry from the /etc/network/interfaces file.The line should be something like below.Just remove the dhcp word:

When I did that, ifup did not work:
```
$ sudo ifup eth0
/etc/network/interfaces:5: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
```
I figgured out you have to replace **dhcp** with **static.**.

Then it still does the same thing:
```
$ sudo ifdown eth0
$ sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0 up
$ sudo ifup eth0
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                [ OK ] 
$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted

```

Gary

---

