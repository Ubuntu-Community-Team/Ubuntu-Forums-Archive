---
title: "Terminal commands not working on Kubuntu 10.04"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2010-06-21
I have recently been trying out Kubuntu 10.04 and after manually setting my modem up and getting it to work I have found "Konsole" (Terminal for ubuntu users) to be unresponsive.

I typed:
sudo apt-get install aptoncd

> but got this afterwards:
nightstrike@KMetalTux:~$ sudo apt-get install aptoncd
[sudo] password for nightstrike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package aptoncd

Any ideas on how to get Konsole (Terminal) working properly?

---

### Post by snowpine on 2010-06-21
There's nothing wrong with Konsole. :) Try:

```
sudo apt-get update
sudo apt-get install aptoncd
```

---

### Post by wojox on 2010-06-21
Nightstrike isn't in the repo's

---

### Post by snowpine on 2010-06-21
> **wojox said:**
> Nightstrike isn't in the repo's

:lolflag:

---

### Post by Nightstrike2009 on 2010-06-21
> **By wojox:** Nightstrike isn't in the repo's

I hope not I am here. LOL

Cheers Snowpine that worked :-) any idea how I run aptoncd after installation, I am new to Kubuntu (I am familiar with ubuntu 10.04 though) :-)

---

### Post by snowpine on 2010-06-21
> **Nightstrike2009 said:**
> I hope not I am here. LOL

Cheers Snowpine that worked :-) any idea how I run aptoncd after installation, I am new to Kubuntu (I am familiar with ubuntu 10.04 though) :-)

Glad it worked. :) I have never used aptoncd before, sorry. :(

---

### Post by Nightstrike2009 on 2010-06-21
In ubuntu it just turns up on menu but doesn't in kubuntu even when you search for it with Kmenu, anyone any ideas?

---

### Post by lkjoel on 2010-06-21
Ok, I attached APTonCD source files.

Just build it.

---

### Post by snowpine on 2010-06-21
> **Nightstrike2009 said:**
> In ubuntu it just turns up on menu but doesn't in kubuntu even when you search for it with Kmenu, anyone any ideas?

Press Alt+F2, type 'aptoncd'?

---

### Post by lkjoel on 2010-06-21
APTonCD is not in the ubuntu repositories.

---

### Post by snowpine on 2010-06-21
> **lkjoel said:**
> APTonCD is not in the ubuntu repositories.

[http://packages.ubuntu.com/lucid/aptoncd](http://packages.ubuntu.com/lucid/aptoncd)

---

### Post by lkjoel on 2010-06-21
Oops, I forgot to reload the packages!
It just took me
```
sudo apt-get update
sudo apt-get upgrade
sudp apt-get install aptoncd
```
to install it.

---

### Post by Nightstrike2009 on 2010-06-21
> **by lkjoel:** APTonCD is not in the ubuntu repositories.

Yes it is both ubuntu and kubuntu download aptoncd from the repos.

Thanks to everyone for trying to help but in my personal opinion Kubuntu just makes life hard for the sake of it so I am going back to Ubuntu 10.04 where life is much easier, if Kubuntu wants to "shoot itself in the feet" like this then fine, just don't expect me to stand around and watch, I've been put off Kubuntu for good. :-(

**UPDATE 24/06/10:** I hate it when people just "up sticks to another distro" but I came from Ubuntu and have returned to it, Kubuntu really is that bad in my opinion (possibly never returning to it), I think xubuntu has promise, but I am sticking with Ubuntu now. :-)

---

