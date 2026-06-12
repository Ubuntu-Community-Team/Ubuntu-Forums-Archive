---
title: "Ping not resolving hostname"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-09-11
Question: I use ping to ping a windows computer from Linux.
I've switched off all firewalls on both computers. 

If I ping the windows computer via its IP, it works.
If I ping the windows computer via its hostname, then it doesn't.


What's the matter ? It used to work...
The router can see both the Linux and the windows hostname perfectly.


I always get

server can't find <hostname>: NXDOMAIN

---

### Post by surfer on 2010-09-11
DNS does not seem to work correctly. does your machine know about your dns server? do you have one? 

otherwise you can just enter ipaddress and hostname in your [FONT="Courier New"]/etc/hosts[/FONT] file

---

### Post by sikander3786 on 2010-09-11
Name resolution problem.

[http://ubuntuforums.org/showthread.php?t=581325](http://ubuntuforums.org/showthread.php?t=581325)

[http://ubuntuforums.org/showthread.php?p=9830373](http://ubuntuforums.org/showthread.php?p=9830373)


[COLOR="Red"]**Edit:**[/COLOR] [Nice Ubuntu Search Engine]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ping+by+name&as_qdr=all&sa=Google+Search&lang=en#921")

---

