---
title: "Wireless idea"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by kaar3l on 2007-07-24
I have a wireless router on my neighbour house, and i have 3 computers that i want to put into internet. And i have one computer that would recieve the signal from my neighbour's house. (P2 466MHz, 64MB)
I have a wireless reciever: DWL-G122 C1 (it's no problem to get working, but i want to send the signal out from the network card to router. Is there any program that i could use to do it?

---

### Post by spd106 on 2007-07-25
I think what you are saying is that you want to share an internet connection from the wireless router through the wireless client to the other two wired PCs, is that correct?

These wiki pages should help
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)
[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

---

### Post by kaar3l on 2007-07-26
Yes exactly, but is there any graphical tool that i can use for this?

---

### Post by walkerk on 2007-07-26
you'll need a second wireless card in your pc that receives the connection from the router..

1 Wireless NIC to connect to the router.
1 Wireless NIC to broadcast that information to your other PCs

[Wireless Ad-hoc networking]("http://en.wikipedia.org/wiki/Wireless_ad-hoc_network")

---

### Post by spd106 on 2007-07-26
Try [firestarter]("https://help.ubuntu.com/community/Firestarter")

---

### Post by walkerk on 2007-07-27
> **spd106 said:**
> Try [firestarter]("https://help.ubuntu.com/community/Firestarter")

firestarter is a firewall. I believe he is try to share internet connection via wireless through one PC thats connected to a router.. (like Internet Connection Sharing, ICS, in Windows..)

firestarter won't do this..

---

### Post by spd106 on 2007-07-28
Firestarter is not really a firewall as such, it is a clever utility for creating packet filtering rules. Which is closely tied to how connection sharing works. I don't want to get too technical, so I suggest that you read the page I linked to, then you will see ICS is listed as the second key feature of Firestarter. It's not perfect, but it's the best GUI method I have seen.

---

