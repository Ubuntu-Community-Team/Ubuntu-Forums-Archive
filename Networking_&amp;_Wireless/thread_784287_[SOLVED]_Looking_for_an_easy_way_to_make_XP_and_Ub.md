---
title: "[SOLVED] Looking for an easy way to make XP and Ubuntu talk to each other through rou"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by the8thstar on 2008-05-06
Hello all,

I have bought an Actiontec DSL modem / router + wireless.

I have configured the modem easily with Ubuntu (WAP is active, I can connect to the Internet and all) on my laptop (see sig).

Now I'm going to set the modem up to work with my desktop that has Windows XP through a wired connection. Setting up the system shouldn't be too hard, since the modem configuration is all browser based and the connection is ethernet.

Assuming that I succeed, my questions are:
 
[COLOR="Blue"][B]1. how do I make Windows and Ubuntu see each other?
2. How do I enable file transfers b/w the two?
3. Are there any security risks?
4. Are there CLI or GUI tools to monitor/diagnose traffic and security?[/B][/COLOR]

Thanks for your help.

---

### Post by renzokuken on 2008-05-06
The answer to 1. and 2. is to use **Samba**. There ae plenty of guides on the wiki and in the forums (+ Google) on how to do it.

Security is a matter of configuring correct permissions in Samba, all easy to do.

4. There are but i can't remember the names of any of them.

---

### Post by jonandrews on 2008-05-06
Check out my step by step guide to Windows / Ubuntu networking:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

I hope it helps

---

### Post by the8thstar on 2008-05-06
> **jonandrews said:**
> Check out my step by step guide to Windows / Ubuntu networking:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

I hope it helps

Thank you. How is 8.04 different from 7.10 in your opinion?

---

### Post by renzokuken on 2008-05-07
it will appear essentially similar but it is the latest versions of all software and is also a Long Term Support release so you will get updates for 3 years for desktop version and 5 years for server version.

i would go with 8.04

---

### Post by stinger30au on 2008-05-07
a great tutorial... thanks.
8.04 is slightly different though

---

### Post by the8thstar on 2008-05-11
Thanks again for the tutorial.

I was wondering if there is a program that would allow XP and Ubuntu users to send little IMs to each other through the network.

Any suggestions?

---

### Post by renzokuken on 2008-05-12
you can use "net send" for XP to XP, but not sure how linux fits in......google for **linux net send equivalent**

---

