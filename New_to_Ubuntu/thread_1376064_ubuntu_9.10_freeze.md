---
title: "ubuntu 9.10 freeze"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by robond8 on 2010-01-08
hello,

my Ubuntu 9.10 freezes after I log in and start browsing files, internet, playing music, etc etc. it seems to hold out longer if I have a movie or music playing...It's really weird. I may have a hardware failure but I've used this computer with no problems on the 3 previous Ubuntu versions with no problems...

my specs: HP tower, 740 mb RAM, intel Celeron

It's an old computer so I am running the 32 bit version of Karmic.

Please help! Thanks!

---

### Post by J V on 2010-01-08
Open up your system monitor, its possible a rouge app sucks up all the ram and you have no swap...

if so, the monitor should pick it up...

---

### Post by robond8 on 2010-01-08
> **J V said:**
> Open up your system monitor, its possible a rouge app sucks up all the ram and you have no swap...

if so, the monitor should pick it up...

I checked everything out in the SM and nothing is taking up more than 5 mb except for google chrome (which I am using now) which is taking up like 50 mb. I my processor is running at like 30% so it's not "working too hard." 

Thanks for that tip, any thing else I can try?

---

### Post by Yvan300 on 2010-01-08
Yeah i sometimes experience some lockups, why not try using the old kernel?

---

### Post by robond8 on 2010-01-08
> **Yvan300 said:**
> Yeah i sometimes experience some lockups, why not try using the old kernel?

How do I do that? Will it be like reverting to 9.04?

---

### Post by J V on 2010-01-08
No, its an option when booting grub... that 30% isn't normal for just viewing webpages, which is using how much?

---

### Post by Yvan300 on 2010-01-08
Well if you're up to date then when your computer starts you should see the grub screen. If not wait for the part where there is a countdown and click esc. Then pick the older kernel from the menu that comes up.

---

### Post by robond8 on 2010-01-08
> **Yvan300 said:**
> Well if you're up to date then when your computer starts you should see the grub screen. If not wait for the part where there is a countdown and click esc. Then pick the older kernel from the menu that comes up.

Oh I see, I forgot what kernals were. :P 

I will try that but I do know that Karmic has updated like 3 kernals and the freezing problem has happened. But I guess that there could be a different outcome if I switched to an old one.

---

### Post by robond8 on 2010-01-08
> **J V said:**
> No, its an option when booting grub... that 30% isn't normal for just viewing webpages, which is using how much?

chrome is using about 70 mb of RAM when it is in use.

---

### Post by robond8 on 2010-01-08
Okay I tried booting an older kernal and honestly it only made the OS freeze faster. So I think it's something else. Any ideas?

---

### Post by Yvan300 on 2010-01-08
Hmmm, does it freeze when you are doing something in particular?

---

### Post by robond8 on 2010-01-08
> **Yvan300 said:**
> Hmmm, does it freeze when you are doing something in particular?

Nothing in particular. It seems to do BETTER when I have rythmbox, or banshee running music. That's the only thing I've noticed...

---

### Post by Sef on 2010-01-08
Applications > Accessories > Terminal  

type in 'top'.

---

### Post by iponeverything on 2010-01-08
I think I am going to skip 9.10 all together, I have installed it twice for testing on two different laptops and both times the issues were beyond the usual small annoyances. 8.10 and 9.04 both work great on my hardware..

---

### Post by robond8 on 2010-01-08
> **Sef said:**
> Applications > Accessories > Terminal  

type in 'top'.

Response to "Sef"

When I run that command the terminal produces something similar to what the System Monitor looks like. What does this help me with? Is there something in particular that you want me to find out? Thanks!

---

### Post by robond8 on 2010-01-08
response to "iponeverything":

good for you! I am too curious every time a new version comes out! :)

---

### Post by Yvan300 on 2010-01-09
Htop is the same as system monitor but a bit more accurate. Well maybe your problem is just some hardware incompatibility. What i suggest you do is to stick with jaunty for the time being until lucid is released. But then again i'm a noob and are not that good at troubleshooting in under this topic. So you could wait for a more experienced guy to guide ya straight. :)

---

### Post by bingobingo on 2010-01-09
I am having the same problems, it does not matter what desktop manager I using, I get constant freezing. No problem with 7.10 or 8.?, it starting with upgrade to 9.10. It looks like I going to downgrade and or move to another distrabution. Why so many upgrades anyway?

---

### Post by robond8 on 2010-01-09
> **Yvan300 said:**
> Htop is the same as system monitor but a bit more accurate. Well maybe your problem is just some hardware incompatibility. What i suggest you do is to stick with jaunty for the time being until lucid is released. But then again i'm a noob and are not that good at troubleshooting in under this topic. So you could wait for a more experienced guy to guide ya straight. :)

Haha okay thanks for your help. So this issue is STILL UNSOLVED, if anyone out there can help me (and the others too I guess) that would be great! Thanks!

---

