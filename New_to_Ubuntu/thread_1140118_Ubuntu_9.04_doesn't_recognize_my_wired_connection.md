---
title: "Ubuntu 9.04 doesn't recognize my wired connection"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by abrand888 on 2009-04-27
Hello,

I am running the live version for the time being. I am connected to the outside through a wired network and use Earthlink. I Windows, I am connected automatically. I downloaded Ubuntu 9.04 and when I click on the network icon on the upper tray, I selected auto etho but it isn't connecting me at all. When I right click enable network, it says checked but when I click Network Connections, under Wired it states Auto etho but states never.When I click on Auto Etho edit, it opens up another window editing Auto Etho connect automatically is checked, the MAC address is listed in the window, MTU is automatically bytes, I click apply and the Network 

Screen reappear and states   Auto Etho   Never.

How can I get rid of never and be connected to my wired network ?

Thanks

---

### Post by Cypher on 2009-04-27
What is your network setup? Do you connect directly to a cable/dsl-modem or go through a router? Do you run special software on Windows to connect to Earthlink?

---

### Post by abrand888 on 2009-04-27
My network adapter is a Nvidia Nforce Networking controller and there is also a Nvidia Network Bus enumerator which works in my windows setup. I am using a router. I do not run any special software in windows to Earthlink

---

### Post by Cypher on 2009-04-28
Can you give us the output of
```

lspci -v
ifconfig -a
lsmod

```

I think I have the same network controller as you..

---

### Post by abrand888 on 2009-04-28
Here are the files.

---

### Post by abrand888 on 2009-04-30
Did these files come in ok that you can understand them ?

---

### Post by abrand888 on 2009-05-04
Cypher,

Did the text files come in correctly . I ran the three files you asked me to run and the results are in the files.

Thanks

---

