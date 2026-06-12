---
title: "where can I find the g++ complier?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by ricdtinsley on 2009-04-23
where can I find the g++ complier?

---

### Post by KIAaze on 2009-04-23
Install [build-essential]("apt:build-essential")

Or just [g++]("apt:g++") if you don't want the rest.

---

### Post by Godly on 2009-04-23
> **KIAaze said:**
> Install [build-essential]("apt:build-essential")

Or just [g++]("apt:g++") if you don't want the rest.

Can you please re-post link, it's not working. Thank you.

---

### Post by KIAaze on 2009-04-23
It should work if you're using Firefox in Ubuntu. I used apturls:
[https://help.ubuntu.com/community/AptURL](https://help.ubuntu.com/community/AptURL)
[https://wiki.ubuntu.com/AptUrl](https://wiki.ubuntu.com/AptUrl)

I thought it would be better than giving a command-line help. It seems I was wrong. ^^'

Here:
```
sudo apt-get install g++
```
or
```
sudo apt-get install build-essential
```

You can of course install them by using Synaptic if you don't like the command-line:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If you plan on compiling a lot from source and/or start learning programming, you really should install build-essential which contains all necessary programs like g++, make, etc.

---

### Post by djbushido on 2009-04-23
As a note, please do "sudo aptitude install build-essential" as you will need this package in Linux sometime later. I guarantee it. Save yourself some trouble and install it now.

---

### Post by Godly on 2009-04-24
Thank you, KIAaze

---

### Post by Dileeshvar on 2009-04-24
It is installed by default 
But still you can install it using
apt or from synaptic package manager.

---

