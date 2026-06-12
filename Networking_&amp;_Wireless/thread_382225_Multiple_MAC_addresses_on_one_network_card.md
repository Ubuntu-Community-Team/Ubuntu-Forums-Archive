---
title: "Multiple MAC addresses on one network card"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by mayfer on 2007-03-11
hi,
i am on a network where ip numbers are assigned according to the ports that the computers are connected to on the switches, using DHCP. however it is still possible to connect more than one computer to one port on the switch if you have a hub or a switch yourself, and then DHCP would assign the unused ip numbers to these other computers.

now my problem is that i want to change my ip number.
i tried changing my MAC address to see if that makes any difference, it didn't. i still got the same ip number.

i noticed that VMWare can emulate a second MAC address on the same network card, and act as a separate computer, and it gets assigned a different ip number. (i am using bridged network in VMWare and connect to the physical network directly.)
[B]
my question is, how can i do what VMWare is doing on my ubuntu and create multipe MAC addresses on my network card? [/B]

i am guessing somehow i would have to create two network interfaces, such as eth1 and eth2 and give them different MAC addresses. this way i would be assigned two differnet ip numbers on these two interfaces, and then i can change the default route.

thanks a lot,
- murat.

---

### Post by Mr. C. on 2007-03-12
I'm a little confused as to why you want to do this, or what are you trying to accomplish?

Ethernet hardware has one MAC address.  Any emulation by other software is managing proxy arps and the hardware, so it can do what it wants.

Two interfaces does not satisfy your 1 interfaces w/2 MAC addresses.

With two interfaces on the same network, which one responds to broadcast messages?

MrC

---

### Post by lloyd_b on 2007-03-12
> now my problem is that i want to change my ip number.

To echo MrC, Why?  What's magic about the IP number?

A solution:  If you know that a given IP is available on the network, then setting your machine with a static IP address will probably work.  But don't yell at me if the sysadmin hunts you down and thwacks you with a cluebat for doing this :) 

Lloyd B.

---

### Post by mayfer on 2007-03-12
a quota system is used on the network, and whenever a total of 5GB (upload+download) is exceeded in the past 24 hours, the bandwidth goes down from 10mb/s to 100kb/s. the same penalty goes for people using static ip's. 

so basically in order to avoid this situation, i need to be assigned a different ip number from my own with dhcp.

i hope the problem is more clear now.

---

### Post by lloyd_b on 2007-03-12
I'm of two minds on this one.  

On one hand, you are obviously trying to do something that the network people don't want you to do.

On the other hand - It's an interesting challenge:) 

A general idea.  When you first boot (with the normal MAC address), you get the initial DHCP lease, which provides the initial IP address.  Normally, any attempt to restart the network will result that lease being released, so when DHCP looks for a new lease, it will wind up with the same IP address.  In addition, info on that lease is stored in the dhclient.leases file, and your computer will *try* to reuse that lease.

So what you somehow need to do is shut down the interface without releasing that original lease, then change the MAC address (so that the DHCP server thinks it's talking to another computer), and request a new lease (which will have a different IP address).

I can see a way to do this manually:  Unplug the network cable, stop networking, manually delete the lease from the dhclient.leases file, change the MAC address, plug the network back in, and then start up networking.  

At least I *think* that would work...

Sorry, but I'm not all that knowledgeable about DHCP.  I *suspect* there's some way to pull this off without having to physically disconnect the network cable, but I haven't a clue as to what it is.

Lloyd B.

---

### Post by netztier on 2007-03-12
> **mayfer said:**
> now my problem is that i want to change my ip number.
i tried changing my MAC address to see if that makes any difference, it didn't. i still got the same ip number.


Changing the MAC address would be easiest - you could swap the NIC too, if your hardware allows for it.

How did you change the MAC address? 

I know of two ways, but there's probably more: on-the-fly with **macchanger** (there's a package in the repos somewhere with that name) or - if you want the change to be persistent - by adding a line to **/etc/network/interfaces**, as described in: [How to change MAC address]("http://http://www.ubuntuforums.org/showpost.php?p=2235346&postcount=8"). 

A MAC address like 12:34:56:78:9A:BC will *certainly* draw the network admin's attention and curiosity, so consider using one from an old unused NIC - this can be some really old stuff (10mbps NE2000 card or so...). You or a buddy of yours probably have one of these in their "well, I might need one of these some day"-box.

Other alternative: check what lease time you get when obtaining the old address - and if possible, wait for long enough to let it completely expire and then re-request a new address.


best regards

Marc

---

### Post by mayfer on 2007-03-12
> **lloyd_b said:**
> I'm of two minds on this one.  

On one hand, you are obviously trying to do something that the network people don't want you to do.

On the other hand - It's an interesting challenge:) 


hehe, the two things that you mentioned are basically what motivates me :)
you can only prevent something by first understanding how it works...

> **lloyd_b said:**
> 

So what you somehow need to do is shut down the interface without releasing that original lease, then change the MAC address (so that the DHCP server thinks it's talking to another computer), and request a new lease (which will have a different IP address).

I can see a way to do this manually:  Unplug the network cable, stop networking, manually delete the lease from the dhclient.leases file, change the MAC address, plug the network back in, and then start up networking.  

Lloyd B.

i was trying to do this by leaving the original connection on and getting a second connection going using a second MAC address, but your ideas sound easier. 
i will try doing what you suggested when i can, and i will let you guys know what happens.

however there's one little thing i don't understand, if i stop networking, why would i still need to physically unplug the network cable? isn't stopping networking essentially the same thing?

---

### Post by lloyd_b on 2007-03-12
> however there's one little thing i don't understand, if i stop networking, why would i still need to physically unplug the network cable? isn't stopping networking essentially the same thing?

When you stop the network normally, the DHCP client is supposed to send a "DHCPRELEASE" message to the DHCP server, which will tell the server that that particular IP is no longer in use.  And when you restart networking, the DHCP server will issue that lease to the new MAC address (as you've discovered).

By disconnecting the network, you make it impossible for the DHCP server to receive that message, hence it still believe that there is a machine using that IP address.  So it will issue a new IP address when the machine issues a DHCPREQUEST with a different MAC (the DHCP server will mistake this for a second machine).

You may not need to disconnect the network cable - the DHCP client may not send that message.  In which case, your "change the MAC" technique may just work, provided that you clear all references to that out of the dhclient.license file (it's "/etc/dhcp3/dhclient.license", btw) after shutting down the network, but before starting it back up.  You may want to give that a try.

Lloyd B.

---

### Post by Mr. C. on 2007-03-12
> **mayfer said:**
> hehe, the two things that you mentioned are basically what motivates me :)
you can only prevent something by first understanding how it works...

... and were you my employee, I'd fire you on the spot, no questioned asked.  I personally have no tolerance for people who *agree* to an implicit or explicit set of policies, and then go against policy anyway.

MrC

---

### Post by mayfer on 2007-03-12
**yep, lloyd's idea worked perfectly.**

before i understood the difference between stopping the network and unplugging the cable, i tried it without unplugging the cable. in that case i got a "no dhcp lease" error from my ISP, and i had the bandwidth penalty again.

**now i have one last question,**
how can i switch back to my original MAC address using macchanger? can i?

thanks a lot for everyone who helped,
and i promise i will try not to annoy the network admins :)

---

### Post by netztier on 2007-03-12
> **mayfer said:**
> 
**now i have one last question,**
how can i switch back to my original MAC address using macchanger? can i?


Remove the "hwaddr ..." line from **/etc/network/interfaces** (if it's there) and reboot your system. The driver module will read the original MAC address (aka "burn-in address", unchangeable) from he card when it's loaded. **macchanger** hasn't actually changed that address, it's just overwritten the address at it's specific location in memory. No need to run it again, just reboot the box. 

Gee... what am I writing here?*grin*. Rebooting is Windows style, and we're not doing that here. Use **macchanger** to change it back or edit (if needed) /etc/network/interfaces followed by **ifdown eth0** and **ifup eth0** ;-)

best regards

Marc

---

