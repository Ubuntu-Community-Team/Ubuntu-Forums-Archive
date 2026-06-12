---
title: "not recognized second ethernet card"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by MadMaster on 2006-08-15
Hi there, 

I've come up to this issue when I installed Ubuntu.

I have a Realtech 8139 card onboard and a second one with the same chip on PCI (you know 8139). The problem is that ubuntu did not initialize the second (PCI) ehtenrnet card, althoug lspci saw it. It just did not show up in ifconfig.

Will appreciate help.

TIA.

---

### Post by louis_nichols on 2006-08-15
ifconfig only shows configured connections (not necessarily cards, as you can define more than one connection on one card). Correction: not configured, but activated. You can configure all parameters of a connection, IP and all, but won;t see it with ifconfig unless it's active.

The question is whether it shows up in System>Administration>Networking. If it does, then you should configur it over there and check the option to set it active, i.e. activate it at boot.

---

### Post by MadMaster on 2006-08-15
Hello,

Well, it's not listed there.. Can you hint me how to activate it at boot. May be some example.

---

### Post by louis_nichols on 2006-08-15
Actually... I have to look into that, as I've never done it before myself.

---

### Post by andrebtoda on 2006-08-23
I have the same problem
please help us!!!

---

### Post by louis_nichols on 2006-08-24
Ok. Through a strange chain of events, I ended up having pretty much the same problem. Now, the following will work only if the card is shown by the command lspci. If it isn't, then you have to check it's plugged correctly, as it's quite unlikely there won't be a driver for it.

So here goes:

[LIST=1]
[*]Make a backup of the file /etc/networking/interfaces
```
sudo cp /etc/networking/interfaces /etc/networking/interfaces.bak
```
[*]Open it for editing:
```
gksudo gedit /etc/networking/interfaces 
```
[*]Now this step depends on whether you have a static IP or one assigned dinamically by your ISP through DHCP. In the latter case, you have to add 2 lines at the end of this file:
```
iface eth1 inet dhcp
auto eth1
```
Else, if you have a static IP, you have to add several lines, like this:
```
iface eth1 inet static
address xxx.xxx.xxx.xxx
netmask yyy.yyy.yyy.yyy
gateway zzz.zzz.zzz.zzz
auto eth1
```
where xxx.xxx.xxx.xxx is your IP number and yyy.yyy.yyy.yyy is the netmask. zzz.zzz.zzz.zzz will be the gateway number.
[*]Run the following command:
```
sudo /etc/init.d/networking restart
```
[/LIST]

Everything should work now. You should be able to see the network card in System>Administration>Networking and further configure it there, if you want.

---

### Post by andrebtoda on 2006-08-24
Hi man!
Thanks for the help...

But that doesn't works here...

The result of my lspci about my ethernet card is:

0000:00:08.0 Ethernet controller: Unknown device 1904:8139 (rev 01)

Help me please!!!

](*,) :( ](*,)

---

### Post by louis_nichols on 2006-08-24
> **andrebtoda said:**
> Hi man!
Thanks for the help...

But that doesn't works here...

The result of my lspci about my ethernet card is:

0000:00:08.0 Ethernet controller: Unknown device 1904:8139 (rev 01)

Help me please!!!

](*,) :( ](*,)

What kind of ethernet card is it?

---

### Post by andrebtoda on 2006-08-24
Hi there

Thanks for the help!

My ethernet card is a pci Realtek lan card...
If you need more information about this i can post that later. (I'm in my office now :-D )

---

### Post by louis_nichols on 2006-08-24
Realtek should work pretty well. I have one on board and works great.

Are you sure it is plugged well? Does it work in other OS's?

---

### Post by andrebtoda on 2006-08-24
This card works fine on my Windows XP :sad:

---

### Post by louis_nichols on 2006-08-24
It sounds like you don't have the driver... although it should be there. Can you be more specific on the exact model of the Realtek card? We can search which driver may be compatible or something.

---

### Post by andrebtoda on 2006-08-24
Hi dude

My Ethernet card is a "Realtek RTL8193 PCI Fast Ethernet Adapter"
Thats is very strange...
I search for the driver in the site...and i found "8139too"
[http://www.realtek.com.tw/downloads/downloads1-3.aspx?series=16&Software=True#16Unix%20(Linux](http://www.realtek.com.tw/downloads/downloads1-3.aspx?series=16&Software=True#16Unix%20(Linux))

](*,) ](*,) ](*,) ](*,) ](*,) 
:neutral: :neutral: :neutral:

---

### Post by GTvulse on 2006-08-25
> **MadMaster said:**
> Hi there, 

I've come up to this issue when I installed Ubuntu.

I have a Realtech 8139 card onboard and a second one with the same chip on PCI (you know 8139). The problem is that ubuntu did not initialize the second (PCI) ehtenrnet card, althoug lspci saw it. It just did not show up in ifconfig.

Will appreciate help.

TIA.
By default the kernel loads the 8139c driver which may not work with your second card (ther are two variants of the 8139 chipset).

With your favorite text editor create a file with whatever name you want in /etc/modprobe.d, for example:
```
sudo <editor> /etc/modprobe.d/second-card
```
And add the following line:
```
alias eth1 8139too
```
Save and exit. Reboot.

Now open the networking tool (assuming you use GNOME) and you'll find the interface there ready to be configured. Unless the chipset is not supported (I doubt it).

---

### Post by andrebtoda on 2006-08-25
Thanks man

I Will try this later and post my result here!:D

---

### Post by MadMaster on 2006-10-08
Well tried this with the alias... and no success... although dmesg said

---
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179590.380000] 8139cp: pci dev 0000:00:0f.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[17179590.380000] 8139cp: Try the "8139too" driver instead.
[17179590.388000] 8139too Fast Ethernet driver 0.9.27
[17179590.388000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179590.388000] eth0: RealTek RTL8139 at 0xe8a12000, 00:0d:61:2d:84:c5, IRQ 217
[17179590.388000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
------

---

### Post by Alexfield on 2008-03-21
Hi Folks,

I had this issue. The card 01:01.0 Ethernet controller: Unknown device 1904:8139 (rev 01) is NOT Realtek 8139
It is a Silan SC92031 PCI Fast Ethernet Adapter
You need the correct driver for it. It is available in Kernel version 2.6.24.3
:KS

---

