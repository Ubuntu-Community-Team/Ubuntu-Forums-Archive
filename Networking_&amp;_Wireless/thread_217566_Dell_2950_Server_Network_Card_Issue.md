---
title: "Dell 2950 Server Network Card Issue"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by GeoffNewnham on 2006-07-17
Hi,

when installing Ubuntu 6.06 on a Dell 2950 Server with Broadcom NetXtreme II 5708 Gigabit Ethernet NIC the install routine says it cannot see any network cards in the server. Does anyone know how I can resolve this issue?

Thanks

Best Regards

Geoff

---

### Post by Liam on 2006-07-17
That should be handled by the bnx2 driver.

Does it show up when you do an lspci?

You might also want to try loading it manually. Try:

# modprobe bnx2

---

### Post by Grizzly_Adams on 2006-07-30
G'day.

I have the same issue.  I have a shiny new Dell 2950 that I am having difficulty getting to work with Ubuntu (I will post full details in another thread).

One of the issues I am having is the network card, I tried what you suggested and here is the output:

# lspci | grep -i broad
 PCI bridge: Broadcom: Unknown device 0103 (rev c2)
 Ethernet controller: Broadcom Corporation: Unknown device 164c (rev 11)

I can see both ports if a do a 'ifconfig eth#', however I cannot bring them up.

---

### Post by Grizzly_Adams on 2006-07-31
Problem solved.

Ubuntu does not detect the network cards during installation, however it is possible to activate them after first boot by adding the necessary entry for the interface in the /etc/network/interfaces file, then ifup'ing the interface.

---

### Post by hogman23 on 2006-11-07
So what exactly did you put in the interfaces file to make this work?

---

### Post by peacefrog on 2006-12-08
> **hogman23 said:**
> So what exactly did you put in the interfaces file to make this work?

Yes, Grizzly could you elaborate a little on your reply above. TIA!

^ Noob

---

### Post by michaelcoburn on 2006-12-13
> **hogman23 said:**
> So what exactly did you put in the interfaces file to make this work?

For a static IP address assignment:

 [FONT="Courier New"]vi /etc/network/interfaces[/FONT]

then

[FONT="Courier New"] auto eth0
 iface eth0 inet static
 address 10.10.51.79
 netmask 255.255.254.0
 network 10.10.50.0
 broadcast 10.10.51.255
 gateway 10.10.50.1[/FONT]

This should get you going.  don't forget to restart networking:

 [FONT="Courier New"]/etc/init.d/networking restart[/FONT]

It will automagically load bnx2 module.  Neat, eh?

---

