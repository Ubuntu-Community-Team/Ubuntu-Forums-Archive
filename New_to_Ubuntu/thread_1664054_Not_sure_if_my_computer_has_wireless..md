---
title: "Not sure if my computer has wireless."
date: 2011-01-10
forum: New to Ubuntu
---

### Post by thewasteland on 2011-01-10
I just got a new laptop and installed Ubuntu 10.10 on it; I've never used Ubuntu before.

When I press the dropdown menu for wired/wireless networks, there is absolutely no mention of wireless networks, only wired ones. When I typed "lspci | grep Wireless" into the Terminal, it came up with absolutely nothing.

Does this mean that I don't have a wireless card, or that I have one and just don't have the drivers for it? I'm pretty sure this laptop is supposed to have wireless. Someone on another forum told me to type in "lspci | grep -i 'net'" to see if I needed any wireless drivers, it came up with "04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)". I have no idea what that means though.

Can anyone please interpret this situation for me and, if I need drivers, tell me where to find them? Thanks in advance.

---

### Post by endotherm on 2011-01-10
try posting back the output of:
```
ifconfig -a
sudo lshw -C Network
```
and hopefully that will tell us. the realtek NIC that shows up in your lspci output is a wired connection.

---

### Post by cottfcfan on 2011-01-10
This might help:
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by endotherm on 2011-01-10
> **cottfcfan said:**
> This might help:
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)
thats some good advice for a wired connection problem. in this case however, we are more worried about the wireless or lack thereof.

---

### Post by thewasteland on 2011-01-10
> **endotherm said:**
> try posting back the output of:
```
ifconfig -a
sudo lshw -C Network
```and hopefully that will tell us. the realtek NIC that shows up in your lspci output is a wired connection.

micael@micael-TW8-SW8-DW8:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:8b:11:61:3e  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe11:613e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:172268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202270234 (202.2 MB)  TX bytes:45811763 (45.8 MB)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

micael@micael-TW8-SW8-DW8:~$ sudo lshw -C Network
[sudo] password for micael: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:11:61:3e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.1 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:1000(size=256) memory:92410000-92410fff memory:92400000-9240ffff memory:92420000-9242ffff

I wish I had any idea what any of that means.

---

### Post by endotherm on 2011-01-10
I'm not seeing any sign of a wireless card.

ifconfig -a just prints out info about all the network cards present in your machine, even those that are disabled. from that I can see that you have only the one nic (eth0), and a loopback interface (lo0)

lshw is "List Hardware" and "-C Network" tells it to skip all the info except that which pertains to the category "Network". 

it is possible that your box has a wifi card that the kernel can't see, but that is out of my element. i would start by googling the exact model number of your box and see if the manufacture says anything about whether it;s there or not, and if so, try to find out what kind of card it is. then google about a bit more to find advice on installing drivers for it.

---

### Post by thewasteland on 2011-01-10
> **endotherm said:**
> I'm not seeing any sign of a wireless card.

ifconfig -a just prints out info about all the network cards present in your machine, even those that are disabled. from that I can see that you have only the one nic (eth0), and a loopback interface (lo0)

lshw is "List Hardware" and "-C Network" tells it to skip all the info except that which pertains to the category "Network". 

it is possible that your box has a wifi card that the kernel can't see, but that is out of my element. i would start by googling the exact model number of your box and see if the manufacture says anything about whether it;s there or not, and if so, try to find out what kind of card it is. then google about a bit more to find advice on installing drivers for it.

Huh. That sucks. I've basically Googled every phrase on any sticker attached to my laptop and nothing. It was a gift and came with almost nothing other than the laptop box, so I have no way of delving further.

Thanks a lot anyway.

---

### Post by mcduck on 2011-01-10
Those outputs just show the detailed information about your wired network card. (Realtek RTL8111/8168B gigabit ethernet card, and it's currently connected)

So based on that info you don't have a wireless, or at least it's missing the drivers and doesn't show because of that.

However I'd find it rather amazing if you'd managed to get your hands on a new laptop that doesn't have a wireless network card. If you can tell the computer's model we can probably check if it actually has a wireless card, and maybe even tell what you need to do to get it working...

---

### Post by thewasteland on 2011-01-10
> **mcduck said:**
> Those outputs just show the detailed information about your wired network card. (Realtek RTL8111/8168B gigabit ethernet card, and it's currently connected)

So based on that info you don't have a wireless, or at least it's missing the drivers and doesn't show because of that.

However I'd find it rather amazing if you'd managed to get your hands on a new laptop that doesn't have a wireless network card. If you can tell the computer's model we can probably check if it actually has a wireless card, and maybe even tell what you need to do to get it working...

Uh, I don't think it's a new laptop. My friend got it as a gift from the guy that owns this computer place, so it could be pretty old. There's little to no information about it online, however, I have found a couple of people selling it claiming it has wireless.

It's a Sahara Imagebook 15WCS, has an Intel Celeron M processor. Another sticker on the bottom claims it has "Agere Delphi D40" somethings, I don't really know what that one corresponds to.

---

### Post by mcduck on 2011-01-10
I tried to check the model, and based on what I was able to gather it does seem to have a wireless network card, although I really couldn't find out which one (the Sahara computers website throws some PHP/database errors when trying to get into support section).

(The Agere Delphi D40 seems to be a modem.)

---

### Post by thewasteland on 2011-01-10
> **mcduck said:**
> I tried to check the model, and based on what I was able to gather it does seem to have a wireless network card, although I really couldn't find out which one (the Sahara computers website throws some PHP/database errors when trying to get into support section).

(The Agere Delphi D40 seems to be a modem.)

K thanks a lot, I'll keep trying.

---

### Post by walt.smith1960 on 2011-01-10
If it were me and I just wanted wireless, I'd install a USB WiFi adapter.  Obscure wireless adapters can be a tricky even when it's seen by lspci. There are several good USB choices available.  If you want the challenge, this may be a good one.:)

---

### Post by wojox on 2011-01-10
What's this show:

```
lsmod | grep 816
```

Try the driver here [Realtek Software: Drivers & Utilities]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

---

### Post by thewasteland on 2011-01-11
> **wojox said:**
> What's this show:

```
lsmod | grep 816
```Try the driver here [Realtek Software: Drivers & Utilities]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

It gives:
r8169                  36489  0 
mii                     4425  1 r8169

However, I phoned the manufacturer this morning and they absurdly don't have any drivers on hand for Ubuntu. I asked them to give me the Windows drivers, which I'm currently downloading. Does anyone know if installing them with Wine will work?

---

### Post by amsterdamharu on 2011-01-11
You should know the make and model of your wireless:

```
lspci
lsusb
```will list pci and usb devices (my laptop has an internal wifi listed under usb).

Then there are key combinations to switch the wireless on and off so check your fn key and the pictures on your function keys.

Then there is the command rfkill to enable and disable wireless cards, you can check out the output of 
```
sudo rfkill list
```

If no Linux driver is available then [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") could work, you need the right driver for it though.

---

