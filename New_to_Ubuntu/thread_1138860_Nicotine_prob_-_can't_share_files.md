---
title: "Nicotine prob - can't share files"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by loobyloo on 2009-04-26
Hello
I've had a couple of rather snotty notes from other Nicotine users who (quite understandably!) are annoyed that I'm not sharing my files.  I can't really work out why they're not appearing in others' searches. My ahred files are in .../.nicotine/temas.

This is what my sharing settings in Nicotine look like

[http://loobynet.co.uk/images/nictotne.png](http://loobynet.co.uk/images/nictotne.png)  (that's not a spelling mistake btw!) 

However, when I ask Nicotine to browse my files, it's saying I'm not sharing anything (as you can see from the image).

Does anyone know what might be wrong?
Many thanks

---

### Post by loobyloo on 2009-04-26
Sorry to bump this but here's my output from iptables -L: 

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:2240 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:2234 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

-----------------
2240 and 2234 are the ports used by Nicotine so I assume this means the ports are open?

---

