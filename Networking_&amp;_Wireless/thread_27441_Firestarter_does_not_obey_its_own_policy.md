---
title: "Firestarter does not obey its own policy"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by dakhan on 2005-04-16
High all!

I try to set SAMBA working between my desktop (Ubuntu Hoary, IP 192.168.0.1) and laptop (W2K, IP 192.168.0.2).
I managed to enable on Ubuntu Internet sharing and DHCP, also I am able to browse laptop disk contents from my desktop. Now I'd like to browse the other way around,  but firewall doesn't allow this.

I have set following policies in Firestarter:

Allow connections from host
192.168.0.2
Allow service
SMB   137-139   192.168.0.2
DHCP 67            192.168.0.2
SMB   137-139   192.168.0.1

but still I can see these events appear regularly:

Blocked connections
138  192.168.0.2  UDP  SMB
137  192.168.0.2  UDP  SMB

I would be very grateful if anybody has some ideas about this strange behavior.

Thank you for your attention!

Andrzej

---

### Post by ubuntu_demon on 2005-04-16
You should do the following :

1) only install firestarter on the internet gateway and don't run a firewall on the other pc's (if everything is set up correctly than you can also go installing firewall's on your other pc's)
2) allow all outgoing connections
3) allow incoming SMB
4) allow incoming port 445

---

### Post by aburda on 2005-05-10
I am in agreement with Andrzej, I have setup firestarter on my server and I specifically grant 22 for ssh to everyone and then I can still see it is recording it blocking it.  I then specifically grant the IP address access and I can still see it blocking the IP address.  It doesn't actually seem to be acting according to the rules that I have entered.

---

