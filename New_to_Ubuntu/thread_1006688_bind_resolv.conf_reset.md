---
title: "bind resolv.conf reset"
date: 2008-12-09
forum: New to Ubuntu
---

### Post by gerreth on 2008-12-09
hi,

I successfully installed bind on laptop (part of a school project)
However when i connectd my pc to a different network (school network, home network etc) my resolve.conf file in /etc directory automaticaly get's erased by my ISP (i quess)

When i switch my ip from automatic to static the file doesn't get erased.

Is there another way around instead of changing my ip everytime i connect to a network?


Thank you very much!

---

### Post by cmnorton on 2008-12-10
Using Network Manager, you should be able to set up different connections for different places you go.

I would also preserve a copy of resolv.conf, once you have it the way you want it (for the connection you use the most).

sudo cp /etc/resolv.conf /etc/resolv.conf.keep (or a name that means something to you).

---

### Post by superprash2003 on 2008-12-10
i presume you want to use your own DNS servers manually.. ?? if so you could follow this . Opendns used in this example 208.67.222.222 and 208.67.220.220 .. change as you wish [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

