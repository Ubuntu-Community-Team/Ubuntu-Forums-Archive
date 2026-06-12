---
title: "new Ubuntu installation problem"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by squall51489 on 2010-01-11
Hello there, 
I have recently installed Ubuntu 9.10 on my laptop, dualbooting alongside windows 7. Everything was working well, but randomly when I booted into ubuntu it just hangs then goes to a black screen 2 underscores.

I googled the problem and someone suggested 
sudo dpkg-reconfigure --phigh xserver-xorg
in safe mode
but it returns that xserver-xorg is not installed.

any ideas?

---

### Post by Anatashinu on 2010-01-11
I'm not exactly sure whats going on, but my first thought woud be ```
sudo apt-get install xserver-xorg
```

---

### Post by tom.swartz07 on 2010-01-11
> **Anatashinu said:**
> I'm not exactly sure whats going on, but my first thought woud be ```
sudo apt-get install xserver-xorg
```

if that doesnt work, try booting to your recovery (grub should have it listed when you boot up your computer) and running xfix. Perhaps a config file got lost somewhere.

another possibility is to check your ubuntu-desktop

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by squall51489 on 2010-01-11
> **tom.swartz07 said:**
> if that doesnt work, try booting to your recovery (grub should have it listed when you boot up your computer) and running xfix. Perhaps a config file got lost somewhere.

another possibility is to check your ubuntu-desktop

```
sudo apt-get install --reinstall ubuntu-desktop
```

is 'xfix' a command by itself? I get command not found

as for
```
sudo apt-get install --reinstall ubuntu-desktop
```
it says it could not resolve 'ca.archive.ubuntu.com'
```
apt-get update
```
also says fails to resolve for all hosts

I assume I have to have an active internet connection, how is that achieved from recovery mode

---

### Post by MooPi on 2010-01-11
Did you have an active connection when you first installed Ubuntu. When I say active I mean either a wired connection or wireless configured while using the Live CD function ? If you didn't your instalation may have been incomplete.

---

### Post by squall51489 on 2010-01-11
> **MooPi said:**
> Did you have an active connection when you first installed Ubuntu. When I say active I mean either a wired connection or wireless configured while using the Live CD function ? If you didn't your instalation may have been incomplete.

I did have a connection when I installed at home, I am currently at school on their open WIFI network

---

### Post by sandyd on 2010-01-11
> **squall51489 said:**
> is 'xfix' a command by itself? I get command not found

as for
```
sudo apt-get install --reinstall ubuntu-desktop
```it says it could not resolve 'ca.archive.ubuntu.com'
```
apt-get update
```also says fails to resolve for all hosts

I assume I have to have an active internet connection, how is that achieved from recovery mode
when you get to the lines on your screen, can you press alt+f1, login, and type this?
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
as of (jaunty??) there doesn't need to be a xorg.conf - it will use default settings if no xorg.conf is found.

---

### Post by squall51489 on 2010-01-11
> **carlee said:**
> 
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```


this seemed to clear everything up, is there a reason that my xorg.conf file got messed up? it was working fine and then a reboot made it not work.

---

### Post by tom.swartz07 on 2010-01-11
> **squall51489 said:**
> this seemed to clear everything up, is there a reason that my xorg.conf file got messed up? it was working fine and then a reboot made it not work.

Did you install anything related to your video card?
I borked my system the first time i booted ubuntu because i installed ATI catalyst center and my card wasnt supported.

---

### Post by squall51489 on 2010-01-11
my laptop actually has two gfx processors, one is disabled by default. I ran a system update so maybe the driver for that was updated and the card was enabled.

Anyways, thanks for the help!

---

### Post by sandyd on 2010-01-11
> **squall51489 said:**
> my laptop actually has two gfx processors, one is disabled by default. I ran a system update so maybe the driver for that was updated and the card was enabled.

Anyways, thanks for the help!

You should now be able to renable the drivers.
a
side note.
after renabling, run
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
each time xorg screws up, run
```

sudo cp /etc/X11/xorg.conf.bak /etc/X11.xorg.conf
```
restart and your xorg will be normal ;)

---

