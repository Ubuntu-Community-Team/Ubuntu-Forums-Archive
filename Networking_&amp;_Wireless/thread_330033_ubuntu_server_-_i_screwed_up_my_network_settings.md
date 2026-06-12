---
title: "ubuntu server - i screwed up my network settings"
date: 2007-01-02
forum: Networking &amp; Wireless
---

### Post by treyd on 2007-01-02
Hey guys, I have an old computer that I use for my web server. The only connections I have going to it are my power and ethernet cables. I recently purchased a new Linksys WRT54G router, and decided to use the 192.168.1.x ip range, compared to the 192.168.2.x range I was using with my belkin router.

So I ssh'ed into my server and typed nano /etc/network/interfaces and changed all instances of 192.168.2.x to 192.168.1.x, but shortly after, my ftp and ssh was running terribly slow, such as a 10 second delay after I entered my user name until I was prompted for my password, and a horrible delay from logging on/switching directories in my ftp client. I read a post somewhere on this forum about this problem having to do with dns, so I deleted the dns-nameservers line from "interfaces". We'll this screwed something up bad, and I could no longer connect to my server at all. So I had to go find an lcd and a keyboard. I booted up, and set my ip settings to dhcp. I then typed /etc/init.d/networking restart. Nothing. Couldn't even ping my router.

Now I'm just horribly confused, and am tempted to just to a fresh install. Any advice? :-k

EDIT: Maybe I could fix this in Gnome, but I disabled it , but forgot how. Is there a command to launch it back up?

---

### Post by linuchsan on 2007-01-02
I had the same problem. Which version you have (the WRT54G router) ?

---

### Post by treyd on 2007-01-02
> **linuchsan said:**
> I had the same problem. Which version you have (the WRT54G router) ?

V. 6

I solved the problem. I just typed "ifup eth0" and my card went up. Could ping my router, and now everything works.

---

