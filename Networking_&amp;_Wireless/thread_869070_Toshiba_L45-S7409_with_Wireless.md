---
title: "Toshiba L45-S7409 with Wireless"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by noimus on 2008-07-24
Okay hey guys. I just installed linux onto my laptop. Now i cant seem to get the internet running. I am a complete n00b with linux because i just started using it today. I think its a Realtek 8187B Integrated Wireless Card. Well as far as I know the Toshiba L45-S7423 is the same laptop as this one. Their internet and sound devices are the same. So can anyone give me a set of directions so i can set this up? Plus do i have to install Ubuntu to get the internet working or can it work with the live cd.

---

### Post by noimus on 2008-07-24
Anyone? Please i really need your help!

---

### Post by chili555 on 2008-07-24
Please do, in a terminal:```
sudo lshw -C network
```and see if you really have an 8187B. If so, search this forum for the 193 posts on how to get this one going.

I'm pretty sure you can not proceed without an internet connection so you can download additional packages. Is your wired ethernet working?

---

### Post by noimus on 2008-07-24
yes my wired internet is working. okay do i have to install ubuntu to get the internet working or can i just test it in a live cd?

---

### Post by chili555 on 2008-07-24
I'm pretty sure you can do everything in the LiveCD. Just remember, when you reboot, it's all gone.

The reason there are so many posts on the 8187B is not just because it's widely distributed, but because it is fairly difficult to get going. Look for a post that has the all important word: SOLVED and follow directions carefully.

Is yours a USB device? This looks pretty good: [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

---

### Post by noimus on 2008-07-24
can anyone link me to that forum post? how do i know its a usb or not?

---

### Post by chili555 on 2008-07-24
> can anyone link me to that forum post?What do you mean? Did you simply click it?> how do i know its a usb or not?Is it sticking out of a USB port on your laptop? If not, it's not a USB device and is probably not a 8187**B**. What does:```
sudo lshw -C network
```tell us?

---

### Post by noimus on 2008-07-24
its 8139

---

### Post by chili555 on 2008-07-24
The Realtek 8139 is a wired ethernet device. Weren't there two entries, one for wired and one for wireless?

---

### Post by noimus on 2008-07-24
well it shows me RTL-8139/8139C/8139C+

Thats the product. And the description shows me Ethernet Interface.

---

### Post by noimus on 2008-07-24
okay so any luck finding some info?

---

### Post by noimus on 2008-07-24
anyone?

---

### Post by sq0nk on 2008-09-23
Here's the output from that command on my Toshiba L45-S7409.

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1d:60:f2:28:aa
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
$


> **chili555 said:**
> Please do, in a terminal:```
sudo lshw -C network
```and see if you really have an 8187B. If so, search this forum for the 193 posts on how to get this one going.

I'm pretty sure you can not proceed without an internet connection so you can download additional packages. Is your wired ethernet working?

---

### Post by mrtsmith on 2008-11-16
I myself have ran into the same problem with this model, I've followed multiple post to get the wireless to become activated. My next option i think i saw a like to ndiswrapper. Question regarding that is ndis pretty reliable for use. If it is i'll be happy to use it. Also one interesting thing related to this post using Ubuntu 8.04 hardy as its booting up into the prog. as the bar  moves to right I notice the led for the wireless does light up as if ubuntu sees the device but of course without the driver not knowing what to do with it, and as the system blinks to the login prompt it fades away how sad. But yet an enjoyable challenge lol

---

### Post by Marcus Derekus on 2008-11-16
First Right-Click on the Network Manager icon on top right corner of taskbar (looks like two computer moniters).

If there is an enable wireless option make sure it is checked. 

Then left click on icon and choose connection if ubuntu didn't connect already.

if there was no Enable Wireless option when you right-clicked on the icon

got to System<Administration<Hardware Drivers and enable wireless driver

---

### Post by mrtsmith on 2008-11-20
I appreciate the quick response and apparently when I installed this wicd i belive its called it took out the other form of network manager you were speaking of so I went ahead and re-installed the nm and the wireless connects using Wep only although if I right click on the dual-monitors on the taskbar, and choose edit wireless network it does give me the option of Secuirty for wpa personal i enter my passcode there choose set password (it doesn't seem to change, and also does not connect. Also if i left click on the dual-monitors it does give me a list of available networks to connect to i choose mine from the list and it only gives me wep passphrase/hex/ascii as options, as well as leap though not wpa, I do notice in the software install seciton that a wpa-supplicant is installed though, any thoughts from this point thanks all

---

### Post by negrin on 2009-10-31
i test l45 s7409 w/ ubuntu 9.04 and wireless rtl8187b work fine!

---

