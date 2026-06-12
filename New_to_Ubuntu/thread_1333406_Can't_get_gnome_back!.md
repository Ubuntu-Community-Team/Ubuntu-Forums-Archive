---
title: "Can't get gnome back!"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by YoungD112 on 2009-11-21
Hello. I'm pretty much a noob, but I'm running ubuntu 9.10 and I wanted to try out KDE. I installed kubuntu, but now when I go to the login screen my only options are KDE and xterm, no gnome. I've gone into the software management on KDE and tried to install ubuntu again, but nothing changes, how do I fix this??

---

### Post by ikt on 2009-11-21
> **YoungD112 said:**
> Hello. I'm pretty much a noob, but I'm running ubuntu 9.10 and I wanted to try out KDE. I installed kubuntu, but now when I go to the login screen my only options are KDE and xterm, no gnome. I've gone into the software management on KDE and tried to install ubuntu again, but nothing changes, how do I fix this??

How did you install kubuntu?

---

### Post by YoungD112 on 2009-11-21
Through Synaptic.

---

### Post by cjohnston on 2009-11-21
Then you should be able to remove the packages just as you installed them.

---

### Post by wilee-nilee on 2009-11-21
Here is a link for Karmic and how to remove Kubuntu and reinstall gnome.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

You just follow the directions. copy and paste the line of programs into the terminal and watch the magic happen.

---

### Post by Magnesium on 2009-11-21
YoungD112,

Try this: after you boot up,

press Ctrl+Alt+F1
Enter your username and password to login
Type
```
sudo stop kdm
```
then
```
sudo restart gdm
```

That should get you back to your gnome login. If that works, post back and we'll see if we can get it set up permanently.

Mg

---

### Post by ayenack on 2009-11-21
```
sudo apt-get install ubuntu-desktop
```

Should do it.

---

### Post by Magnesium on 2009-11-21
> **ayenack said:**
> ```
sudo apt-get install ubuntu-desktop
```

Should do it.

I think the OP already tried that (through Synaptic, however) and it didn't work.

Mg

---

### Post by YoungD112 on 2009-11-21
> **FFEMTcJ said:**
> Then you should be able to remove the packages just as you installed them.

I didn't realize synaptic was also in KDE, sorry about my noobishness.

> **wilee-nilee said:**
> Here is a link for Karmic and how to remove Kubuntu and reinstall gnome.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

You just follow the directions. copy and paste the line of programs into the terminal and watch the magic happen.

I did this and thanks, it worked perfectly.

---

### Post by wilee-nilee on 2009-11-21
> **YoungD112 said:**
> I didn't realize synaptic was also in KDE, sorry about my noobishness.



I did this and thanks, it worked perfectly.

Keep the link to psychocats it is a very useful site, or at least remember the name psychocats, kind of sticks in your craw.

---

### Post by Soul-Sing on 2009-11-21
> keep the link to psychocats it is a very useful site, or at least remember the name psychocats, kind of sticks in your craw.

+1

---

