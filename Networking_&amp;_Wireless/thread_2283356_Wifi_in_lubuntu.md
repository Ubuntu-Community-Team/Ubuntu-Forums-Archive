---
title: "Wifi in lubuntu"
date: 2015-06-21
forum: Networking &amp; Wireless
---

### Post by Cristian1969 on 2015-06-21
Hi, my frends, I have un comp with 2 sistems - windows and lubuntu. I have wifi in windows, and in lubuntu I work with cable. I want setup wifi and I wont work in lubuntu. What I must to do?

---

### Post by Bucky Ball on 2015-06-21
*Thread moved to **Networking & Wireless**.*

Welcome. Well, you can give us more information. Unplug the cable, open a terminal and copy/paste the following command:

```
sudo lshw -C network
```

Post the output here between code tags (see the last link in my signature). 

Also, what have you done to fix it, if anything? What have you found online about how to fix it and what have you tried? Links if possible. What exactly happens when you try to connect, with the cable out?

Have you unplugged the cable and rebooted the machine? What happens with wifi when you try to connect? What message are you getting? Are you being notified there are wireless networks available?

With the cable in and online, do an update then open 'Additional Drivers'. What, if anything, is listed in there?

Any other useful info you can think of, thanks. :)

---

### Post by Cristian1969 on 2015-06-21
I haved ubuntu sometime. In ubuntu I have icon for wifi in task bar. I hit the icon and I see the wirelles disponibles. And I hit the wirelles I want and that it s. But in lubuntu I d ont know where I find command for wirelles. How I can see the wirelles connections availables. I put in terminal your comand and the terminal show me configuration: autonegation=on brad cast= yes etc.

---

### Post by Bucky Ball on 2015-06-21
Please follow the instructions in my last post. Post the entire output of that command here rather than 'etc. etc.'. We need that information which is why I asked for it. Thanks. 

On the information you've given to this point we can't really help much. The network icon should be in the top panel on the far right. It might be on the left. Move the mouse over each icon slowly and see what they all are. Also, have you searched online for a solution to your issue? I'm not sure if what you want to know is where the network icon is or if you want to know how you get your wireless network card working. :-k

---

