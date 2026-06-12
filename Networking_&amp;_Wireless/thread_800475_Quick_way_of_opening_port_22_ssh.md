---
title: "Quick way of opening port 22 ssh"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by joplass on 2008-05-19
what is the quick way of opening port 22 for ssh connection.  i have three machines two are debian servers and one is ubuntu notebook.  both debian machines connect to each other but none connect to the notebook and the notebook can't connect to them either.  anyway i don't the servers connecting to the ubuntu notebook.

i get this at the terminal
```
~$ ssh username@host.domain_name.com
ssh: connect to host host.domain_name.com **port 22: Connection refused**

```

---

### Post by tamoneya on 2008-05-19
how is everything currently networked.  It maybe that there is a firewall in your router that is block access on port 22.

---

### Post by wannadumpwindows on 2008-05-19
Did you install the ssh package on the Ubuntu machine?

Edit: You can also use Firestarter to open the port to the specific hosts that you want to allow.

---

### Post by Iowan on 2008-05-19
> **wannadumpwindows said:**
> Did you install the ssh package on the Ubuntu machine?More specifically - the ssh server?  Not a real concern if you don't want the servers connecting to the notebook. Does this [HowTo]("https://help.ubuntu.com/community/SSHHowto") help?

---

### Post by joplass on 2008-05-20
> **tamoneya said:**
> how is everything currently networked.  It maybe that there is a firewall in your router that is block access on port 22.

i read somewhere that router port 22 has no impact on ssh but the linux internal firewall does.  i am not too sure since this is the first time that i play with ssh. anyway i tried opening that port with tcp and udp with no luck.

---

### Post by joplass on 2008-05-20
> **wannadumpwindows said:**
> Did you install the ssh package on the Ubuntu machine?

Edit: You can also use Firestarter to open the port to the specific hosts that you want to allow.

yes, the ssh package is installed and it came with both client and server.
if you know where i can find a how to for the firestarter i will be grateful.

---

### Post by joplass on 2008-05-20
> **Iowan said:**
> More specifically - the ssh server?  Not a real concern if you don't want the servers connecting to the notebook. Does this [HowTo]("https://help.ubuntu.com/community/SSHHowto") help?

i will have to give that link a try tonight when i get home.

---

### Post by tamoneya on 2008-05-20
> **joplass said:**
> i read somewhere that router port 22 has no impact on ssh but the linux internal firewall does.  i am not too sure since this is the first time that i play with ssh. anyway i tried opening that port with tcp and udp with no luck.

They both can and from my experience it seems like it is often a hardware issue.  Even so we still need to know how things are configured if we are to sort out the linux firewall.  Is everything connected to one router?  Is the laptop at work on an external connection? etc

---

### Post by joplass on 2008-05-20
> **tamoneya said:**
> They both can and from my experience it seems like it is often a hardware issue.  Even so we still need to know how things are configured if we are to sort out the linux firewall.  Is everything connected to one router?  Is the laptop at work on an external connection? etc
everything is connected to a router on a home network.  once i get everything working at home i would like to get to one of the servers from work on a windows machine.
thanks

---

### Post by joplass on 2008-05-20
now this is weird.  i got home fired up my ubuntu notebook, brought up nautilus and all of a sudden i can log into both of my debian servers.  this is not good because i would like to know what i did not do right in the first place for ssh not to work.  at this point i did not even open port 22 on my router.

---

### Post by joplass on 2008-06-06
now that i have eveything working at home i am trying to get to one my machines at home from work.  i follow this link but it did not work: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
is there anything i can try?  maybe use my plublic ip address instead of the private address of the machine?

---

