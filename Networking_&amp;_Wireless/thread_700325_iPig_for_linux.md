---
title: "iPig for linux?"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by Allus on 2008-02-18
Well, I've got Gutsy installed on my laptop and it works really well with my wireless.  I'M MOBILE!  WoooHoooo!  I can almost taste the latte now. Slight problem though.  

I have the encryption set on the router in my home,  but I don't know what to do for public access wifi as far as security.  I was looking into the VPN software available for Ubuntu, but that doesn't give you a server.

Googling around, I found iPIG - the iOpus Private Internet Gateway.  Free software AND service for Windows users.  URL = [http://www.iopus.com/ipig/](http://www.iopus.com/ipig/)

So, my obvious question is: is there anything like this for Linux users?

Thanks.

---

### Post by jago25_98 on 2008-02-18
do check out IPSec and Hamachi,

and tell us do you want it on the router? My router runs linux so I think I can do ipsec and hamachi on it. I think I may even be able to do PPTP (windows we do it our way `vpn`)

---

### Post by Allus on 2008-02-18
Hmmmm... Well, I don't know.  This is all new to me.  

Can you put something like hamachi on a routher?  

Since I first read your post I started poking around with hamachi.  It was easy on my windows computer.  Except I installed it as administrator, but I don't want that computer online all the time as administrator. But when I log out and then log in as user I don't know if hamachi is still running.  I guess some experimenting is needed there.

To get this program running on Ubuntu took a good bit of time.  This write up did me good:

[http://www.computechgroup.com/?p=360](http://www.computechgroup.com/?p=360)

And I got it running and logged on to the network I created on the other computer.  I then got the gui gHamachi and am able to logon with that.

But, I'm afraid I still don't get it:  If I am logged on to that network does that mean all input and output from this machine is encrypted through the other machine?

So that if I go out to a coffee-shop somewhere and they have a public wifi, I just start up ghamachi and join that network and all my online activity is safe?

---

### Post by jago25_98 on 2008-02-18
ssh -D8080 user@remoteComputerIP

& 

firefox socks proxy using 8080

may be an easier solution

---

