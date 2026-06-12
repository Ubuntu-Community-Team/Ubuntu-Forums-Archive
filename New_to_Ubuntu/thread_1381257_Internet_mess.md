---
title: "Internet mess"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by JakeFrederix on 2010-01-14
Currently there are two available internet connections. My own wireless, and that of my neighbours.
For some reason, some programs simply will not work with my internet connection, but gladly accept the other.
Firefox works with both, aMSN only with my neighbour's, synaptic only with neighbour's.

How can I resolve this problem?

---

### Post by Björn on 2010-01-14
I'm no expert but it sounds like the problem might be in your router. Do you have a firewall or anything of the like in it? It might block some ports.

(to log in to it you usually go to 192.168.0.1, 192.168.0.0, 192.168.2.0 or something like that with firefox, there might be an instruction on the backside of it)

Björn

---

### Post by J V on 2010-01-14
Go to the router (like the man said) and enable UPnP

---

### Post by JakeFrederix on 2010-01-14
Alright, I've found that part. I can now add exceptions to the firewall, but honestly, it's still not easy.
Now I have to find out which program uses which ports.

---

### Post by JakeFrederix on 2010-01-14
To enable uPnP check 'enable uPnP' and then select a connection.
No idea what that means. Can choose from pvc0 to pvc7.

---

