---
title: "Wireless ethernet bridge and DSL sharing"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by slAoD on 2008-06-26
Hello i have the following setup.

[IMG]http://i28.tinypic.com/28rxue.jpg[/IMG]

The routers are linksys wrt54g(s) with dd-wrt on them and the PCs have Ubuntu and WinXP as their operating system.

The DSL modem  A is a siemens speedstream 4200 and is working in a bridged mode. It is connected to C's Wan port and C is working as a PPPoE and shares the internet connection.

The problem is that although every router and pc can ping each other,  and the dsl connection is properly shared with B and D , E and F cannot see the internet. 

The good thing is that E and F can resolve internet addresses through C but they cannot even ping at the internet.

I did a little research over the internet and found that my case is almost identical to that : [[COLOR="Blue"]http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge[/COLOR]]("http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge") , but the only difference is that the router D which corresponds to the dsl modem is in access point mode. Is this change going to make a difference??

What seems to be the solution to my problem here?

thank you in advance.

---

### Post by kevdog on 2008-06-26
What's the connection between D and E -- wireless?  Don't you want D in repeater bridge mode rather than client bridged mode (assuming its wireless)?  E is fine in access point mode.  Have you set the gateway addresses properly?

---

### Post by slAoD on 2008-06-26
thank you for your reply.
The connection between E and D is indeed a wireless  connection.
I  have set the default gateway of all routers of the network to be    10.176.7.33(C).

Actually your idea about repeater bridged client is interesting but  why do i need a repeater?

---

### Post by kevdog on 2008-06-26
Isn't D just supposed to rebroadcast the signal?  I can't see your picture now for some reason so I have lost your network design (and it was a good picture).

---

### Post by kevdog on 2008-06-26
Whats the purpose of the D router?  By your drawing it just seems like its acting as a wireless hub of sorts.  E and C can not communicate directly?

Also it seems at a minimun E should be in client bridge mode or repeater bridge mode -- the difference between the two is that with bridge mode, only wired clients can use the network (similar to your drawing) -- with repeater bridge -- wired and wireless clients may be clients connecting through E.
[http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge](http://www.dd-wrt.com/wiki/index.php/Wireless_Bridge)

If you are insistent with using D for whatever reason, it seems D would need to be configured in Access Point Mode with dhcp turned off.  In fact in all cases you want router C to be your only dhcp server on the lan.  All of your gateways should also list the IP address of C as the gateway also.

---

### Post by slAoD on 2008-06-27
OK i changed D into a AP and E into a wireless bridge and now everything works like a charm(apart from some winXP clients in B that their route table grow unnecessarily large but i will find out a solution for that ).

Thank you for your valuable advice!!

---

