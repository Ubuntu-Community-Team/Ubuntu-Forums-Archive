---
title: "Can't get any NIC working"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by disk11 on 2008-03-28
My dad is loaning me a laptop and I've been trying to get Ubuntu working on it all afternoon to no avail.

I have tried:
Onboard Ralink 2500 (wireless)
Onboard Via "Rhine II" (wired)
D-Link DWL-G630 PCMCIA (wireless)

None of them can get an IP address from my router, even with a static IP and pointing them to my home's gateway.

I have tried the rt2x00.serialmonkey.com driver, ndiswrapper 1.52, and some drivers I found for the onboard wired NIC, but none of them will compile all the way.  Probably because I don't have all the necessary kernel add-ons and all the "build-essentials" stuff.

How in the world do I get around this?

---

### Post by pytheas22 on 2008-03-28
Please post the output of

```
ifconfig -a
```

So you plugged an ethernet cable in and Network Manager didn't assign you an address?  Or did you try to manually configure it first (there should be no need to do this unless your network requires special settings)?  Your ethernet device especially should definitely "just work."  The ralink card should also work out-of-the-box, as well as with the serialmonkey version of the driver or with ndiswrapper.  Please give some more information and hopefully we can figure out what's wrong.  If your home network has any special settings (like MAC filtering or doesn't support dynamic dhcp), please also post that information.

Also, you can easily install all of the stuff that you need to compile drivers with the simple command:

```
sudo apt-get install build-essential
```

Make sure the Ubuntu install CD is in the drive when you do this.

---

### Post by disk11 on 2008-03-29
Alright, I got ndiswrapper installed, good thing "build-essential" is on the CD.  Still can't connect at all.

The ralink card sees the network, but for some reason it keeps reloading the screen that asks for the security code, in this case a WEP key.  The only special setting is SSID broadcast is disabled.  4 other computers plus my Nintendo Wii when in a good location can connect to the router, which is a Linksys WRT54G v8.

As for the wired NIC, I've tried setting it to DHCP to no avail, it will not pick up an IP address.  I've also tried the trick to set a static IP address.  The router is 192.168.1.1, the DHCP range starts at 192.168.1.100, so I set the laptop's IP to 192.168.1.10, subnet mask 255.0.0.0, and the gateway to 192.168.1.1 and that still doesn't work.

ifconfig -a output:
```
eth0      Link encap:Ethernet  HWaddr 00:40:45:25:9E:EF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xd800 

eth0:avah Link encap:Ethernet  HWaddr 00:40:45:25:9E:EF  
          inet addr:169.254.8.93  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9360 (9.1 KB)  TX bytes:9360 (9.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:09:0D:BA:1F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:dfffe000-e0000000 


```

---

### Post by pytheas22 on 2008-03-29
The problems with wireless could just be because of something weird with ndiswrapper.  You could try loading some different versions of the Windows driver into it and see if it helps; in my experience, ndiswrapper can behave unexpectedly just because the Windows driver that it's wrapping around is not good.  However I am wondering why you needed ndiswrapper for your ralink card at all--it should have just worked, since an rt2500 driver is included in the Gutsy kernel.

As a possible solution to getting wireless going, beyond playing around with ndiswrapper more, you could try the serialmonkey drivers, which you should be able to compile now.  Note that they won't work with Network Manager--you will have to install serialmonkey's special wireless manager, [http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all](http://packages.ubuntu.com/search?keywords=rutilt&searchon=names&suite=gutsy&section=all) , or connect via the command-line.  You will also have to blacklist the ndiswrapper and rt25xxusb modules:
```

sudo -s
echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist
echo "blacklist rt2x00lib" >> /etc/modprobe.d/blacklist
echo "blacklist ndiswrapper" >> /etc/modprobe.d/blacklist

```

then restart to make sure the serialmonkey modules are being used.

---

### Post by disk11 on 2008-03-29
It was doing the same thing before with the network key thing.

I'll throw rutilt on and see if it helps.

---

### Post by disk11 on 2008-03-30
rutilt doesn't like me
```
matt@matt-laptop:~$ rutilt 
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)


```

This is when I apply the profile to connect.

---

### Post by pytheas22 on 2008-03-30
This is strange; I guess there's a bug in the code, but I have no idea how to program so I can't help there.  I have found one other reference to the same error at [http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt&page=3](http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt&page=3) , but that person says the program still keeps connecting even after complaining.  Does this happen for you, or do you just get that error message dumped to the terminal and the program crashes for good?

A possible third solution is to use the alternative connection manager wicd, [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) I think it supports the serialmonkey drivers, although I'm not entirely sure.

---

