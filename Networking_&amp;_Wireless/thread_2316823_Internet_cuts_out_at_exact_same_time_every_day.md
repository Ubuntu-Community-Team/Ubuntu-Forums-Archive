---
title: "Internet cuts out at exact same time every day"
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by dale20 on 2016-03-11
Since building my new desktop my internet dies every day a few minutes before 9:30pm like clockwork. I'm running Ubuntu 14.04 with an ASUS Z170k motherboard and a Telstra TG797nv3 router. Any ideas what could be causing this?

---

### Post by kc1di on 2016-03-11
Hello dale20  and Welcome to Ubuntu :)
That would sound to me like your Internet provider has a problem.  I would check with them first.

---

### Post by dale20 on 2016-03-11
Hi, thanks for the welcome, I'm a comp sci student and have been resisting using Linux as my main operating system for as long as humanly possible just because I was so used to Windows and used to be a pretty into gaming and still occasionally indulge. 

Given the amount of C programming and other stuff I have to do this semester though it is not feasible for me to not be using Linux as my main operating system, but I have come to the light and I actually don't mind it, except for the lack of support for gaming and no DX12. 

I am little bit skeptical that this is a problem with my internet provider, I have been using the same ISP for years and have never had any problems. I can literally count on one hand the number of times my internet has cut out in the past couple of years, but I could be wrong. Since building this new PC a few weeks ago I have been having issues and only realized in the past couple of days it happens at the exact same time. 

I suspect it is either a faulty ethernet adapter on the motherboard, hopefully a new adapter will fix this, or possibly, because it is happening at the exact same time every day, some kind of setting in Ubuntu, like software updates, where it is downloading something that is causing the internet to cut out somehow. If it does happen to be something in Ubuntu I will try to update this thread later.

---

### Post by kc1di on 2016-03-11
Ok I'm not sure what it could be in Ubuntu - that would happen at almost the exact same time each day.  
I once had a similar problem that happened for a min. or so each day and turned out to be the servers were being changed at that same time each day.
they corrected that and it went away. 
Good luck with your studies.

---

### Post by Hadaka on 2016-03-11
Hi, here are a couple things you might check .
In the Launcher..left side click..
[COLOR=#ff0000]>Ubuntu Software Center[/COLOR] icon
**then at the very top of the screen..not the software center box
but the same level as the clock and envelope,,it says Ubuntu Software Center
top far left. click..
[COLOR=#ff0000]>Edit[/COLOR]
[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000]>Software Sources
>Updates  tab
[/COLOR]#see attached
[ATTACH=CONFIG]267751[/ATTACH]
As you can see mine is checked daily, yours may be also
change that and see if the disconnects follow the change.
also make sure the last 2 choices are NOT checked, like attached.
Next lets take a look at your crontab file and see if anything is scheduled in there that you are not aware of.
please do and post to display..
```
crontab -l
```
thanks

---

