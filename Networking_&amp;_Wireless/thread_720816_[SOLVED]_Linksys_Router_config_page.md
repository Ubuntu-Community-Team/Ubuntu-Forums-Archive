---
title: "[SOLVED] Linksys Router config page"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by mcrysler on 2008-03-10
I apologize if this issue has been covered before and I have read through most of the other similar posts but none of them actually seem to explain why this occurs nor offer a valid fix so I am submitting my own post.  I am having a problem connecting to my Linksys Router's config page via the web.  I am using Firefox 2.0.0.12 and have disabled pop-up windows but no luck.  I am also unable to hit the page from my wife's Mac.  I was able to get to it fine when I had a Windows machine or even OpenSuse installed but now, for whatever reason, I cannot.  Any suggestions?

Thanks,
Matt

---

### Post by Eiríkr on 2008-03-10
Presumably you're trying to access it by typing in the IP address in the browser address bar; what exactly happens when you do that?

---

### Post by mcrysler on 2008-03-10
That's correct.  I type 192.168.1.1 in the address bar and hit Enter.  Eventually the page just times out and nothing shows up.  I even installed IE6 via Wine and got the same result.

---

### Post by Eiríkr on 2008-03-10
Has the router been reset?  This happened to me a while back and it took me a goodly while to realize I needed to use the default router address of 192.168.0.1 (and then reassign it to where I wanted it).

---

### Post by mcrysler on 2008-03-10
No, the router hasn't been reset.  I can still ping the 192.168.1.1 address and get to the internet just fine.

---

### Post by jrusso2 on 2008-03-10
Make sure you enable java script in the browser or if you using no script whitelist that address.

Then reboot the router and try it

---

### Post by mcrysler on 2008-03-10
Javascript is currently disabled and I'm not sure what you mean when you say "whitelist" the IP Address.  Router has been rebooted and still the same result.

---

### Post by mcrysler on 2008-03-10
So just for kicks I tried entering [https://192.168.1.1](https://192.168.1.1) and that gets me there.  I honestly don't remember turning on SSL for the config page but it was apparently turned on at some point.  Thanks for all the suggestions and sorry if I wasted time but hopefully this will solve other people's problems too.  Or at least give them something else to try.

---

### Post by Eiríkr on 2008-03-10
Firefox's NoScript extension has the ability to add certain sites to the "scripts are okay" list -- this is whilelisting.  

As to why this might be relevant, many router config web interfaces make use of JavaScript.  However, it's more of an issue once you can actually access the router in the first place.  :-|  

Is there any other device that might also be trying to claim the same address?  I had an obscure similar problem some time ago, that I discovered was at least partially caused by my DSL modem and router both claiming the same IP address.  This meant the IP address was pingable, but typing it into the browser did not give me the expected router admin page.

---

### Post by Eiríkr on 2008-03-10
Bingo!  Glad to hear that adding the "s" worked.  If that resolves your issue, please remember to mark the thread as SOLVED in the Thread Tools dropdown at the top of the page.

Cheers,

Eiríkr

---

