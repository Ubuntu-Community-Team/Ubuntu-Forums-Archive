---
title: "Using ubuntu at work pc support"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by pretender? on 2009-06-21
I have been running ubuntu for over 12 months at home for mythtv mainly.  I work on a helpdesk doing pc support and I have just installed a virtualbox vm running ubuntu a 9.04 there has been a couple of times I have used ubuntu to open office files that  currupt or so ms office said but opened fine in ubuntu

my question is what apps or terminal commands can be useful in helpdesk support doing 2nd level desktop support 

 what I have installed so far

vnc for remote support
citrix receiver
I use psloggedon a lot in xp to see who is logged into a pc.  What is similar in linux

also whats involved in join the vm to the domain (its a windows 2003 domain)

I guess basically i have been running ubuntu at home for a while now and just want to see what other possibilties and uses it has.

Also very bored with PC support at times with XP and office on the helpdesk as you dont come across new errors and learn things that are new to you as you seem to be fixing the same old errors and doing the same old things week after week.

regards
pretender

---

### Post by powel212 on 2009-06-21
I am sorry if I am misunderstanding the question.

I also like using Virtualbox and have had some troubles joining the windows domain until I changed the network setup in the virtualbox to Bridged instead of "NAT"

Hope that is the information you are looking for.

Powel

---

### Post by 3rdalbum on 2009-06-21
> **pretender? said:**
> 
I use psloggedon a lot in xp to see who is logged into a pc.  What is similar in linux

The "who" command will show you who is currently logged into the PC. If you need a list of who WAS logged into the PC and when, the "last" command will do this.

---

