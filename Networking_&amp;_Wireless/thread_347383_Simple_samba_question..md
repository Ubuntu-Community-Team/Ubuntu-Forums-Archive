---
title: "Simple samba question."
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by randomusername on 2007-01-27
Hi all.

I have two XP pro boxes, a NAS box running samba and an Edgy box connected via a Linksys DSL router/eth switch, all are members of the "WORKGROUP" workgroup.  

My problem is as follows: On the Edgy box I can't see any of the other machines in the workgroup under "Network Servers" , but I can mount their shares if I go **Places->Connect to server->Custom location **and enter **smb://ipOfDesiredMachine**

The XP boxes can see all of the other machines in the workgroup under "Network Places" with no issues.

What do I need to do in order to be able to browse the workgroup using Edgy?

---

### Post by mal on 2007-01-27
I'm not sure how to solve your problem, but have you tried the samba instructions at [http://ubuntuguide.org]("http://ubuntuguide.org")?

Mal

---

### Post by randomusername on 2007-01-27
Thanks Mal, I did have a look at that one, but no luck I'm afraid.

---

### Post by neill on 2007-01-27
what is the NAS 

a proprietary device ?

another ubuntu box ?

if you can connect to a share OK, but can't 'see' it, then one possibility is that it's hidden by the NAS

---

### Post by randomusername on 2007-01-27
The NAS is a proprietary device, but none of the shares on it are hidden, neither are any of the shares on the XP boxes.  The ubuntu box is the only one that can't see everything else in the workgroup.

---

### Post by neill on 2007-01-29
i had similar problems with my setup - dapper, some XP boxes and a NAS (freeNAS in my case)

i noticed that when i had a particular config option in freeNAS set - enable master browser - then, for whatever reason, my DD box could see the various servers like the XPs could. if that freeNAS option was unset, then DD couldn't see them (or at least all of them) !!

:confused: 

i didn't pursue it myself because all the shares were statically mounted in fstab anyway, so i didn't need to browse the network

have you tried asking this question in a more general forum - linuxquestions.org for example

neill

BTW if you sort it off forum please feedback

ta

---

