---
title: "Wireless problem (ubuntu 8.04) I have a wierd problem"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by sendblink23 on 2008-08-06
It seems not to work even if I do use the "ndiswrapper"

heres a print screen:
[IMG]http://i29.photobucket.com/albums/c272/sendblink23/Screenshot.png[/IMG]

As you can see It does show my Driver is *PRESENT, so whats wrong it doesn't show up in my *Network to be able to access wireless connection ??? 
That **Print Screen** is **After I CLICK**... **Configure Network**, so as you can see, the Wireless Network Card, I have doesnt show up.

I use a Belkin "Wireless Desktop Network Card" F5D6001
It is installed currently in my Windows XP working perfectly. I manually installed it, because my computer did not come with *Wifi.  Also my Router 
is really Far from my Desktop I cannot get it closer to be able to connect Internet *Ethernet Directly*...

So any help on my Problem, have tried so many things seen around in the Forums Commands.. all sort ...  I havent had any success, only getting it on "ndiswrapper" using the ".inf" from the *CD of Belkin. So after that ..  it still doesn't work.  :(

---

### Post by superprash2003 on 2008-08-07
have you rebooted after installing the drivers??

---

### Post by sendblink23 on 2008-08-07
> **superprash2003 said:**
> have you rebooted after installing the drivers??

thats the most obvious, I have rebooted into Windows to simply write back to people over here LOL, and booted back to Ubuntu.. to try what people give me or see around threads...   

none are working ...  

Can you help me out according to my Wireless network Card ?

---

### Post by sendblink23 on 2008-08-07
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```


lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:07:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
```




I ran these Commands, so whats next ??

---

### Post by sendblink23 on 2008-08-07
hehee  2 hours ago.. and nobody  helping....  :P

---

### Post by sendblink23 on 2008-08-07
> **sendblink23 said:**
> iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```


lshw -C network
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:f2:07:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Wireless PCI Card - F5D6001
       vendor: Belkin
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
```




I ran these Commands, so whats next ??

Hello  anybody ???

---

### Post by Crafty Kisses on 2008-08-07
I've looked into this, and I had a similar problem, I use to have the same wireless card on Feisty and I got it working and this is how I did it, first you need to install ndiswrapper and set it up so that your Belkin f5d6001 uses the Windows XP net8180 driver:

```
$ sudo aptitude install ndiswrapper-utils-1.9
$ sudo modprobe ndiswrapper #add ndiswrapper module to linux kernel.
$ sudo ndiswrapper -i
<path> /NET8180.INF # install windows driver (net8180)</path>
$ sudo ndiswrapper -d 1799:6001 net8180 #use installed driver (net8180) for device id (1799:6001)
```

Configure your /etc/network/interfaces either through vim, it's really your choice but anyways that's only if you feel like hacking away in command line. Here’s what my /etc/network/interfaces file is structured (keep in mind that yours will be different) after you've done that do the following:
```
man interfaces
```

The output should look something like this:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto wlan0
iface wlan0 inet static
wireless-essid {your ess id}
address 10.0.0.1
netmask 255.255.255.0
gateway {your gateway}
mode Managed
ap {mac address of your Access point - don‘t know if this is essential however.}
wireless-key {your encrypted wireless key}
```

Restart your computer.

Now if you logged in and your wireless still isn't working try the following:
```
sudo ifdown wlan0 #or whatever your wireless card’s interface id is
```

If this worked and you don't want to have to enter this every time you reboot you're going to have to add a couple of lines in the following interface:
```
wlan0 in /etc/network/interfaces
```

These are the lines you're going to have to add:
```
pre-up ifup wlan0
pre-up ifdown wlan0
```

Then you should be set, but remember you should not use the Windows drivers provided by Belkin with your wireless card, instead go on the Realtek website and download the rtl8180 driver, after ALL this you should be set.

If you have any problems just contact me.

---

### Post by sendblink23 on 2008-08-07
ok i'm going to give it a try

---

### Post by sendblink23 on 2008-08-07
i still hitting bumpssssss


I also tried using "auto-ndiswrapper"

Followed its instructions...
but when I get to the part of placing the *inf & *sys file ... it says i have to put it at an exact folder..  i did place them there..  and well it said i  had to press Enter .. i Do that but simply Nothing happens ...

LOOK HERE
my Print Screen:
[IMG]http://i29.photobucket.com/albums/c272/sendblink23/Screenshot2.png[/IMG]  

Any help with this one?? yes by the way I did manage to get the FILES inside the "1799:6001 (rev 20)" folder, i used the command:  sudo nautilus      to be able to do it ...  well  anyways  afterwards... I hit ENTER and  still  nothing   :(

I used the CD Files, because the Download of those drivers are not available anymore...  and well its mentioned everywhere I have to use the *realteks i also tried with the "net8180 driver" files and the same thing happened too .. *NADA NADA

---

### Post by Crafty Kisses on 2008-08-07
Try this:
```
sudo ifdown wlan0 #or whatever your wireless card’s interface id is
```

Supposedly there are issues with this type of wireless card, and  the drivers are very difficult to install, but try this:
```
Click on the "Routes" tab and enter the ip address of your Access Point as your Default Gateway IP (or whatever IP address your default gateway is).
Click apply, click **ok**
```

Not sure if I gave this to you, but my interface looks like this:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto wlan0
iface wlan0 inet static
pre-up ifup wlan0
pre-up ifdown wlan0
wireless-essid {your ess id}
address 10.0.0.1
netmask 255.255.255.0
gateway {gateway address}
mode Managed
ap {mac address of your access point}
wireless-key {your encrypted wireless key}
```

Hope this helps, and like I said before anymore problems, let me know.

---

