---
title: "Questions &amp; Help with setting up Swap Space"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by bamim2 on 2010-01-05
I have a dual boot system with Ubuntu installed on its own partition of a hard drive that has Windows XP installed on the other partition. I'm pretty sure it didn't setup any swap space during the installation. I'm not 100% sure how to tell, but if I do the 'df' command I don't see any swap space. 

I've been on this web site for 2 hours looking at info on swap space & I finally gave up & decided to just ask these questions:

1) How can I tell if & how much swap space I have setup? 

2) Can I still setup swap space without destroying what's already setup on my hard drive? 

3) If I can setup swap space without destroying my current setup, how do I do it?

---

### Post by howefield on 2010-01-05
> **bamim2 said:**
> How can I tell if & how much swap space I have setup? 

Go to System > Administration > System Monitor.

Around the middle of the application window, do you see swap usage indicator next to the memory usage ?

The other questions can be answered depending on the outcome of your first.

---

### Post by Cheesemill on 2010-01-05
df only shows devices that have mount points, it doesn't show swap. What's the output of:
```
swapon -s
```

---

### Post by bamim2 on 2010-01-05
Yes! On the 'Resource' tab, there's a section that's got "Memory & Swap History" & below that it shows my 'Swap'! Thanks! I looked right passed that 100 times & totally didn't see it. Since we're here... it shows 2.3GiB Swap & 2.0GiB Memory. 

Does that mean I don't really need to make any changes to it then? 

I was hoping that would be the case since I let the installation program do its thing. 

Thanks again for helping me see the totally obvious... Said the bonehead nub. =:-)

---

### Post by Cheesemill on 2010-01-05
Yep, you're all good. I've never known the installer to not setup a swap space unless you explicitly tell it not to.

---

### Post by howefield on 2010-01-05
> **bamim2 said:**
> Does that mean I don't really need to make any changes to it then?

Looks like it ;)


:guitar:

---

### Post by bodhi.zazen on 2010-01-05
> **Cheesemill said:**
> df only shows devices that have mount points, it doesn't show swap. What's the output of:
```
swapon -s
```

Cool Story Bro =)

I have always used

```
free -m
```

---

### Post by Cheesemill on 2010-01-05
> **bodhi.zazen said:**
> Cool Story Bro =)

I have always used

```
free -m
```

Me too, I just man'd (is that a word) swapon to make the result as unambiguous as possible for bamim2

---

### Post by bamim2 on 2010-01-06
Thank you both for helping me out with this. I've logged both commands in my "central database" for future reference. I have 10+ years of Solaris UNIX experience, but about 2 months (can ya tell?) Ubuntu Linux experience. I've been spending a lot of time trying not to shoot myself in the foot. 

Rock on!!

---

### Post by J V on 2010-01-06
> **bamim2 said:**
> I have a dual boot system with Ubuntu installed on its own partition of a hard drive that has Windows XP installed on the other partition. I'm pretty sure it didn't setup any swap space during the installation. I'm not 100% sure how to tell, but if I do the 'df' command I don't see any swap space. 

I've been on this web site for 2 hours looking at info on swap space & I finally gave up & decided to just ask these questions:

1) How can I tell if & how much swap space I have setup? 

2) Can I still setup swap space without destroying what's already setup on my hard drive? 

3) If I can setup swap space without destroying my current setup, how do I do it?There are 2 ways to go about this:

1: Preferred, create a swap partition
2: Less likley to cause damage (although #1 was already unlikley), Create a file on the harddrive and hook it to swap

---

