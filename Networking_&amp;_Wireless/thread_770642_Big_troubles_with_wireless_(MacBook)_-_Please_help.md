---
title: "Big troubles with wireless (MacBook) - Please help!!!"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by arseniy on 2008-04-27
I've been working on this for like two days and still can't get it. So I turn here.

Here's the story: I installed Gutsy on a MacBook (clean install, nothing but Ubuntu is present). I downloaded and installed successfully ndiswrapper (1.52). I downloaded the Atheros wireless card driver that someone posted online (coming from the Boot Camp "Windows Drivers" that you get when you use Boot Camp to make the second partition). I unrar-ed that driver (AtherosXPInstaller.exe) and got a whole bunch of stuff extracted to a directory I made for it (~/atheros), including "net5416.inf". So I opened a Terminal and ran this:

```
sudo ndiswrapper -i ../atheros/net5416.inf
```

and got this output:

```
installing net5416 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
```

so everything was installed fine. I even checked it with:

```
sudo ndiswrapper -l
```

and got:

```
net5416 : driver installed
```

so everything *was* fine. Then I did ```
sudo modprobe ndiswrapper
``` like the instructions I was following told me to do, and all was fine. But here's the weird part... I run ```
iwconfig
``` and all I see is:

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

Does this mean that my wireless card is broken or something? Why can't iwconfig see it???

Here's some more information. MacBook 13" Core 2 Duo 2.0GHz, 2.0GB RAM. And here's some history that I hope will help:

Before ndiswrapper (and the cause of me having to install ndiswrapper) was an attempt at madwifi. I downloaded, made, and install version 0.9.4, and I did everything up to this next step correctly. I ran ```
modprobe ath_pci
``` and that was fine, and then I did this:

```
wlanconfig ath0 create wlandev wifi0 wlanmode sta
```

and it said something like (I can't say exactly b/c I don't have it now) "cannot *verb* ioctl: No such device".

Please help!

---

### Post by arseniy on 2008-04-27
Anyone?

---

