---
title: "Wifi Connect, but No Network After Airplane Mode Turned Off"
date: 2017-03-05
forum: Networking &amp; Wireless
---

### Post by armersuender on 2017-03-05
Hello all,

Long time listener; first time caller. So, I'm running Xubuntu 16.04 with the 4.4.0 kernel on an HP TPN-C125 laptop. My laptop has a airplane mode hotkey next to the delete button that I pressed by accident.. wifi kicks out. Okay, no problem, I hit the key again, and wifi reconnects, but with one problem -- no internet. Huh okay, thinking it's a DNS issue, my first reaction is to jump into a terminal and ping 8.8.8.8. To my surprise, I get a Connect: Network Unreachable (or something to that effect). I check the route command, and there's nothing in the table. Trying to add my own route, but nope SIOADDRT: Network Unreachable (again, might have mangled that).

So, I'm not sure where the problem lies. (DHCP maybe? ...but I wouldn't have been able to recomment to wifi, I'm thinking..) It's the same problem over removing and readding the wifi connection and over reboots. Attached are my wireless specs gathered from the provide script on this site. Please let me know if you need any other information.

Thanks in advance,
RJ[ATTACH]274012[/ATTACH]

---

### Post by jeremy31 on 2017-03-05
I would try ```
sudo dpkg-reconfigure resolvconf
```
As it appears /etc/resolv.conf is empty and the route info is missing

---

### Post by armersuender on 2017-03-05
Baller! Thanks so much! I'll have to research this more, but for now it worked! it's interesting something so simple can be so destructive. haha. I'll mark as solved.

Thanks again,
RJ

---

### Post by armersuender on 2017-03-05
Hello there. 

Hmmm... I might have spoken too soon. Your solution worked right after I tried it, then I suspended to finish up things of my old laptop, and then came back to the one in question, and I got the same problem. This time, after multiple tries of applying it and reboots, your solution no longer seems effective. resolv.conf remains empty. Could there be something else blocking it from getting populated?

Thanks,
RJ

---

### Post by armersuender on 2017-03-05
Oh lordy.

You've got to love Linux. Ooookay, so APPARENTLY, there's a difference between "Restart" and "Shut Down". I've been "Restart"-ing which I supposes caches some information and doesn't do a "full reboot". Suffice it to say, that's why it wasn't populating resolv.conf. Once I did a "full reboot", that is "Shut Down" and power back up, it worked. Still not sure why suspension killed resolv.conf in the first place. It seems I'm going to have dig deeper to not to this manually each time I try to suspend.

Anyway, the problem is technically solved, so again I thank you, but if you have the time to shed any other light on the other issues, I'd love it hear it!

RJ

---

