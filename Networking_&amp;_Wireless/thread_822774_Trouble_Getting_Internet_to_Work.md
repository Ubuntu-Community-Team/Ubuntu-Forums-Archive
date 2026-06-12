---
title: "Trouble Getting Internet to Work"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Inc0ming on 2008-06-08
Hello,

I have a WMP300N wireless card paired with a WRT300N router with a dual boot of Windows XP and Ubuntu. My internet on XP works fine but Ubuntu's isn't. I can't figure out a way to install ndiswrapper. I don't have a USB flash drive either to help me get it working. So please, help me try to figure out a way to get my internet working.

Keep in mind that I don't have the CD.

---

### Post by joebrueske on 2008-06-08
This should do it. Just open a terminal and copy and past this in. I don't use it but it works. There is also [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) should it not work.

Last year I started using Ubuntu and there's a lot of different setups for installing everything. If you're ever looking for a package go to **System > Administration > Synaptic Package Manager** and then just do a search for whatever you need.

```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

---

### Post by Inc0ming on 2008-06-08
But when I do 

```
lshw -C network
```

I recieve no logical name or drivers being listed.

And when I do the code you listed, it says

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ndiswrapper-common
```

---

### Post by Inc0ming on 2008-06-08
Bump.

---

### Post by Inc0ming on 2008-06-08
Bump.

---

### Post by Inc0ming on 2008-06-09
Bump...

---

### Post by Inc0ming on 2008-06-09
Bump...
...

---

### Post by Inc0ming on 2008-06-10
Gotta love this support.

Bump...
...
...

---

### Post by Inc0ming on 2008-06-11
Bump...
...
...
...

---

