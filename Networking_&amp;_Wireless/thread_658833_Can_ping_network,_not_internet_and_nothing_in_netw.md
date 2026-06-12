---
title: "Can ping network, not internet and nothing in network setting"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by FFMG on 2008-01-05
Hi, 

My setup:
Win Vista ultimate connected to the net, (2 other windows machine are connected fine).
xUbuntu laptop connected to the Windows machine
All the machines connect to the net via ICS, (from the VISTA machine).

- xUbuntu can ping the windows machine, (192.168.0.1) and the windows machine can ping the xUbuntu machine, (192.168.0.102)
- The xUbuntu machine cannot go onto the internet.

But when I look at the network, (Aplication ->System ->Network), there is nothing.
I mean the dialog box appears, but with nothing in it.
The 'location' dropdown list is empty, the 'connections' tab is empty.

When I click on the Network icon, (top right hand toolbar, next to exit button), and select the manual configuration I do get 'Wired connection' and 'Modem connection', but it does not help at all.

So, something is definitely not right here.
How can I remove/re-install my network?

What do you suggest I do?

FFMG

---

### Post by tehet on 2008-01-05
Can Xubuntu ping IPs on the net or can you browse to google with 64.233.187.99?

---

### Post by FFMG on 2008-01-05
> **tehet said:**
> Can Xubuntu ping IPs on the net or can you browse to google with 64.233.187.99?

No xUbuntui can only ping local ip, (192.168.0.1).
It cannot ping the net.

FFMG

---

### Post by Predator[23rd] on 2008-01-05
how is your network card configured, i.e. how does your */etc/network/interfaces* file look like?

---

### Post by FFMG on 2008-01-06
> **'Predator[23rd] said:**
> how is your network card configured, i.e. how does your */etc/network/interfaces* file look like?

```

auto lo
iface lo inet loopback

# The primary network interfaces
auth eth0
#iface eth0 inet dhcp

```

As I said I can ping the main computer, (the windows VISA box)

FFMG

---

### Post by Predator[23rd] on 2008-01-06
change our */etc/network/interfaces* file to either make eth0 to accept DHCP configuration or set IP etc. manually.

[I]auto eth0
iface eth0 inet dhcp[/I]

or

[I]auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
[/I]

then restart your network with **sudo /etc/init.d/networking restart**

hope it helps....

---

### Post by FFMG on 2008-01-06
> **'Predator[23rd] said:**
> change our */etc/network/interfaces* file to either make eth0 to accept DHCP configuration or set IP etc. manually.

[I]auto eth0
iface eth0 inet dhcp[/I]

or

[I]auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
[/I]

then restart your network with **sudo /etc/init.d/networking restart**

hope it helps....

Thanks for the help.

But neither seems to help.

VISTA can ping xUbuntu, (192.168.0.10)
xUbuntu can ping VISTA, (192.168.0.1)
but xUbuntu cannot ping [www.google.com](www.google.com)

Also the xUbuntu machine does appear in the VISTA network list, even though VISTA can ping it.

FFMG

---

### Post by FFMG on 2008-01-06
> **'Predator[23rd] said:**
> change our */etc/network/interfaces* file to either make eth0 to accept DHCP configuration or set IP etc. manually.

[I]auto eth0
iface eth0 inet dhcp[/I]

or

[I]auto eth0
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
[/I]

then restart your network with **sudo /etc/init.d/networking restart**

hope it helps....

Sorry, I fixed it, (with your help).

I joined a new ISP and by default my internet sharing was disabled.
All I had to do was enable it and it all worked fine.

For the record, when you enable Internet sharing VISTA disables the other.
So if you have 2 accounts, (as I do), only one can be used for sharing.

Thanks for all the help.

But I am still not sure why VISTA can ping xUbuntu but does not have it listed in the connections list.

FFMG

---

### Post by Predator[23rd] on 2008-01-06
> **FFMG said:**
> But I am still not sure why VISTA can ping xUbuntu but does not have it listed in the connections list.

FFMG

Don't ask. I am still puzzled why my XP computer can access files on my VISTA computer while VISTA can't even see XP on the network. I turned all the file sharing stuff down to a minimum and still can't see XP in the list ...

VISTA is total crap! XP is the best OS microsoft produced so far. and frankly, XP is still good in comparison with LINUX. not better, but not worse either ...

for professional desktop use I would recommend XP. although ubuntu/suse/fedora are catching up fast ... which is GREAT!

---

