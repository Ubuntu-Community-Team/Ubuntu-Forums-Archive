---
title: "Bewildered by router/ip setup on my network"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by herbster on 2007-07-03
I have this Feisty box I'm on and a networked Windows XP box on my home network, using a Linksys WRT54GS router.

My box's ip is 192.168.1.1, and my XP box is 192.168.1.105. Initially I wanted to change the XP box's ip to x.x.x.102 as it mysteriously changed to .105, but then I was googling and read up on static IPs and such, but I have to say I am confused as hell.

What I want to know is:
1. Is setting a static IP a good idea?
2. If so, how do I do it in Ubuntu? And what could I set it to?
3. How does it affect my networked XP PC ? (Does it stay at 192.168.1.105)
4. How do I set up a static ip on the XP PC ?

TIA for any help!

---

### Post by arvevans on 2007-07-03
[COLOR="Blue"]I have this Feisty box I'm on and a networked Windows XP box on my home network, using a Linksys WRT54GS router.

My box's ip is 192.168.1.1, and my XP box is 192.168.1.105. Initially I wanted to change the XP box's ip to x.x.x.102 as it mysteriously changed to .105, but then I was googling and read up on static IPs and such, but I have to say I am confused as hell.[/COLOR]
[COLOR="Blue"]
What I want to know is:
1. Is setting a static IP a good idea?[/COLOR]
[INDENT]Setting up your IP addresses statically versus dynamically helps if you are doing things that require that your IP address always be the same.  This is especially useful if you have some "Internet Appliances" which expect your PC to always have the same address.

Running a dynamic IP address allows PC's to be plugged into your LAN (Local Area Network) and automatically be assigned an available IP address.  There is no speed advantage or disadvantage of having static or dynamic IP addresses[/INDENT]
[COLOR="Blue"]2. If so, how do I do it in Ubuntu? And what could I set it to?[/COLOR]
[INDENT]There are two basic ways to set up a static IP address.  You can have your router/hub assign a specific IP address based on the hostname you assign to your computer.  If you want your hub/router to set up a static IP address, you have to configure that into the hub/router device.  This involves setting it to assign a specific IP address to a specific host named computer...much like it does for dynamic IP addresses.  

The other way to assign a static IP address is to use the CLI (Command Line Interface) command called "ifconfig", or one of the GUI front-ends for that command.  Here you would set up a specific IP address for your computer, but this must be within the range of addresses that are supported on your LAN by your hub/router.  In your case this would normally be IP addresses in the range of 192.168.1.1 to 192.168.1.254.  Addresses ending in 0 or 255 are reserved for broadcast functions.  If you do assign your own hard-coded IP address, be sure that you don't assign the one that belongs to your hub/router, because that would really confuse things. [/INDENT]
[COLOR="Blue"]3. How does it affect my networked XP PC ? (Does it stay at 192.168.1.105)[/COLOR]
[INDENT]You can use any available IP address that falls within the range supported by your hub/router, as long as you don't assign the same address to multiple PCs.  This is where using dynamic IP address assignment (DHCP) helps, because it will not assign two PC's the same address.  Using DHCP also lets you automatically assign DNS server address' for your computer, rather than having to manually assign them.[/INDENT]
[COLOR="Blue"]4. How do I set up a static ip on the XP PC ?[/COLOR]
[INDENT]I have not used MS Operating Systems for several years (100% Linux here), but it is in the /settings/control panel/network configuration area.  There you have options for "Automatically Assign Address (DHCP)" or un-click that and enter your own IP address, gateway address, and DNS server addresses.[/INDENT]

**_MINI-Tutorial:_**

IP addresses are usually represented by a set of 4 dot-separated "octets" (don't worry about the "octet word" it is geek-speak for octal word).  Each dot-separated number represents a list of 255 possible address sets (0 thru 255), with addresses 0 and 255 reserved for administrative and broadcast functions.

Along with the IP address is a "netmask" number, also a set of 4 dot-separated numbers.  This is a mask that tells equipment which set of numbers should be looked at for routing traffic on the local network (i.e. 255.255.255.0 indicates to use only the lowest significant bits, or x.x.x.1 to 255 to route traffic between devices on your LAN).

In addition to the netmask there is the "gateway" address.  This is normally the IP address of your hub/router and tells your PC where to send traffic that is destined for outside your LAN, or possibly for other computers on your LAN.

_._

---

### Post by herbster on 2007-07-03
^^^^^ Thank you so much for that, I am beginning to really understand how the process works now. I am going to stick with dynamic IPs as I really have no use for static with regards to anything needing my PC to have a static IP.

However, I am still having trouble figuring out how to change my XP networked box from 192.168.1.105 back to 192.168.1.102 (I have no idea how the 102 changed to 105, did in just the last day or two). I have gone into my router setup menu in firefox but can't find where it says I can do this, any ideas ???

---

### Post by coke on 2007-07-03
The linksys router's dhcp server assigns leases starting at 100. The range is usually 192.168.1.100 to 192.168.1.150.

Most likely what happened is your lease on your XP machine for your .102 IP expired and your linux box when in and made a DCHPDISCOVER and was offered the .102 IP since there was no valid lease on it any longer.

There really is no rhyme or reason that the linksys dhcp works the way it does. It is not like that when you run your own dhcp server (linux/unix/sun/etc)

---

### Post by raptor95368 on 2007-07-07
you might also consider setting up permanent leases for machines that remain connected and allow other mobile systems to obtain dynamic leases...this will ensure that even if you power off your desktop machines, they will come back online with the same IP address, without setting a static IP on the ethernet adapter....just a suggestion with the linksys...they seam to be touchy on maintaining leases and connections

---

