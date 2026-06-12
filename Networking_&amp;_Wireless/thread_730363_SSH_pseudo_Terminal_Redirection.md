---
title: "SSH pseudo Terminal Redirection"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by mdeshpande on 2008-03-20
Hi Guys . 

i am not much aware of pseudoterminals (pty and tty) , hence looking for gurus to help me out.

ssh puts network input onto stdin of a negogiated terminal T1. Then it redirects stdout of same terminal T1 to network. I want to decouple this behaviour. 

i want to write the network input on to stdin of a different terminal T2,  a program running in that terminal, will accept stdin, and print something on T1's stdout. 

As a separate question, is there a way, i can fuse two pseudoterminals together on same machine, say a client and server are running in same machine?

Thanks and Regards
Manoj.
Georgia Institute of Technology

---

