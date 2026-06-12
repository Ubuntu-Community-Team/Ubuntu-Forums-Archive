---
title: "Building a Dial-in ISP"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by medya on 2007-03-17
hi ,
I want to know can we make an ISP using ubuntu ? does anybody have any tutorial or article ?

I have an ADSL internet, I want to let my friend , to connect to my computer using Phone (dial up internet) and use my internet .
is that possible ? 

logically I think it should be possible.

I would be greatefull if u post any article, tutorial , for how to make an ISP (any kind of ISP) using linux.

---

### Post by Mr. C. on 2007-03-17
Sure, you can provide dial in access, and then route that traffic to the internet.

You need to first configure your modem to accept calls, allow and authenticate a PPP connection, and configure your system to act as a router.  This is a fair amount of work, but may be worth your while.

To accept more than one call, you need more than one phone line; typically ISPs have modem pools and many phone lines.

If you are serious about this, search for PPP HowTos to get acquainted with making a connection to the internet.

MrC

---

### Post by medya on 2007-03-17
thanks for reply, 
> You need to first configure your modem to accept calls
do you mean my normal Dial up modem ? I have a conexant 56 KB dialup modem , can I make ISP using that ? or I must buy a special modem .

[I am going to do this like an expriment not like comercial thing, I like to learn and also give free internet to my friend using phone]

---

### Post by Mr. C. on 2007-03-17
Yup, normal dial-up modem.  That's what you said you want.

I suppose if you consider being able to connect with 1 customer at a time an ISP, that's OK by me.

Dial-up ISPs (POP - points of presence) have very large banks of rack modems, dozens of modems per rack.  They also have special phone lines that can handle many calls at once (T1 or greater).

So, for your friend, you can allow dial-in calls and provide internet services for your friend.

MrC

---

### Post by medya on 2007-03-17
so is there any tutorial or something to start building my ISP ?

-what are rack modems ?
-how I can get those special phone lines?

---

### Post by Mr. C. on 2007-03-17
Time to start googling.  You know how to use it.

I already suggested your start by learning how to configure PPP.  Search the Ubuntu forums for PPP HowTos.  If you're having trouble doing this 1st step, you'll be very hard pressed to complete the rest of the task.

MrC

---

### Post by medya on 2007-03-17
yeah thanks , I already know how to make a dial up connetion using PPP (I can connect to internet using dail up modem in linux)

---

### Post by Floppyjoe on 2007-03-17
I found this article on the net but am not sure if it will be what you are after.

[http://www.enterprisenetworkingplanet.com/netos/article.php/2228641](http://www.enterprisenetworkingplanet.com/netos/article.php/2228641)

---

