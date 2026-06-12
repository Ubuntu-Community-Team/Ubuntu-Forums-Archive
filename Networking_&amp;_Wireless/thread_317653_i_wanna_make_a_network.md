---
title: "i wanna make a network"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by mr dodo on 2006-12-12
hello guys 
i wanna ur help plz 
i wanna make a network in my home 
i have 2PC and 1LAPTOP 
1 of this PCs will be the server and i wanna make this server running under ubuntu and the other one is only clint using windows XP and the laptop using ubuntu 
whatever i wanna to know how i can make the server controlling other clients 
thanks

---

### Post by daniminas on 2006-12-12
you can configure your server with 'Firestarter'.. it's esay to use.. and its GUI ;-).. 
Need 2 networks cards... one for IN connection, and other for OUT-->(to the switcher) -- And from the switcher to each PC you want to connect

And in the cient PCs ive this config:

Gateway: 192.168.0.1(my ubuntu server)
IP: 192.168.0.30(diferent for any pc on the lan)
Mask: 255.255.255.0

and the DNS!!.. don't forget to configure the dns! :p 

Thats what i've, hope it gelps ))

---

### Post by mr dodo on 2006-12-13
thank u i'll try this stips 
thanx again

---

