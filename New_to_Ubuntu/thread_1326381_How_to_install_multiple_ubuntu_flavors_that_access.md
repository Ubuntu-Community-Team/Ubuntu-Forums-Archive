---
title: "How to install multiple ubuntu flavors that access the same files?"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by BT1 on 2009-11-14
Alright, I tried to make the title include the idea.

To clarify, I want to install Kubuntu, Ubuntu, and xubuntu on the same partition, to access the same files, but I don't want different partitions for the OSes. Is it possible to install all three on the same partition and select one on startup?

I want to test some stuff to see which I prefer, using the same files on the same drive.

One more question, if it is possible to do that... would it be possible to install 64 bit editions on the same partition along side x86 ones, or would they need their own partitions?

Thanks for the help!

---

### Post by eagle416 on 2009-11-14
as for question 1, yes.

I think you just
```
sudo apt-get install kubuntu-desktop xubuntu-desktop
```
and then you can choose at the login manager.

I don't know anything about the 64-bit thing.

---

### Post by waspbr on 2009-11-14
just go to synaptic and search for kubuntu-desktop for the kubuntu environment and xubuntu-desktop for xubuntu, install those packages. 

Once you are done, you will be able to select which environment you want want to access at the login screen, in the sessions menu. 


as for the 64 bit thing, I don't think so.

gl

---

### Post by Paqman on 2009-11-14
> **BT1 said:**
> would it be possible to install 64 bit editions on the same partition along side x86 ones, or would they need their own partitions?


They'd need their own root partitions, although they could share common swap and /home partitions.

---

