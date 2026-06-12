---
title: "Port forwarding"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by divided_by_zero on 2011-04-04
I started using Ubuntu 10.10 with Transmission recently and I'm having trouble figuring out how to set up port forwarding so I can use Waffles again. Thing is, Transmission always reports the used port as closed and the same goes for canyouseeme.org.

I'm really not comfortable enough with Ubuntu yet to try to mess with this on my own, so I'm really hoping you guys can help me. I tried googling and looking at previous port forwarding threads on the forum, but they all seem very specific.

Thank you in advance!

---

### Post by ajgreeny on 2011-04-04
I have no idea what Waffles might be, but can you use transmission to download, for example, ubuntu live CD .iso files?

I have made no changes to the default in transmission's preferences window, and I get good d/l speeds close to my ISP max.  I have attached a screenshot of the preferences on my system;  if your's are different, see if a change there will help.

---

### Post by ~Plue on 2011-04-04
> **divided_by_zero said:**
> 
I'm really not comfortable enough with Ubuntu yet to try to mess with this on my own, so I'm really hoping you guys can help me. I tried googling and looking at previous port forwarding threads on the forum, but they all seem very specific.

in a default ubuntu install you wouldn't need to 'open ports', so most likely, its the firewall settings on your router if you're using one.

router settings differ from manufacture / model so try [http://portforward.com/](http://portforward.com/) and see if there are instructions for your router make/model. (skip the advertisements for their program)

---

### Post by divided_by_zero on 2011-04-04
Thank you both for replying :)

I just looked into it and I managed to work it out at last. In case anyone else has this problem, here's what I did.

I already did set up the port on the router's end, but I also had to use the "sudo ufw allow [port number]" command for the port to finally show as open.

And that was that! :D

---

