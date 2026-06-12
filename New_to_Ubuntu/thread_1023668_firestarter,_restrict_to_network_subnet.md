---
title: "firestarter, restrict to network subnet"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by PetePete on 2008-12-28
in firestarter under the policy tab i can "allow  connections from host", then a new window comes up saying "ip, host or network"

If i want to allow all computers on the network in the subnet , how do i enter this?

i tried 192.168.2.1/244 but that didn't seem to work :(

---

### Post by Dedoimedo on 2008-12-28
Hello,

The number after the slash - /xx is called CIDR and it tells how many bits of the ip address are allowed to change out of total 32 bits. 32 - 24 = 8, so 8 bits = 256 hosts. This is a typical, classic C-class subnet.

The first number needs to be the network ID, usually x.x.x.0

So you would want to specify 192.168.2.0/24.

BTW, in general, the first IP (x.x.x.0) is network id, the last IP (x.x.x.255) is the broadcast, for /24 (or C-class) subnets.

The number you tried 244 does not exist. Available numbers are 0-32. 32 is equivalent to host itself, because 32-32=0, 2^0=1.

Hope this was clear.

Cheers,
Dedoimedo

---

### Post by PetePete on 2008-12-28
thanks for giving a mini network lecture and my answer!

cheers

---

### Post by aVirulence on 2009-03-12
I'm basically trying to do the same thing, since my Mediatomb server doesn't get picked up automatically by my local network systems. This is the case when the firewall is off.

What I would like to do is the following:just accept ALL traffic from the local network. What I did is the following: I added 192.168.0.0/24 to the "Allow connections from host" window. (My local IP Address is 192.168.0.1). However, this doesn't help with the blocking problem.

How can I free my entire Lan network traffic from the firewall? I also tried filling in lan in the "Allow connections from host" window. I got an error that the network wasn't recognized then.

Thanks!

---

### Post by ub-newbie on 2009-07-26
Dodoimedo,  I'm noob, but I read the Firestarter manual trying to get CIDR to work.  If I'm looking at it correctly, there seems to be a mismatch between IPTABLES and FIRESTARTER.

I'm trying to poke a hole for 192.168.4.20 through 25.

IPTABLES -L shows 192.168.4.16/29 (under CHAIN inbound)

while FIRESTARTER shows 192.168.4.20/29
[IMG]http://operations.mesonet.org/~rheck/fs.jpg[/IMG]

Is this the way it should be?
---------------------------------------------
EDIT - I talked with a local SysAdmin and figured it out.  To use a CIDR of 29 I have to shift my IP range from starting at 20 to starting at 16.

Here is the calc I used (It requires Internet Exploder)
[http://www.subnet-calculator.com/cidr.php](http://www.subnet-calculator.com/cidr.php)

---

