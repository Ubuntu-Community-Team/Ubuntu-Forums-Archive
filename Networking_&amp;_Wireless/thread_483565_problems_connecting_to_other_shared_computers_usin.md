---
title: "problems connecting to other shared computers using Ubuntu"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by morpheus9602 on 2007-06-24
Hi everyone,

If there is a post already on this topic, then just refer it to me please, otherwise please respond.

I am having a hard time finding the right information on the web and on forums, so I will ask myself.

I am trying to access other computers on my network.  Most of them are Windows machines and a couple are Linux machines.

I am not able to access any computer using the computer name, but somehow it will allow me to access the intended computer using the IP address.

Ubuntu is able to see the workgroups on the network, but cannot access the computers of the workgroup.

I know I am able to share resources from this computer to another computer, since I was able to access this computer from a Windows machine with no problem.

The basic idea is that the network computers can see this computer but this computer cannot see the network computers, unless I use the IP address, but that can be a pain to have to keep track. I would rather access the computers using the computer name.

Thanks

Morpheus9602

---

### Post by Sonofmoog on 2007-06-24
> **morpheus9602 said:**
> 

The basic idea is that the network computers can see this computer but this computer cannot see the network computers, unless I use the IP address, but that can be a pain to have to keep track. I would rather access the computers using the computer name.

Try accessing a network share from a) the location bar of Nautilus.  (Type Ctrl-L to open) or, b) from the address bar of Firefox.  

For example, say you had a workgroup called Stooges and PC's Curly, Larry and Moe, and Curly is the troublemaker .. (It's *always *Curly, but I digress)

In the Firefox address bar on Curly, type 

```
smb://Moe
```

Can you see Moe?

---

### Post by morpheus9602 on 2007-06-24
Firefox does not access the computer

anymore ideas?

---

