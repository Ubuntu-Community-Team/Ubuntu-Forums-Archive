---
title: "Authentication through Server 2003 blocking Ubuntu updates"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by Pencilpen on 2008-08-04
Hi there,
I am running an Ubuntu Desktop 8.04. It sits in a Server 2003 environment and I'm wondering about the best options to get through the Server 2003 authentication to allow Ubuntu to update via the web.

At the moment I have the Ubuntu proxy settings set with my Server 2003 account domain\u/name and pwrd settings but it's blocking the updates.

I have used ntlmaps successfully on another machine but using that I seem to have to store my server 2003 password unencrypted in the ntlmaps config file - decidedly not good.

Can anyone tell me whether ntlmaps is the best solution or is there a better one? And if it is ntlmaps how does one configure ntlmaps so that one doesn't have to store and unprotected password?

TIA

Karl

---

### Post by hiteshkc on 2008-08-08
> **Pencilpen said:**
> Hi there,
I am running an Ubuntu Desktop 8.04. It sits in a Server 2003 environment and I'm wondering about the best options to get through the Server 2003 authentication to allow Ubuntu to update via the web.

At the moment I have the Ubuntu proxy settings set with my Server 2003 account domain\u/name and pwrd settings but it's blocking the updates.

I have used ntlmaps successfully on another machine but using that I seem to have to store my server 2003 password unencrypted in the ntlmaps config file - decidedly not good.

Can anyone tell me whether ntlmaps is the best solution or is there a better one? And if it is ntlmaps how does one configure ntlmaps so that one doesn't have to store and unprotected password?

TIA

Karl

Hi 
I am using ubuntu 8.04 but not able to use atp-get or synaptic since i am behind the MS proxy i tried it with ntlmaps but it is not at all working i made all the necessary changes in server.cfg .
then i tried ntlmaps with firefox then i realized that it is again and agin asking for username and password that means ntlmaps is not able to authenticate my username with ISA server;

Anybody have some idea to get ride off from here then it will be appreciable.
Thanks in Advance 
Hitesh

---

### Post by engalaa on 2008-11-20
i have same problem

---

### Post by Pencilpen on 2008-11-20
Hi guys,
In the end I used cntlm for this and it works brilliantly - you can store hashed passwords in the config file so it is much more secure. 

See
[http://cntlm.awk.cz/](http://cntlm.awk.cz/)

---

