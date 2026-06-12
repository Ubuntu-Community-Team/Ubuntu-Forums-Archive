---
title: "65-minute-old user wants to watch Youtube"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by GNPZR on 2008-12-28
Ubuntu 8.10

I googled for the past 60 minutes and my head spins. 

I'm sure this is an annoying question for seasonned users. Thanks!

---

### Post by taurus on 2008-12-28
The easiest way is to install the ubuntu-restricted-extras package.

System -> Administration -> Synaptic Package Manager -> Quick Search

---

### Post by brenan on 2008-12-28
Are you using the 32 or 64 bit version?

---

### Post by steeleyuk on 2008-12-28
Or just [click this]("apt://ubuntu-restricted-extras"). :)

Edit: does the same thing taurus suggested in reality.

---

### Post by mapes12 on 2008-12-28
I got it working by just going to the youtube website then clicking any old video. A prompt came up telling to install a Flash package (or something like that). I then had to close Firefox, relaunch it and everything works fine.

---

### Post by kansasnoob on 2008-12-28
I'd begin by installing ubuntu-restricted-extras. It's in synaptic or just go to terminal and:

```
sudo apt-get install ubuntu-restricted-extras
```

I also find that flashblock improves overall flash performance and saves system resources. It's also in synaptic or:

```
sudo apt-get install flashblock
```

Restart Firefox after installing new add-ons.

I should add that my system simply won't play flash well without flashblock and after recent updates in 8.10 flashblock (and therefore flash) would no longer work at all well for me so I made the jump to Ubuntuzilla and I've been very, very pleased!

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by steveneddy on 2008-12-28
From a link in my sig:

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

