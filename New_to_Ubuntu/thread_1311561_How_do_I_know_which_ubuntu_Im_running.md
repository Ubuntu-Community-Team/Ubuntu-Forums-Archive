---
title: "How do I know which ubuntu Im running?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by jezebel on 2009-11-02
Hi 
I have installed Ubuntu netbook remix 9,10 twice on the same pc (I'll explain why in a dif post with a big, tough question); but basically - is there a utility where I can see which Ubuntu I'm running? I just really need to see the size of the disk space of the OS to know which I'm in.

---

### Post by aktiwers on 2009-11-02
Open terminal and type:
```
cat /etc/issue
```

Edit: sorry I was a little fast there :)
Can't you just view the volumes under Places and see how much space the other Ubuntu partition has?

---

### Post by Alex Yeh on 2009-11-02
> **jezebel said:**
> Hi 
...I just really need to see the size of the disk space of the OS to know which I'm in.

try this:

open a Terminal window, from Applications>Accessories>Terminal

copy and paste:
```
df -h | head -1 && df -h | grep '^.*/$'
```
and hit return or enter. This will show you how much space you have on the root partition (the part of the drive you are booting from).

---

### Post by slakkie on 2009-11-02
> **Alex Yeh said:**
> try this:

open a Terminal window, from Applications>Accessories>Terminal
type:
```
df -h | head -1 && df -h | grep '^.*/$'
```
and hit return or enter. This will show you how much space you have on the root partition (the part of the drive you are booting from).


The short version of this: df -h /
And to figure out what you are running: lsb_release -a

---

### Post by kansasnoob on 2009-11-02
You could also install gparted:

```
sudo apt-get install gparted
```

You'll then find it in System > Administration:

[ATTACH]134406[/ATTACH]

---

### Post by jezebel on 2009-11-02
Thanks for such quick and thorough replies, guys.

Actually, I accidentally found what I needed (I'm running Netbook Remix for the first time and am totally unfamiliar with the interface). Anyway:

Accessories - Disk Usage Analyzer told me what I needed to know. I'm in my 'good' (45 gb) Ubuntu!

---

