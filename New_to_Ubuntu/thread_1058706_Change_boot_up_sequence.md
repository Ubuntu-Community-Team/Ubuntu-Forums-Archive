---
title: "Change boot up sequence"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by longtom on 2009-02-03
Hi,

I have a dual boot system on my PC with WinXP and Ubuntu.  At present Ubuntu gets started as default OS.
Since I am not the only one working on this, I'd like WinXP to be the default OS and Ubuntu the additional one.

There is a suggestion (sudo command) how to do this in the Ubuntu manual, but that one didn't work for me.  "Directory doesn't exist" or something in that vein.

Could somebody point me in the correct direction please?

Greetings

longtom

---

### Post by Zillion on 2009-02-03
You need to change the boot order in the Grub.

```
sudo nano /boot/grub/menu.lst
```

or instead of nano your favourite editor

---

### Post by yeats on 2009-02-03
You can go to the Synaptic Package Manager and search for startupmanager, which is a graphical interface for setting up your GRUB menu.  It will allow you to pick which OS you would like to be your default.

---

### Post by Partyboi2 on 2009-02-03
You can change the "Default" setting in your grub menu.lst, you can do this by following
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

If you need help still post your grub menu.lst
```
cat /boot/grub/menu.lst
```

---

### Post by longtom on 2009-02-03
Wow - that was fast....

Thank you, that'll do!:)

longtom

---

### Post by longtom on 2009-02-03
Just let you know, got it going.

Thank you very much

longtom

---

