---
title: "Eth0 work only for a few"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by dr.lnx on 2006-10-30
hi after i upgrade to edgy my connections are not working good
if i use eth1(wireless) it works fine if i have only eth1 up
if i eth0(ethernet) the first few minutes workis fine but then the device works no more, she say no errors or nothings only i can't surf no more
no connections in any case or whit any protocol, after a few that she dosn't work she became again to work for another few..
what could i do?

sorry for my english!

---

### Post by Paul41 on 2006-10-30
Run this to see if you ethernet card if Tulip based:
```
lspci | grep Eth
```
If it is this should fix the problem.
[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by dr.lnx on 2006-10-30
this is the result
```

root@rix:/usr/local# lspci | grep Eth
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)

```

is it?

---

### Post by Paul41 on 2006-10-30
No, it doesn't look like it is Tulip based.

---

### Post by Iowan on 2006-10-30
After it quits, run **ifconfig** to see if the IP address may have mysteriously changed.

---

### Post by GCR on 2006-10-30
Do youuse DHCP to acquire the I.P. or is it s static IP?

Whats the output of pingging a site?

---

### Post by legandir88 on 2006-10-30
Hi, yeah I've been having exactly the same problem as dr.lnx. I had this problem with ubuntu 6.06 as well although now in edgy it takes longer before the connection cuts out. I'm using a SZ2VP/x with the Marvell 88E8036 PCI-E Fast Ethernet Controller.

When i tried to fix the problem in 6.06 i read that it was due to a problem with the skge driver (not sure whether I got that right) and that I needed to install a new driver from [http://www.syskonnect.com/support/driver/]("http://www.syskonnect.com/support/driver/") however, when i tried to install the driver I get this :

```
install.sh: 69: Syntax error: "(" unexpected
```

I've found that entering the following into the terminal gives you a few minutes of connection time before it cuts out again:

```
sudo ifdown eth0 && sleep 2 && sudo ifup eth0
```

---

### Post by Eric Aarts on 2006-10-31
I also have the same problem on my Sony Vaio SZ2XP with the Marvell 88E8036 PCI-E Fast Ethernet Controller.

I have the problem with SOME kernelversions in Dapper and with the kernel in Edgy.

And ONLY when the kernel supports the PRO/Wireless 3945ABG network...

When I start Edgy with the 2.6.15-26-686 kernel, I have NO wireless, but the wired connection is stable.

So: now I can't use wireless and wired together.

???

---

