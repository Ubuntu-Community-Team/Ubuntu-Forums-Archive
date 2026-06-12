---
title: "Some sites work, some never load - wired connection???"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by garfonzo on 2008-04-25
I just did a fresh 8.04 install. I'm toying with the idea of switching to Ubuntu away from Vista and am willing to go through some difficulties. However, this is annoying. 

I don't know why, but some websites work fine, and some never load. For example, I can never reach [www.ubuntuforums.org](www.ubuntuforums.org) or [www.digg.com](www.digg.com). They are always "Transfering". However, other sites seem to work fine such as google, and others.

Anyone have any ideas as to what is going on, why it isn't working?


Cheers,

Garfonzo

---

### Post by tamoneya on 2008-04-25
that sounds to me more like a firewall problem.  Have you installed any firewalls.  I had a similar problem when I installed moblock.  It was turning itself on when the computer started and I didnt realize.  I had to reconfigure it.

---

### Post by garfonzo on 2008-04-25
> **tamoneya said:**
> that sounds to me more like a firewall problem.  Have you installed any firewalls.  I had a similar problem when I installed moblock.  It was turning itself on when the computer started and I didnt realize.  I had to reconfigure it.

That's a good thought, but this is a fresh install. I didn't think a firewall was installed by default. Am I wrong? Does Ubuntu, by default, install and turn on a firewall?

I'll reboot and look for a firewall...

---

### Post by tamoneya on 2008-04-25
ubuntu sets up IPTables by default.  They also added Uncomplicated Firewall (ufw) in hardy.  I don't know much about ufw since it is new on hardy.  Does anyone else know how to check to make sure it isnt blocking websites.

---

### Post by tamoneya on 2008-04-25
Edit: posted into the wrong tab.  Ignore this post

---

### Post by nightwolf2k5 on 2008-07-19
I had the same problem from the last 2 weeks up till today. :)
What the problem was?? I may sound crazy but when i installed Moblock through the regular updates that we get and restarted the machine. All sites worked.

I still dont know what the problem was earlier. I tried all sorta things to disabling the ipv6 in the browser, changing the sysctl.conf file to add some statements and reinstalling non-free flash plugin. But nothing worked.

So i suggest installing Moblock and checking. If that doesn't work, you can try what i tried before this. ;)

Let us know if you need help on that as well.

These links might help

[http://ubuntuforums.org/showthread.php?t=662572](http://ubuntuforums.org/showthread.php?t=662572)

[http://ubuntuforums.org/showthread.php?p=5371465#post5371465](http://ubuntuforums.org/showthread.php?p=5371465#post5371465)

All the best :)

---

### Post by lswb on 2008-07-19
What type of connection do you have? By any chance is your computer directly connected to a DSL modem?

---

### Post by jre on 2008-07-19
> **nightwolf2k5 said:**
> What the problem was?? I may sound crazy but when i installed Moblock through the regular updates that we get and restarted the machine. All sites worked.

Since moblock 0.9~rc2-12 (the recent update) port 80 (www) and 443 (https) are whitelisted per default (so they are not checked by moblock). That's why the recent moblock update did help you.

---

