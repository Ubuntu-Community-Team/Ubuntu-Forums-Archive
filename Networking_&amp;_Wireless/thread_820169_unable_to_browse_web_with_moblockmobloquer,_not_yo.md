---
title: "unable to browse web with moblock/mobloquer, not your usual problem"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by kraymore on 2008-06-06
I'm having a very unusual problem using moblock and mobloquer.  they were installed per the instructions at the [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) site.  

after installing it, it downloaded the lists.  that went just fine.  i noticed that that just so long as moblock was running that I could not browse web pages.  I read many people who said to simply add

WHITE_TCP_OUT="http https"

to the 

/etc/default/moblock

however (even after sudo moblock-control reload) that would not do it after reloading moblock-control and starting moblock  

I'm a little confused about what else to do.  I've seen all the posts that claim that alone does it.  not for me though.  

the message i get to the moblock.log file when i try and browse the web is this:

Thu Jun  5 23:49:02| Marked block OUT: IANA Reserved for private use FNLC,hits: 11,DST: 192.168.1.1

any ideas how i can get this thing running?

btw i am using hardy.  the ubuntu moblock wiki mentioned whitelisting the lan.  i am not sure if that is my problem.  if it is, the ubuntu wiki doesn't give sufficient information on how to do this (it only lists too vague examples), just allowing web browsing, while keeping the level of protection the blocklists provide.  my lan is 192.168.1.1 with subnet of 255.255.255.0 and its your everyday home network.  

 

would appreciate help

---

