---
title: "Unable to get online"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by Cremaster1 on 2010-12-16
I could use some help here. I am trying out Ubuntu on a cd disk. It will boot on my laptop.

I am unable to use my wireless and get on line.

Ubuntu ask for stuff that I understand to edit the connection, like SSID, mac addresses, ad hoc and other stuff. Then it wants a password for some kind of key ring.

Does the try out version let me get on line?

Could someone PLEASE help? I will run ipconfig and post it here, I will dig into my wireless router for what ever settings I need. I don't understand. I have spent hours reading the guides in the forum. Maybe I have missed something. I will commit to doing what I need to do here if someone can please rather than post a hint or incomplete answer just stick with me. I will call you, hop on one foot, or stick my head in the toilet if you think it will help. I just don't want to give up family time if I am wasting this time.

I need a hand holder. 

Thank you.

---

### Post by sydbat on 2010-12-16
> **Cremaster1 said:**
> I could use some help here. I am trying out Ubuntu on a cd disk. It will boot on my laptop.

I am unable to use my wireless and get on line.

Ubuntu ask for stuff that I understand to edit the connection, like SSID, mac addresses, ad hoc and other stuff. Then it wants a password for some kind of key ring.

Does the try out version let me get on line?

Could someone PLEASE help? I will run ipconfig and post it here, I will dig into my wireless router for what ever settings I need. I don't understand. I have spent hours reading the guides in the forum. Maybe I have missed something. I will commit to doing what I need to do here if someone can please rather than post a hint or incomplete answer just stick with me. I will call you, hop on one foot, or stick my head in the toilet if you think it will help. I just don't want to give up family time if I am wasting this time.

I need a hand holder. 

Thank you.It is possible that your wireless card needs proprietary drivers (Broadcom especially) and is the reason you cannot get online with the LiveCD. If you can plug your laptop into your network with an Ethernet cable, you should be able to get online.

However, as far as I know, you cannot install proprietary drivers while running the LiveCD, because they require a restart and as soon as you restart, you begin from scratch when loading the LiveCD again. If you can boot from a USB stick, there might be other options.

---

### Post by nothingspecial on 2010-12-16
You need to post your wireless card for people to help.

In your menu, go accessories > terminal

and type

```
sudo lshw -C network
```

Then copy and paste the output in a new post here.

---

### Post by Cremaster1 on 2010-12-16
***Yes it is a broadcom****

I will attempt to "plug her in" and see what that brings us.

I will run that code and post results. I am hoping that it will give me sometype of copy paste option and that I can save the info in a file.

Thank you.

---

### Post by Cremaster1 on 2010-12-16
Here we go. I am on line via ethernet.


 *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:44:e4:05
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.192 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:a000(size=256) memory:d0208800-d02088ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:b6:85:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
ubuntu@ubuntu:~$

---

### Post by Daveth on 2010-12-16
this then.....?

[HTML]http://ubuntuforums.org/showthread.php?t=1490717[/HTML]

---

### Post by Cremaster1 on 2010-12-16
Well I can not really be updating firm ware on my network card just to get a demo OS going?

---

### Post by sydbat on 2010-12-17
> **Cremaster1 said:**
> Well I can not really be updating firm ware on my network card just to get a demo OS going?Blame Broadcom.

Also, if this were Windows, and you were installing from scratch (not getting a pre-installed, pre-configured computer system with Windows), you would have to do the same things. At least with Linux, you have a (mostly) one-stop repository system to help you out, as opposed to having to search the Internet for all your drivers and firmware (and don't forget all the software).

---

### Post by Cremaster1 on 2010-12-17
Progress Update

I was able to get online via my cable. Worked great! I thank you guys for the ideas. I think that I shall use a formatted drive for any Ubuntu install. I have several on the shelf.

If anyone thinks there is anything else to accomplish in this thread please feel free to add. I will check it once more in a few days.

I want to apologize for some earlier post. I was frustrated. You guys are great, here to help, and deserve better than I gave in my anger. 

Again, Thank you and I hope I can contribute in the future.

---

