---
title: "Getting internet to hardwired computer"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by AliasXNeo on 2006-09-06
Okay, let me explain what I have. I have two computers. One runs Windows XP Pro, the other runs Ubuntu. The computer with XP Pro has a network card and has access to my home network, where it get's it's internet connection. The other computer used to run Windows XP Home, but I hardwired the two computers, pulled everything off the XP Home one, then reformatted and installed Ubuntu. So now here they sit, still hardwired.

My question is, is it possible to get internet over to the computer with Ubuntu via them being hardwired? I figured the comp would first go through my comp, then to the network, and then reach the router where it can get it's connection, sounds logical, but I have no idea if it's possible.

Thanks!

---

### Post by pyros on 2006-09-06
Is there any reason not to run directly to the router?

---

### Post by AliasXNeo on 2006-09-06
It's on a wireless network, and the router is on the other side of the house.

---

### Post by bluenova on 2006-09-06
What exactly do you mean by 'hardwired'?

---

### Post by AliasXNeo on 2006-09-06
Hooked up with a crossover cable.

---

### Post by bluenova on 2006-09-06
Ah, then I guess you would just be able to use the Windows internet connection sharing and NAT would forward the packets to the other computer (in theory). It would just be a LAN within a LAN.

---

### Post by pyros on 2006-09-06
In theory. It's certainly worth a try. If you are running a workgroup through the router, the xp machine probably won't be able to see it. fair warning: I've never had much luck with xp and crossover cables.

---

### Post by AliasXNeo on 2006-09-06
> **bluenova said:**
> Ah, then I guess you would just be able to use the Windows internet connection sharing and NAT would forward the packets to the other computer (in theory). It would just be a LAN within a LAN.

How exactly would I do this?

---

### Post by pyros on 2006-09-06
run the network setup wizard. choose "this computer connects directly to the internet. the other computers on my network connect throught this computer" for the connection method, select your wireless card on the next step, next until done.

---

