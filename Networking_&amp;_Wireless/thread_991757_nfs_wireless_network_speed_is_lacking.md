---
title: "nfs wireless network speed is lacking"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by satipera on 2008-11-24
I have stumbled in an uncomprehending manner to eventually set up two ubuntu machines that can swap files over a local network using nfs.
   
   The two machines are connected to a wireless router. I am assuming they are communicating via the router and not directly (I do not know) 

   The transfer rate is 1 meg/second this seems low to me as my internet connection (rated up to 8 megs/second) works regularly at 4 megs/second when you have stopped laughing at my ignorance :) if someone could explain to me why the machine to machine transfer rate is so low, thanks.

---

### Post by gTinker on 2008-11-24
[QUOTE=satipera]   
   The two machines are connected to a wireless router. I am assuming they are communicating via the router and not directly (I do not know)[/QUOTE]

Yes, they would be connected via the router. Most routers have status lights on the front. You should be able to see the lights flash while you are doing the transfer and not using the Internet for anything. Most network cards (and laptops with onboard wireless) have a light for the connection too and you should see the transfer on those.

[QUOTE=satipera]
   The transfer rate is 1 meg/second this seems low to me as my internet connection (rated up to 8 megs/second) works regularly at 4 megs/second when you have stopped laughing at my ignorance :) if someone could explain to me why the machine to machine transfer rate is so low, thanks.[/QUOTE]

First off, don't confuse the Internet connection rate with the connection rate on your internal network. There are lots of variables with the transfer you mention. There could be collisions on your intranet causing retransmissions. There could be a slow network card on one of the computers limiting the connection speed to what it is capable of. There could be a hardware problem on one of the cards or radio interference near one or both of the computers. Sorry, I can't give you a more definitive answer.

---

