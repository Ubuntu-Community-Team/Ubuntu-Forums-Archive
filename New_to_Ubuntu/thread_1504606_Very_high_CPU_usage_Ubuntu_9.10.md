---
title: "Very high CPU usage Ubuntu 9.10"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Tiwazz on 2010-06-08
Hello,

I'm using Ubuntu for about a year and using it as my default OS  i'm running Ubuntu 9.10 x86_64 fully up to date (8th of June 2010). 10.04 doesn't feel that stable and fast for me.

The problem i'm having is a very high CPU usage. I'm looking in my system-monitor now or on my conky desktop and the usage for my CPU's are hopping from 6,2% to 70% to 64% to 99% etc. This happens for both of my cores i have a laptop with a P8600 CPU in it.

The things i run right now are:
Chrome, Terminal Server Client, Rhythmbox and conky these are the active applications for me right now. if i close these applications the usage keep the same.

My system is very fast the usage doesn't effect the feeling as far as i know. The only noticeable thing is that the laptop is getting pretty hot. 

On my desktop at home it has a Quadcore Q9550 the CPU Ussage is like 0% 1% ok the system is more powerful then my laptop but i don't think the usage for my laptop is normal?

Can someone confirm this issue?

---

### Post by mörgæs on 2010-06-08
What does the command **top** show? 

(Press q for quitting top)

---

### Post by Tiwazz on 2010-06-08
The top commando shows mostly 4+ running tasks screenshot shows 13 but this was for 1 second. CPU Usage is mostly 40+%

[[IMG]http://img99.imageshack.us/img99/5782/toprx.png[/IMG]](http://img99.imageshack.us/i/toprx.png/)

---

### Post by mörgæs on 2010-06-08
If you boot the machine and run top without opening anything else, is there a heavy processor load? 

After that you just open the applications one by one to see which is causing the problem.

---

### Post by Tiwazz on 2010-06-08
I allready tried things like that, after a reboot its still around 30 - 40 + % usage.

When I don't log in and go to terminal ( ctrl + alt + F1 ) usage is like 1 - 6% when i stop GDM (sudo /etc/init.d/gdm stop) the usage is like 0 - 1%. When I go back and log-in and don't start anything its back to 30 - 40 + % usage.

***This is even after a fresh install***.

I don't notice any lag at all but it is quite annoying that my laptop is very very hot and my CPU is stressing because of.. noting?

---

### Post by mörgæs on 2010-06-09
This is strange. My only guess is compiz - how does it work, if you disable that?

---

### Post by Tiwazz on 2010-06-09
Yes it is very strange! when i disable compiz the usage is still the same! I'm absolutely not a "absolute beginner" but i couldn't post a topic in other sections except this one because i normally don't post something.

Hope it will be fixed someday thanks for your help ;)!

---

