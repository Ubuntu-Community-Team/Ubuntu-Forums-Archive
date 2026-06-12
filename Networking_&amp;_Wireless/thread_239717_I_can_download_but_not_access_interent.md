---
title: "I can download but not access interent??"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by salowalker on 2006-08-19
I thought at first this was a physical problem with my ethernet card but then I swapped them out and got the same results.
Basically I can ping any address and it works (I can even ping from my other computer to the box with ubuntu), but when I open firefox it will not work (i have the default version that came with ubuntu)... Everything says its connected and working (ifconfig, network (admin)) I've messed around with using DHCP and not using it, both relay the same problem.  I've gone into firefox and tried out different settings with 'auto-detect' and 'connected to internet' and still nothing.  

I'm not sure what else to do?  I am completely new at linux and ubuntu (as of yesterday), so it could be something very simple.

ANy suggestions??

---

### Post by bensexson on 2006-08-19
When you ping are you using an IP address or an URL?

---

### Post by salowalker on 2006-08-19
im using a url... i tried google and yahoo.  they both work, i also just found out i can use gaim and chat with it.  i can't figure it out for the life of me.

---

### Post by bensexson on 2006-08-19
So what happens when you try to browse to a web page with firefox?

---

### Post by salowalker on 2006-08-19
It will keep searching for the page a while, and then respod with server timeout for whatever/any site i try to go to.  I've also tried epiphany browser with the same results.

---

### Post by bensexson on 2006-08-19
OK, this is getting out of my depth.  Have tried to configure proxy server settings? If so that may be the problem but this is weird.  I hope someone else is looking at this thread who may have a better answer.

---

### Post by salowalker on 2006-08-19
I just tried proxy settings and still nothing... this is a strange problem.

---

### Post by salowalker on 2006-08-19
IT WORKS!!
I dont know what i did but i switched back to DHCP Enabled and it works fine now.

thanks for your help bensexson.

---

### Post by bensexson on 2006-08-19
Sorry I could not nail down the issue.  It may have just been a transient network issue.

---

