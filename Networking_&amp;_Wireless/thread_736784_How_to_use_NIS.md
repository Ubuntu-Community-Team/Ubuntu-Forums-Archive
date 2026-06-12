---
title: "How to use NIS"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by expatCM on 2008-03-27
I have set up the client and the server but I do not see how to use NIS.

What I am expecting is to have the same id on both client and server.  What happens is that the client has one id and the server has another.

From a client if I run rpcinfo -p and rpcinfo -p nisdomain or ip I see all the necessary processes loaded.

If from the client I run ypmatch user passwd I get the server id which is what I want.

If I putty to the server and use id user I get the same id.  If I run id user on the client I get the local id and I was anticipating the server id.

I think I did not do something but I do not know what that is.  Can anyone tell me?

---

### Post by Eiríkr on 2008-03-27
I'm no expert by a long shot, but as I understand it, NIS doesn't mean you have the same UID / GID on every machine, but rather that a username held in common can be mapped to the specific UID / GID used on each specific machine.  So user "rutabaga" might be UID 1001 on Machine A, UID 506 on Machine B, and UID 1203 on Machine C, but with NIS (most commonly used for NFS shares, perhaps?) that same username will be matched up with the appropriate UID.  

Does that make sense?

Cheers,

Eiríkr

---

