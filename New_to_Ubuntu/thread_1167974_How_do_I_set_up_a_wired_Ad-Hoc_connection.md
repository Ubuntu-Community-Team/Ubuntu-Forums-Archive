---
title: "How do I set up a wired Ad-Hoc connection?"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-05-23
hey all,

how do i set up a wired ad-hoc connection in network manager? there's plenty of documentation regarding wireless ad-hoc networks, but none for wired (that i can find, anyway).

this is how i want my network set up:

Laptop -----super long 50 ft ethernet cord------ Desktop PC With 50 GB Music

*both the laptop and the desktop are running Jaunty 9.04 desktop editions. 

also, once the network is set up, how do i go about accessing the files on the host computer? (sorry that may sound like a dumb question)

any help would be appreciated ;)
thanks

---

### Post by candtalan on 2009-05-23
Using an ethernet cable to connect directly between two machines without use of any router in between suggests that you would need to use a so-called 'crossed' ethernet cable, not an ordinary 'patch' cable.

I am not sure if the machines will connect automatically, they may do, beause that happpens with a router in play. It is possible though that you will need to run each PC with its own fixed IP address, because lacking a router in the network, the PCs will not have an IP allocated to them by any means.
HTH

---

### Post by asuastrophysics on 2009-05-23
got it!

easy. just set the connection to "Link-Local" on both computers, and it connected automatically. i then went through nautilus and selected folders to "share". 

samba had to be installed on both machines. one computer doesnt have an internet connection, so i just shared the /var/cache/apt/archives directory over the network and installed samba from there.

it works! :popcorn:

solved my own problem

---

