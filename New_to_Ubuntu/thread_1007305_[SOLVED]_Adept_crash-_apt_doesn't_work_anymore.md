---
title: "[SOLVED] Adept crash- apt doesn't work anymore"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by ashwinhgtx on 2008-12-10
I'm on kubuntu 8.10. Adept crashed while i was editing the software sources list. Now adept doesn't start at all. I enter my password and then nothing happens.
When i try any of the apt commands in the terminal this is what i get: 

E: Type 'http://ppa.launchpad.net/openoffice-pkgs/ubuntudeb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I was trying to edit the openoffice repositories when this happened. Now apt is dead.

Can someone help me fix this mess??

---

### Post by adult swim on 2008-12-10
it looks like you have put the open office ppa in your sources.list wrong.  it should look something like ```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
``` notice that if you arent running intrepid youll need to change that to either hardy or whatever you are using.  then run ```
sudo apt-get update
```

---

### Post by ashwinhgtx on 2008-12-10
I removed the openoffice repository but still it is showing me the same error. I had to do it through the software sources link in my kmenu(i got it after installing synaptic a month back) as adept still doen't launch.
But still it is showing me the same error. When i launch synaptic as such this is what i get:

E: Type 'http://ppa.launchpad.net/openoffice-pkgs/ubuntudeb' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Why is it not able to read the sources after my edits? I have removed the openoffice repository but something is blocking synaptic from reading the list. How do i fix this?

---

### Post by taurus on 2008-12-10
Did you remember to run the update from a terminal after you modified your /etc/apt/sources.list?

```
sudo apt-get update
```

---

### Post by ashwinhgtx on 2008-12-10
> **taurus said:**
> Did you remember to run the update from a terminal after you modified your /etc/apt/sources.list?

```
sudo apt-get update
```

I am still getting the error message i mentioned in the first post.
Am i not actually editing the sources list when i am doing it through the GUI because something is wrong with apt after adept crashed? I know that it is possible to edit the sources list from the terminal as this is Linux but i don't know how to do it. If i do that will it fix things?

---

### Post by taurus on 2008-12-10
```
sudo nano -Bw /etc/apt/sources.list
```
Exit it with <Ctrl>x and save it with Y.

---

### Post by SuperSonic4 on 2008-12-10
To edit sources in a terminal:
```
sudo nano /etc/apt/sources.list
```

Have you tried commenting out line 56 by putting # at the start of the line and then running```
sudo apt-get update
```

---

### Post by ashwinhgtx on 2008-12-10
Thanks adult swim,taurus and SuperSonic4. :KS:KS:KS
I commented out line 56 as you had asked me to.
Now Adept is back and so is apt.
Nothing seems impossible through the command line. :guitar:
Now i have to figure out how some updates screwed up my openoffice.org 3 installation. I'm discussing it in another thread.
Thanks a lot guys.

---

### Post by JPS77 on 2009-02-16
[SIZE="6"]Thanx[/SIZE]

I 2 had exactly the same problem and it got solved with this.
I'm just a beginer and know very little about commands.

Thanks a lot
JPS

---

### Post by parkourman01 on 2009-03-08
Ok, so i must be a complete dumbass, i am pretty new with linux tbh.
Anyway, i have this same problem, and i cannot understand what commenting line 56 means or how to do it.
If someone could either give me a complete newbie step by step guide or print screened guide i would be eternally grateful

---

