---
title: "Eth0 Don't Work !"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by dantavares on 2006-08-29
I Have a very strange bug in my network card. It is:
In Live CD, my ethernet device (Davicom 9102, is a commom device) works fine but, after instalation don't assing ip by dhcp server, and if static IP address configured, don't ping with anithing machine ip on lan or site address.

Anyone have some idea about this ?

Obs.: In this machine i related a error in my (serial) mouse detection, and grub instalation (error on boot a windows 98) all then is fixed by myself.

Obs2.: Sorry about my bad english :???:

---

### Post by petermck on 2006-08-29
I got the LiveCD yesterday and have the same Davicom 9102 card. I have exactly the same problem as you, it works on the live CD but not on the installed system. I've tried both DHCP and static IP with no luck.
I've also looked from the router side and see no entry in the DHCP client list.
I'm thinking it's some problem with the network card modules (tulip and dmfe). I've had problems getting this card to work before on linux and I think it was a problem with the modules loading and using the wrong IRQ, but it was a long time ago.
The odd thing is this time round is that it works fine on the LiveCD! 
#################
While I was writing this I tested out an idea and it worked.
Do the following in a terminal;
gksudo rmmod tulip
gksudo rmmod dfme
gksudo modprobe dfme

This fixes it. It appears tulip loads after dmfe and takes over the card, but these cards are quite old and seem to like the dfme module more. On the CD its probably loading the other way around for some reason (possibly the different access time?). This seems to be what dmesg shows as well. On the LiveCD these modules seem to come up in the order tulip then dfme, but booting from HDD is the other way around.

I've also added tulip to /etc/modprobe.d/blacklist so it won't load at boot.

---

### Post by SpikeyMike on 2006-08-29
I am having the same problem, I had ubuntu installed and working using static IP, I reinstalled ubuntu because of a hardware change and now I can't get a connection, I have configured the network settings to the same as before but nothing, I can't even ping or access my router from the firefox browser using its ip address.  I also have a wireless network card in the pc that i'm not using, I am using wired ethernet.  I noticed when I used the command lspci | grep Eth that I got the following output:

0000:00:14.0 Bridge: nVidia corporation MCP51 Ethernet Controller (rev a3)
0000:03:09.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0
01b (rev 01)

i'm not sure exactly what it means, is one of these the wireless card and the other the ethernet card?

Thanks in advance

Mikey

---

### Post by dantavares on 2006-08-30
Ok .. works in half ways ... he he ... you want to say "dmfe" ?

well i found in another forums other way to fix this problem on ubuntu under Davicom 910X, works to me: 

type the following in a terminal

```
sudo -s
nano /etc/modules

```

Add a line with this: dmfe
Save a file

now enter in blacklist do this

```
nano /etc/modprobe.d/blacklist
```

Add a line with this: blacklist tulip


Now, let to know if this is **** another nom Davicom Ethernet device pluged in pc ... in my case works.

---

