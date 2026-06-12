---
title: "connection dead after update...HELP"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by moataz on 2006-08-09
hey guys,

i have a weird problem, when i booted into ubuntu this morning i had this gnome update manager telling me 3 updates were available, after successfully installing them and rebooting, i can only ping my router , but every time i ping google or hotmail or yahoo, i get "incorrect host" or something of that sort....firefox doesnt connect to anything either, could anyone help me out :)
thanks in advance

---

### Post by bscbrit on 2006-08-09
I've seen something similar in the distant past.  I don't know why it occurred, but I know what it was.  I was notified that there were X updates available which I downloaded and installed.  I then had a load of problems until I looked at one of my other machines which said that there were Y updates available.  Going back to the first machine and installing the missing updates fixed my problem.  Don't know how or why.
Whether this helps you or not I don't know, especially if you cannot get back online to update. 

[https://wiki.ubuntu.com/CommonProblemsNetwork](https://wiki.ubuntu.com/CommonProblemsNetwork)

should put you straight again.

---

### Post by stricevics on 2006-08-09
> **moataz said:**
> hey guys,

i can only ping my router , but every time i ping google or hotmail or yahoo, i get "incorrect host" or something of that sort....firefox doesnt connect to anything either, could anyone help me out :)
thanks in advance

I get those when DNS server address is not set up properly so pinging the actual IP address (I guess that's how you ping your router) works, but name resolution (yahoo.com -> 1.2.3.4) doesn't. I have no idea why did that happen in your case, hopefully this may help you in locating the cause of the problem.

St.

---

