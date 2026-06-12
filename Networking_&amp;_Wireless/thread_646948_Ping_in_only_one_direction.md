---
title: "Ping in only one direction"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by troman on 2007-12-21
I have an interesting problem.  I have a sneaky suspicion that this is a hardware issue, but I'd love to see if I can find out exactly what is going wrong.  

The problem is this:  
From my ubuntu gutsy computer I can not ping another computer on my network, however other computers can ping me.

When I connect a cat5 cable into my computer I don't get an ip address for eth2 as I would expect.  What I do get is an ip address for eth2:avah.  When I try to ping from my computer to any other I get no response.  When I ping from any other computer I get replies from my gutsy machine.

I pulled up wireshark to see the traffic going across the wire.  My gutsy machine repetitively broadcasts asking for anyone who has address 208.187.197.69 and asking for the response on the eth:avah address.  I assume that the ubuntu networking is assuming a temp ip of eth2:avah and trying to find an ip that nobody is using to assign to eth2.  I could be very wrong here.

The result is that eth2 can never resolve an ip address.  What is even more boggling to me is that if I connect a game from any other computer back to the gutsy machine the connection will work and the game will play fine.  If I try to connect to another machine I can't ever get anything to connect.

I said at first that I think it must be a hardware issue because I get the problem on both windows and gutsy using a connection that works with any other computer.

Any ideas would be appreciated.

---

### Post by blackhole54 on 2008-01-11
I stumbled across this thread as I was trying to help somebody else who was showing an "avah" entry from **ifconfig** that I did not understand.  Since this thread is somewhat old, I don't know if you are still looking for ideas or not.  But I thought I would post what I am starting to piece together as a working hypothesis and see what comments you or anybody else have.  Please don't take this post as definitive -- I am still feeling my way through some of this myself.

I believe *eth2:avah* is an "alias" for *eth2*, which as I understand it is simply a way to assign additional IP addresses to an interface.  I think  *eth2:avah* has been assigned by [*avahi*]("http://avahi.org/") which is "a system which facilitates service discovery on a local network."  Presumably the broadcasts you were seeing was the attempt to discover other *avahi* enabled devices.  I am guessing any such device would respond to the poll for 208.187.197.69.

This leaves *eth2* available for the use you intended for it.  I presume you have it setup for DHCP and it is still waiting for an address to be assigned to it?  The question is why it isn't receiving an address.  Since MS Windows is also not working with this interface, your conjecture about a hardware problem seems plausible.  Except that it sounds like you are getting some functionality out of this hardware.  The only other thing I can think of is perhaps for some reason your DHCP server is refusing to serve an address to this card based on its MAC address.  I am also a little confused how you pinged this interface if it doesn't have an address.

Any responses to my conjectures are appreciated.

---

