---
title: "HP laptop dv2815nr wireless problem"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by draginx on 2008-05-05
I have searched through google, #ubuntu on freenode and efnet, and tried these forums to find a solution on how to get the network card on a hp dv2815nr laptop, but have not been able to find a successful solution. I am new to linux, so please bare with me. If anyone can help i would greatly appreciate it. I am using Ubuntu Hardy

=)

---

### Post by Ayuthia on 2008-05-05
Can you go to the termial and post the results to lspci -nn?  It will list out your pci cards and we can identify your wireless card. From there we try to find a guide that can help.

---

### Post by draginx on 2008-05-05
I'm assuming you just want the network controller

04:00.0 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

My laptop isn't connected to the internet (I'm on my desktop now) So copying + pasting isn't available ;)

[EDIT]
I also need this laptop to go from using wires to connect to an internet, to using wireless every now and then (so going back and forth should be available)

---

### Post by Ayuthia on 2008-05-05
I am not for sure if this is the right one or not because it says that it is the USB Controller.

Can you do the following:
```
lshw -C network
```
Let me know if the "product" matches with the information that you posted for lspci -nn.

For example, my lspci -nn for my wireless is:
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

My lshw -C network shows:
WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 11:aa:22:bb:33:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.101 multicast=yes wireless=IEEE 802.11g

You will notice that the product: matches with the name in my lspci -nn information (BCM94311MCG wlan mini-PCI).

If it is the same, just let me know.  If it isn't can you post the lspci -nn that matches the product: in lshw -C network?

Most likely, you have a Broadcom card.  I am just trying to make sure that it is not a 4311 rev 02 or a 4312 rev 02.  If they are not, there is an easy way to download the files needed to get your wireless going.  If they are, it will be a little more complicated, but still possible.

Do you have the LiveCD for Hardy?  It will be used to install either b43-fwcutter or ndiswrapper.

---

### Post by draginx on 2008-05-06
daniel@daniel-laptop:/tmp$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:51:a2:b1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.97 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


That's my results, I have ndiswrapper installed, but please let me know what to do =)

---

### Post by Ayuthia on 2008-05-06
What have you done so far with the ndiswrapper installation?  Have you blacklisted b43?  Let's go ahead and verify that ndiswrapper is installed and loaded the driver:
```
ndiswrapper -v
ndiswrapper -l
```The first one will give us the version of ndiswrapper and verify that it does not have any error messages.  The second one lists the driver that is being used.

Your lshw -C network shows that it is UNCLAIMED so no driver has been installed.

---

### Post by draginx on 2008-05-06
daniel@daniel-laptop:/tmp$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 

daniel@daniel-laptop:/tmp$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4315) present

---

### Post by Ayuthia on 2008-05-06
Ok.  Let's try:
```
lsmod|grep -i -e b43 -e ssb -e ndiswrapper
```
If nothing returns, we can try loading ndiswrapper:
```
sudo modprobe ndiswrapper
```

---

### Post by draginx on 2008-05-06
OK, I did the sudo modprobe command, and now it can see all of the available wireless networks. Which is good, but the only problem now is that when I try to connect to my router/modem/etc. I enter in the correct passkey and it tries to connect, but it fails (it also says "Trying to connect to (null)" when I hover over the network icon when I'm trying to connect.

Any ideas?

---

### Post by Ayuthia on 2008-05-06
You might want to try to connect without encryption first.  Is that possible?  It will help us determine if we have a problem connecting with encryption or just connecting.

---

### Post by draginx on 2008-05-06
I can cponnect to it without any encrypted passwords (but when I need the password, I cant connect to it)

---

### Post by Ayuthia on 2008-05-06
> **draginx said:**
> I can cponnect to it without any encrypted passwords (but when I need the password, I cant connect to it)
Which type are you using (WEP/WPA)?  Not sure if I can help much with this, because I don't have much experience in either (I live in the country so encrypting my router would only accomplish me in locking out my family...).

---

### Post by draginx on 2008-05-06
I'm using WEP, by living in the country, do you mean the US? If so, so do I and why wouldn't I need the encryption option?

---

### Post by Ayuthia on 2008-05-06
> **draginx said:**
> I'm using WEP, by living in the country, do you mean the US? If so, so do I and why wouldn't I need the encryption option?
You most likely need encryption.  I was saying that I don't need it where I am located because I am too far away from anyone else that they can't get to my signal.  That is the reason why I don't have much experience with it.  I just played around with WPA yesterday.

You might try doing it from the Terminal:
```
sudo iwconfig wlan0 essid <enter name> key <passkey>
sudo dhclient wlan0
```

---

