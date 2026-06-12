---
title: "connecting through ethernet"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by djFiya on 2008-08-02
hey I Installed ubuntu and cannot connect to the internet using ethernet. It connects through the USB option and need help. Please can somone help?

---

### Post by djFiya on 2008-08-02
Please, is there anyone that can help. i'm bout fed up with windows. please

---

### Post by djFiya on 2008-08-02
thanx for all the help guys

---

### Post by K2712 on 2008-08-02
First of all, your original post is only an hour old.  Just because you aren't answered immediately doesn't mean there aren't people willing to help.

Now, have you check the [wired ethernet troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=87644")?

Also, have you done any forum searches to see if your problem has already been addressed? 

There are a lot of threads out there about network problems, and almost all of them request the output of the following:

```
ifconfig -a
```
```
lshw -C Network
```
```
cat /etc/network/interfaces
```

If the troubleshooter doesn't help you, come back here with that and we'll see what can be done.

---

### Post by djFiya on 2008-08-02
I'm sorry. i'm just a little short temperd dealing with this slow computer. my computer needs a new video card. And my 3 month old just cries aaaaaaaaall day. again I apologize. But i didn't see any help in the thread you suggested. but this is the output of what you gave me.

```
eth0      Link encap:Ethernet  HWaddr 00:18:9b:44:04:2a  
          inet addr:71.238.13.76  Bcast:255.255.255.255  Mask:255.255.248.0
          inet6 addr: fe80::218:9bff:fe44:42a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1151119 (1.0 MB)  TX bytes:154646 (151.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:18:4d:ea:3e:53  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:618 errors:0 dropped:0 overruns:0 frame:0
          TX packets:618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37703 (36.8 KB)  TX bytes:37703 (36.8 KB)

```

[HTML]WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:01:0d.0
       logical name: eth1
       version: 10
       serial: 00:18:4d:ea:3e:53
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:18:9b:44:04:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=71.238.13.76 multicast=yes
[/HTML]

[HTML]auto lo
iface lo inet loopback




iface eth1 inet dhcp

auto eth1
[/HTML]

---

### Post by djFiya on 2008-08-03
please is there any one that can help

---

### Post by TJCIB on 2008-08-03
I'm new also, so this may be a dumb question...

It looks like you have two ethernet cards, are you sure you're plugged into the right one?

---

### Post by djFiya on 2008-08-03
Well I replaced an ethernet card from my storage. that might be it, Or it might be the USB thats showing up. not sure, but its only on card inthere right now.

---

### Post by TJCIB on 2008-08-03
your ifconfig is showing eth0 and eth1.

Usually eth0 is your built-in ethernet (on your motherboard) and eth1 will be the one you installed (ethernet card).

What do you mean "through USB"?  Are you connecting to your modem/router through USB instead of ethernet cables?  If yes, I don't think that's the preferred method.  If you can disable the USB connection, that might help clear things up.

Right now it looks like your eth0 is going and your eth1 is disabled.  However "cat /etc/network/interfaces" isn't showing anything for eth0.

You might want to try to manually set up your eth0.  You can do that graphically by left clicking on the network icon in the top right of your screen and clicking "manual configuration".  In there you can set it to dchp or static ip address, etc...

---

### Post by djFiya on 2008-08-03
well the usb is my only option of connecting. i tried and tried the ethernet but just wont connect. i messed around with the network manager and nothing. soon as i plugged usb in it connected. i'm guessing that the card is installed because you see that. is ther anything i gotta put in the terminal to activate it or somthing?

---

### Post by TJCIB on 2008-08-03
how are you connecting the ethernet cables?
Are you going directly to a modem?
Are the lights on the ethernet care lighting up when you plug in the cable?

Was this a clean install that you just did?

---

### Post by fwre01 on 2008-08-03
have u used the nic before, in a different operating system? you can do a "sudo ifup eth1" but i doubt that will be the reason it says its DISABLED. im assuming you're connecting to some USB modem, this is why you are seeing eth0 with that public IP address. What is your ethernet connection connecting to? the same modem?

its not disabled in the BIOS is it?

---

### Post by djFiya on 2008-08-03
i'm connected directly the the modem. all the lights are on. when i plug in the link light does come on. I re installed numerous of times and they were all clean. the same thing happend when i had At&t but it ended up workin by it self after a few hours. now i have comcast. and it doesnt wanna work.

---

### Post by djFiya on 2008-08-03
Itworks fine when i boot up on xp

---

### Post by K2712 on 2008-08-03
Does your modem match any of the ones on this page?

[https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html](https://help.ubuntu.com/8.04/internet/C/modems-adsl-usb.html)

---

