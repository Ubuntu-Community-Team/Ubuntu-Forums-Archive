---
title: "Router settings"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by damonc on 2006-10-22
Hello,
I have a question regarding the correct router settings for my home network.

I have the following modem/router: [Netcomm NB5Plus4W]("http://www.netcomm.com.au/ADSL/NB5PLUS4W.php")

The default IP of the modem is 192.168.1.1, but this can be changed. The DHCP in the router assigns IPs of 192.168.1.2 and 192.168.1.3 etc to the connected machines.

I have a Windows laptop that connects via Wireless, a Ubuntu 6.06 desktop (wired) and I am trying to setup a Ubuntu server using the [HowTo Forge tutorial]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06").

Now to my question: The tutorial uses 192.168.0.1 as the IP for the server:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```
Would it be best for me to change the address of the Modem to 192.168.0.1 or to change the interface file?

Also, I have noticed in the modem control panel I can set up LAN groups. what are these and should i be using them? Would I put the server in a group on it's own?

Thanks in advance

---

### Post by damonc on 2006-10-22
As an aside, whould it be better for me to assign static IP address to each of the machines? This would be easy since there are only a handful. What are the pros/cons of doing this?

thanks

---

### Post by CatKiller on 2006-10-22
I'd feel that it's generally best to amend the instructions to my setup rather than the other way round. So instead of 192.168.0.1, use whatever your IP address is. That way you won't get messed up when a different tutorial assumes a different address :)

Whether you use static addresses is more down to personal preference than anything else, especially with a small number of computers. With my router, I get to set the range of addresses that the router assigns for DHCP, so I can manually set the addresses of the computers that I want to something not in the range, and it all works out nicely. Any new computers on the network get assigned an IP automatically, but I can still alias the computers I need to. ssh -X iain@weatherwax always works, and means I don't need to work out which order the computers got turned on.

If you don't have this option I would personally go for static IPs, since it means you always know which computer is which, and you can forward ports and suchlike. Personal preference though.

Welcome to the community.

EDIT: Oh, and whichever computer you're setting up as a server would presumably want a fixed IP address.

---

### Post by damonc on 2006-10-22
Thanks for the reply, CatKiller. This is a bit of a steep learning curve for a linux/networking/server new comer!! But that doesn't mean it's not fun to learn!

I am at work now, but when I get home I will try amending the tutorial.

If I do use 192.168.1.100 as the address for the server, will I also need to edit the network, broadcast and gateway addresses to show 1 instead of 0 in the third set* of numbers?

*Just for my learning, is there a propper name for each set of numbers in an IP address?

---

### Post by CatKiller on 2006-10-22
> **damonc said:**
> Thanks for the reply, CatKiller. This is a bit of a steep learning curve for a linux/networking/server new comer!! But that doesn't mean it's not fun to learn!

I'm quite new to this myself. I installed my first router a couple of months ago, although I had both networked with crossover-cable and pestered my friend with questions previously.

> I am at work now, but when I get home I will try amending the tutorial.

If I do use 192.168.1.100 as the address for the server, will I also need to edit the network, broadcast and gateway addresses to show 1 instead of 0 in the third set* of numbers?

As I understand it, yes. Each block of numbers refines the address a bit more, like each line of your postal address in reverse. The subnet mask defines how "big" the network is, which of the blocks of numbers it should count as significant and which it should assume are the same as its own.

Of course, I might have horribly mangled that description.

> *Just for my learning, is there a propper name for each set of numbers in an IP address?

Not as far as I know. Have a read of Wikipedia or the like on IP addresses, DHCP and port numbers and you'll get a reasonable basic understanding. Probably more than I've got, anyway :-D

---

### Post by mips on 2006-10-23
> **damonc said:**
> 
*Just for my learning, is there a propper name for each set of numbers in an IP address?

Each set of numbers is commonly referred to as an **Octet**. When you convert the numbers to their lowest form, binary, that specific number will be represented by a combination of 8 binary bits. The name Octet stems from the number 8 and in this case it is the 8 binary bits that makes up the number in the range of 0-255.

When you want to refer to one of the specific four Octets you would usually just say first Octet, second Octet etc reading from Left to Right as the left is the MSB (most significant bits) and right is the LSB (least significant bits)

Hope that is clear enough.

---

### Post by damonc on 2006-10-23
thanks mips,
i thought there must be a name, but couldn't find any reference to it while searching around. obviously i was looking in the wrong places!

---

### Post by tturrisi on 2006-10-23
rule of thumb:
Always use a static ip for servers, printers, access points, ect. plugged into routers.  This way, file sharing, print sharing & server access will never change, shortcuts & bookmarks don't break, ftp & ssh clients don't have to be reconfigured, etc. etc.

routers:
Most home routers have pre-configured ip blocks used for dhcp & static addressing.  For example, linksys routers have a static ip range of 192.168.1.1 for the router & 192.168.1.2 - 192.168.1.99 for static ip systems.  Dynamic addressing begins at 192.168.1.100 on up.  Other routers have their own pre-set ip ranges. Check the router manual for info on what ips to use for static addressing.

---

