---
title: "VMWare - Firestarter Issue:"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by Gustavo Sobral on 2007-08-26
Hey all! 

I've just chosen Ubuntu as my development / study platform. I run Ubuntu 7.04 64-bit version and it's OK (Intel Core 2 Duo). Well, everything runs smoothly, including my Java tools (Netbeans, JDeveloper and GlassFish).

Also, I decided to configure a virtual machine to install Ubuntu 7.04 x86 in order to be able to run Oracle Database XE, which does not have a 64-bit version. I was able to create the VM as well installing OS, that is running fine btw. The VM ethernet is set to Bridged and a fixed IP address, respecting the same range and subnet mask of host environment. So far so good! Now, the problem itself: 

Both machines cannot see each other while Firestarter is running on the host env. I've have already managed policies to accept entries from the VM env., but it does not work. Also, I'd like the VM could access the internet hosts ppoe connection. I have made lots of atempts, like setting VM ethernet to NAT, without success. It only works if I turn Firestarter off, which is not the right solution, IMO.

My idea is having a complete development / test environment in only one box, so I can simulate software behavior more precisely.

Could anyone help me on this? What I'm doing wrong? 

Many thanks in advance!

Best Regards,

Gustavo
São Paulo, Brasil

PS: Sorry for my bad English. :mrgreen:

---

### Post by Gustavo Sobral on 2007-08-30
Couldn't solve the issue yet...Any help?

Thx,

Gustavo

---

### Post by Gustavo Sobral on 2007-09-06
Still stuck...

Thx,

Gustavo

---

### Post by Gustavo Sobral on 2007-09-29
Hi, please! I'm still stuck on this...I need a help in order to make the host to see the VM and vice-versa, because I installed database server on VM and want to make my app running on host to access db data on VM.

Thanks in advance!

Rgds,

Gustavo

---

### Post by veloce on 2007-10-01
You could try what I've done.  It's not elegant, but has some advantages for my situation.

Host is Ubuntu 7.04

two (or more) vms:
vm 1 windows
vm 2 is IPCop with block out traffic.

Host has host only and bridged networking enabled.

vm1 is attached to host only network
virtual cop is attached to host only and bridged.

This way all communications on the host only network (between vms and host) are within vmware (and fast)

All comms to the wider network from the vm can be controlled.  I don't give my vms access to the internet for example.)

YMMV

---

### Post by Gustavo Sobral on 2007-10-02
Thanks for replying! I will try it asap and post the results.

Best Regards,

Gustavo

---

