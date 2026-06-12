---
title: "How to connect to laptops via router?"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Olnex on 2008-08-17
Hello, I have two laptops, one with Ubuntu 8.04 and one with OpenSuse 10.3, I am a computer science student and I have to write some networking program in Java, simply put, I have to create a server socket on one laptop while another laptop can connect to the server using socket.

I simply connected the two laptops to router, each has network status being "connected", but they cannot find each other.

For specifically, I am writing J2ME program, it is different from standard Java and executed inside an mobile phone emulator.

Thanks a lot!

---

### Post by SpaceTeddy on 2008-08-17
can they ping each other ? what are their ip addresses ???
(sorry for not writing more, but there is too little info here to start explaining right away)

hope we can figure this out :)

---

### Post by cpetercarter on 2008-08-17
Try this:

On each machine, Administration > Network > Hosts > Unlock > Add and insert the ip address of the other machine (eg 127.0.1.1)

You will also need to configure the firewall on the  machine providing the service to permit access by the other. If you use Firestarter to manage the firewall, see [http://www.fs-security.com/docs/policy-page.php]("http://www.fs-security.com/docs/policy-page.php")

---

