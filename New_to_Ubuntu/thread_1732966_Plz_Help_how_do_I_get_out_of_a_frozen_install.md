---
title: "Plz Help: how do I get out of a frozen install ?"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by polaatx on 2011-04-18
I installed ubuntu 10.4 a week ago on an Acer 3680 laptop.My first experience with linux. I keep seeing these pleas for help all over the this forum and so here I go:

It has frozen half-a-dozen times (on installs of Picassa, zoneminder, LightZone, and google earth, etc.)  forcing me to shutoff computer manually.  Usually freezen on "preparing package..." I have search forums but have not found any help other than how to remove the unfinished installation after restart. 

Here's the install that's frozen right now, on goggle earth: [http://tinypic.com/m/egbq5s/3](http://tinypic.com/m/egbq5s/3)

Here's terminal screenshot of a couple of unsuccessful tries I've done to stop the install so I don't have to shut the machine manually again: [http://tinypic.com/m/egbq84/3](http://tinypic.com/m/egbq84/3)

Please respond with newbie language. I am learning but much of what is said in these forums goes over my head.

---

### Post by polaatx on 2011-04-18
I just relized pressing Ctrl-C offers option to get out of the frozen install. 
[http://tinypic.com/m/egbqs0/3](http://tinypic.com/m/egbqs0/3)    I tried it many times but it won't stop. 

Is the only way to get out of this is to shut down the machine manually? 

Shutting down ubuntu doesn't help. It shuts down all programs except this nefarious never-ending install.

---

### Post by Dutch70 on 2011-04-18
Hi and welcome to UF

[[COLOR="Red"]http://kember.net/articles/reisub-the-gentle-linux-restart/[/COLOR]]("http://kember.net/articles/reisub-the-gentle-linux-restart/")

A good way to remember that is...
[COLOR="red"]R[/COLOR]eboot
[COLOR="red"]E[/COLOR]ven 
[COLOR="red"]I[/COLOR]f
[COLOR="red"]S[/COLOR]ystem's
[COLOR="red"]U[/COLOR]tterly
[COLOR="red"]B[/COLOR]roken

Or, Raising Skinny Elephants Is Utterly Boring. You can do it in that order also. 

As far as the freezing, what graphics card are you using? 
If you're not sure, open a terminal and run the following command.
```
lspci | grep VGA
```

Does it freeze if you login to recovery mode?

Edit: When you get the error about "could not get /var/dpkg/lock or whatever, it's usually because you have synaptic package manager or software center opened.

---

### Post by polaatx on 2011-04-18
Thanks so much for your reply.

> As far as the freezing, what graphics card are you using? 
If you're not sure, open a terminal and run the following command.
```
lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

> Does it freeze if you login to recovery mode?

It freezes only when I am installing something. It's always package manager.  I'll try installing in recovery mode and report back. 

> 
Edit: When you get the error about "could not get /var/dpkg/lock or whatever, it's usually because you have synaptic package manager or software center opened.[/QUOTE]

Yeah. I figured that. thanks again.

---

### Post by Dutch70 on 2011-04-18
Hmm, this is my graphics card...
> 00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

I had a problem with my system freezing also, but it would do it at any random time. It turned out to be a problem with Compiz. which I solved with the link in my sig. Not sure if it will help you any, but maybe having that info will help you to get it solved.

---

