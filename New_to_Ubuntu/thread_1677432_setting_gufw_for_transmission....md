---
title: "setting gufw for transmission..."
date: 2011-01-28
forum: New to Ubuntu
---

### Post by werty2010 on 2011-01-28
im a regular user-student whos using my pc for surfing,chatting,studing and downloading torrents(only legal of coarse) 
i was with firestarter(as a frontend) until i read that that that the project was discontinued...
so now i have gufw but i dont know how to set it up for transmission...

some help?

---

### Post by davidmohammed on 2011-01-28
this [thread]("http://ubuntuforums.org/showthread.php?t=1644518") should help you.

---

### Post by lightningfox on 2011-01-28
To allow Transmission in Gufw go to Edit > Add rule. 

Add a rule to allow Transmission in and a rule to allow Transmission out.

[IMG]http://2.bp.blogspot.com/_UlQf_UY6-uY/TTjA4r5TnUI/AAAAAAAAALs/t0B-OKGg6y8/s1600/mintfirewall2.png[/IMG]

[IMG]http://1.bp.blogspot.com/_UlQf_UY6-uY/TTjBoM874NI/AAAAAAAAALw/4ccFE43085E/s1600/mintenablefirewall.png[/IMG]

[IMG]http://4.bp.blogspot.com/_UlQf_UY6-uY/TTjBwLS-S9I/AAAAAAAAAL0/WQ7WVbiWQ5M/s1600/mintfwtransmission.png[/IMG]

[IMG]http://4.bp.blogspot.com/_UlQf_UY6-uY/TTjCJ-MdqZI/AAAAAAAAAL4/WF2zDVS7NhA/s1600/mintfw.png[/IMG]

---

### Post by werty2010 on 2011-01-28
thank you
i ran transmission before i configure gufw(the only thing i did was to enable it) and it started to up/down-load without any problems...shouldnt gufw stopped the traffic until i configure it?

---

### Post by lightningfox on 2011-01-28
Installing Gufw does not also enable it. To enable Gufw you have to click enabled in the Gufw window.

---

### Post by sffvba[e0rt on 2011-01-28
I have enabled UFW ever since I heard of it and I have never had to add a rule for letting software through before (with the exception when I was using SSH to connect to my laptop) :confused: Never gave this much thought... got to check it out when I get home :)


404

---

### Post by werty2010 on 2011-01-28
[lightningfox]("http://ubuntuforums.org/member.php?u=813667") : ive already done that when i tried it

[not found]("http://ubuntuforums.org/member.php?u=1209987") : when you do it please let us know if you have the same results

---

