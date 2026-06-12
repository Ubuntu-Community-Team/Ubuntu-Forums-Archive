---
title: "cd/dvd burning software"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by KHAnet on 2009-02-22
looking for the best program for burning cds and dvds. any suggestions? thanks in advance.

---

### Post by taurus on 2009-02-22
Best for one person might not be the best for others.  You just have to try them out and see which one offers what you want or need:  Brasero, Gnomebaker, k3b, etc.

---

### Post by dasan on 2009-02-22
Try k3b its the best software i ever found
U can get it from packet manager 
[http://k3b.plainblack.com/](http://k3b.plainblack.com/)

---

### Post by binbash on 2009-02-22
I prefer nerolinux over brasero or k3b

---

### Post by paydaydaddy on 2009-02-22
+1 for K3b. Haven't tried nerolinux, but would expect it to be good.

---

### Post by MrWES on 2009-02-22
> **KHAnet said:**
> looking for the best program for burning cds and dvds. any suggestions? thanks in advance.

K9Copy: it'll rip, shrink if necessary and burn your DVD.

or you if you want a complete bit for bit copy you can try this from the command line:

```
dd if=/dev/YOURDEVICE of=dvd.iso
```

Or if you want to rip the main title:

```
mplayer dvd://1 -dumpstream -dumpfile dvd.vob
```

I've had sound sync issues with the last command, so I've resorted to using Handbrake.

Bill

---

### Post by Doug11 on 2009-02-22
It's more of a personal preference thing between K3B and Linux Nero. I like K3B because it can do pretty much everything Nero can do. Easy to use and user friendly. Just because I had problems in the past with Nero. but like I said, it's what you like.

---

### Post by MrWES on 2009-02-22
> **Doug11 said:**
> It's more of a personal preference thing between K3B and Linux Nero. I like K3B because it can do pretty much everything Nero can do. Easy to use and user friendly. Just because I had problems in the past with Nero. but like I said, it's what you like.

Correct me if I'm wrong, but K3B can not shrink a dual layer DVD to fit on a single layer, correct? I've used K9 copy and then burned with K3B.

Bill

---

### Post by Doug11 on 2009-02-22
> **MrWES said:**
> Correct me if I'm wrong, but K3B can not shrink a dual layer DVD to fit on a single layer, correct? I've used K9 copy and then burned with K3B.

Bill I don't know, can it? Can Nero do it? As far K9 copy, I made no reference to it at all.

---

### Post by Steve H on 2009-02-22
I've messed around with quite a few burning progs on Ubuntu and I'm now using GnomeBaker for straight burning of iso's. I miss Nero being able to encode and then burn vid files for playing on DVD players, but I use Devede and GnomeBaker, just takes a bit longer.

I definitely found K3b and GnomeBaker to be the best so far

It really depends what you want to do with it. Ubuntu requires a bit more mix'n'match with progs to get some of the same functionality that Nero gives. Let's face it Nero raised the bar fairly high!!

;)

---

### Post by MrWES on 2009-02-22
K3B can certainly copy DVD's, if you have a dual layer burner, then you're good to go. However, if you don't K3B will not shrink it down to fit. Therefore, the combination of K9Copy (output to iso) and K3B to burn the iso works very nicely.

Bill

---

