---
title: "Network / internet access"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by fairmeadow on 2007-03-05
As a new user (new to both Unix and Ubuntu), I've just installed version 6.10.  All looked fine until I wanted to look outside the PC I've installed on.  And I don't seem to be able to see anything, either other systems on the home network, or the internet.

I've installed on a partition on a Pentium 2 machine.  It has a Netgear FA311/312 (DP83815) Ethernet card that shows up in the Device Database.  It is wired to a Netgear FS608 switch, in turn wired to a Netgear DG834GT router/modem.  That is connected to ADSL.  The ISP connection is configured in the router (I don't specify DNS for example on the individual systems).  The router has a local IP address of 192.168.0.1.  I cannot ping this from Ubuntu.

Also on the home network (and switched on at the moment!) I have a Windows Vista PC wired to the router, and a MacBook Pro running both Mac OSX and (in a Parallels VM) Windows XP Pro.  This is connected wirelessly via (depending on where I am at any moment) either the router or an 802.11g unit (Apple airport express) wired to the FS608 switch.  There's also a printer wired to the airport express and another connected to the Vista machine.  And from Ubuntu I cannot see any of this!

I have Windows (Me!) on the same PC as Ubuntu, and from there I can access the internet without problem so I'm not trying to use anything physical that doesn't already work.

I know this is fairly longwinded, but maybe giving as much info as I can will help.  Can anyone help me?

Thanks
Bob

---

### Post by Jussi Kukkonen on 2007-03-05
> I know this is fairly longwinded, but maybe giving as much info as I can will help. 
Too much information is always better than too little.. In that vein, could you run these commands in a terminal and paste the output here:
```
cat /etc/network/interfaces
dmesg | grep -i eth
ifconfig

```

---

### Post by chili555 on 2007-03-05
I believe the correct module is natsemi, so please try sudo modprobe natsemi. You will have to give your password. If ifconfig shows an eth0 entry, after you loaded the module, then I would simply do sudo ifup eth0. Look for output like 'Bound to 192.168.0.5'. If you get an IP address, you are all good. If not, post back and we'll help you.

---

### Post by fairmeadow on 2007-03-05
The 'sudo ifup eth0' suggested has worked.  :)  Many thanks chili555.  

Jussi.  Also thanks.  I've run the commands now, and see the eth0 entry each time.

Now, if only I could see one of my printers ...

... but I guess that's another thread!

Bob

---

