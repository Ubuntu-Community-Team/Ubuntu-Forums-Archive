---
title: "No internet on new install"
date: 2005-04-03
forum: Networking &amp; Wireless
---

### Post by PMO6022 on 2005-04-03
I have been running ubuntu successfully for several months.  This morning I installed Warty on my wife's machine, and I have no internet access.  

During the install process, DHCP was not detected (which is correct, I have my home network set up through a router, all computers on the network get a static ip).  However, when I entered my ip, gateway, dns, etc. settings I got an error saying something to the effect of "network not configured".  I continued on with the install and it finished up, just with no network.  

I do get an error at boot:> starting hotplug subsystem
modprobe: FATAL: error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/char/hwrandom.ko) no such module
I really don't know what to do at this point, as I have not had this problem on any other ubuntu install I've done.  The computer was previously running XP fine, so I know the ethernet cables are connected correctly, etc.  Prior to XP, she was running Mandrake 9.2 without any problems with the ethernet card.

I do not know the particular brand of ethernet card, as we got it from a friend.  I pulled it out and looked it over, but there was nothing to indicate brand.  I've tried a few things, not really knowing what I was doing, I'll post the output here in the hopes that it will be of some use to someone who knows what they are doing:

```
meg@ubuntu:~ $sudo ifup eth0
Error for wireless request "Set Encode" (8B2A) :
     Set failed on device eth0 ; Operation not supported.
SIOCSIFFLAGS: Resource temporairly unavailable
SIOCSIFFLAGS: Resource temporairly unavailable
Failed to bring up eth0.
```
I don't know why it is mentioning wireless, I am setting up a wired network.

When I try ifconfig eth0, it lists the correct ip address, and subnet mask - the ones I entered at install.  It shows no data transmitted or recieved.

Any help you can offer is appreciated, if you need more info from me, please don't hesitate to ask.  

Thanks,
Pete

---

### Post by PMO6022 on 2005-04-03
Some additional information:

the /etc/network/interfaces file has the same settings as my working ubuntu machine.  

When I run the network settings wizard, I am unable to activate my ethernet card (eth0).  When I try to activate it by clicking "activate", a check momentarially appears  in the "active" box, then disappears.

---

### Post by PMO6022 on 2005-04-03
Some additional info, as I bang my head against the wall some more...

```
meg@ubuntu:~ $ lspci:
0000:02:01.0 Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 01)
```

```
meg@ubuntu:~ $ dmesg | grep -i eth
e100: eth0: e100_probe: addr 0xe4000000, irq 210, MAC addr 00:A0:C9:1B:7B:AA
```

Please correct me if I am wrong, but it seems that ubuntu sees the ethernet card, it is just not configured correctly?  The settings in /etc/network/interfaces are correct.

I am searching the web, the forum, and following the discussion "Newb cant get internet connection to work" at [http://www.ubuntuforums.org/showthread.php?t=23673](http://www.ubuntuforums.org/showthread.php?t=23673) without much success.

---

### Post by arctic on 2005-04-03
i wish i could help but right no i have no clue what might cause your problem except a "broken" module.

---

