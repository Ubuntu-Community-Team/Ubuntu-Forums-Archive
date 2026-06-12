---
title: "[SOLVED] Need some help with lesser used SSH switches"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by PreviousN on 2007-12-09
Hey guys,

I'm using "ssh -X" to forward X. I want to start a program on my laptop this way, ask the program to do a task, then close the ssh session and have the program continue so I can check up on it later. How can you close the ssh -X session but have the program continue running so I can check on it later?

Secondly, I was recently told about ssh -R which is supposed to open up a "reverse tunnel". Was someone just messing with me? I have a use for this. 

My parents use a satellite connection because they live in the country. I want to install ubuntu on their machines and administer it but for some reason they aren't connectible (I think it has to do with the fact that they share their IP with quite a few people). Thus, no ports are forwardable, from what I understand. 

Anyway, for remote administration, can I ask my mom/dad to use "ssh -R mycomputer.com" and then I can connect to them? Any clarification would be sweet. Thanks!

---

### Post by Original Brownster on 2007-12-09
> **PreviousN said:**
> Hey guys,

I'm using "ssh -X" to forward X. I want to start a program on my laptop this way, ask the program to do a task, then close the ssh session and have the program continue so I can check up on it later. How can you close the ssh -X session but have the program continue running so I can check on it later?

Thanks!

Hi,
You need the program called 'screen', should be installed or available via apt-get.


```
My parents use a satellite connection because they live in the country. I want to install ubuntu on their machines and administer it but for some reason they aren't connectible (I think it has to do with the fact that they share their IP with quite a few people). Thus, no ports are forwardable, from what I understand.
```
I don't know about this, possible because the satellite is used for download and dial up for upload? If this is the case this may impact on any chances to use ssh over a tunnel as I cannot see how data could flow back to the satellite linked pc. interesting f anyone else knows the answer to this! 
[This article]("http://http://www.cl.cam.ac.uk/research/dtg/attarchive/vnc/sshvnc.html") would suggest that it is otherwise possible to do.

---

### Post by PreviousN on 2007-12-09
They have a special satellite dish that allows them to broadcast as well as receive (ie: they can upload at like 100kbs to sites like rapidshare). Whenever it goes over an encrypted connection using ssl (for example https), however, it is significantly slower. Maybe that means that its possible but it would really slow?

Anyways, Thanks for the tip about screen, havn't tried it yet because I'm busy, but tis a good thing to know. Thx.

---

### Post by PreviousN on 2007-12-14
So after much searching, I found this website:
[http://www.linuxlogin.com/linux/admin/sshtunnels.php](http://www.linuxlogin.com/linux/admin/sshtunnels.php)

It explains everything so clearly with screenshots and everything. Anyways, I got the ssh -R to work. Here's my steps. 

1. At my parents house, open a terminal and type "ssh -R 8000:localhost:22 domain.myhome.com"
2. At my house, ssh to localhost this way: "ssh -p 8000 localhost" and BOOM, you've got a reverse tunnel that WORKS OVER SATELLITE. W00t. I'm pretty happy. Of course its really laggy, but I could see myself scping files and etc. 

Cheers Yall!. Read that website, some really useful info on it. :guitar:

---

