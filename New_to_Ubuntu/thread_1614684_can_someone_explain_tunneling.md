---
title: "can someone explain tunneling?"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by outleradam on 2010-11-05
I understand that SSH can be a tunnel of sorts.   If I wrote a gui for a telnet app, would it be considered a tunnelling app?   What exactly is the definition of tunnelling?

---

### Post by Zzl1xndd on 2010-11-06
Wiki to the rescue:

[http://en.wikipedia.org/wiki/Tunneling_protocol](http://en.wikipedia.org/wiki/Tunneling_protocol)

---

### Post by outleradam on 2010-11-06
Unencrypted communication over encrypted protocol is tunneling.  Thanks,  I'm applying for a job and just wanted to be sure that I have had experience with tunneling.  I read a bunch of articles about it but none made sense like that one.  Thank you.

---

### Post by alphacrucis2 on 2010-11-06
> **outleradam said:**
> Unencrypted communication over encrypted protocol is tunneling.  Thanks,  I'm applying for a job and just wanted to be sure that I have had experience with tunneling.  I read a bunch of articles about it but none made sense like that one.  Thank you.

Encryption is not a requirement of tunnelling. If one protocol encapsulated by another, that is tunnelling. Of course a common usage of it is to encapsulate an unencrypted protocol in an encrypted one for obvious practical reasons. For example, we sometimes use unencrypted [GRE]("http://en.wikipedia.org/wiki/Generic_Routing_Encapsulation") tunnels as a  method of bypassing the normal routing of packets.

---

