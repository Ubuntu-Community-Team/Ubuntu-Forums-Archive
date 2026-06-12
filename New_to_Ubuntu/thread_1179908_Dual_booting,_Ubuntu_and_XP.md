---
title: "Dual booting, Ubuntu and XP"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by amilojohnson on 2009-06-06
Hi all, Is it possible to change the default boot from Ubuntu to XP when starting up?

Doug...

---

### Post by demon_hunter on 2009-06-06
depends what pc you have

---

### Post by amilojohnson on 2009-06-06
The computer is a bogg standard laptop running windows XP.

Doug

---

### Post by Idefix82 on 2009-06-06
Can you post the output from
```
cat /boot/grub/menu.lst
```

---

### Post by gn2 on 2009-06-06
> **amilojohnson said:**
> Hi all, Is it possible to change the default boot from Ubuntu to XP when starting up?

Doug...

Yes, it's a simple matter of editing your menu.lst file so that Xp is top in the list.

[Here's how]("http://members.iinet.net.au/~herman546/p15.html#menu.lst"), scroll down to "Changing the default (operating system booted by the timer)"

---

### Post by dougcumiskey123 on 2009-06-06
> **Idefix82 said:**
> Can you post the output from
```
cat /boot/grub/menu.lst
```

I entered the line above using the terminal and only got the error "file not found"???

Doug...

---

### Post by dougcumiskey123 on 2009-06-06
> **gn2 said:**
> Yes, it's a simple matter of editing your menu.lst file so that Xp is top in the list.

[Here's how]("http://members.iinet.net.au/~herman546/p15.html#menu.lst"), scroll down to "Changing the default (operating system booted by the timer)"

How do i do that?

Doug...

---

### Post by dougcumiskey123 on 2009-06-06
> **gn2 said:**
> Yes, it's a simple matter of editing your menu.lst file so that Xp is top in the list.

[Here's how]("http://members.iinet.net.au/~herman546/p15.html#menu.lst"), scroll down to "Changing the default (operating system booted by the timer)"

I just spotted the hypertext and had a look, sorry thats far too complicated for a beginner.

Doug...

---

### Post by presence1960 on 2009-06-06
install startupmanager. it is a GUI for boot functions and more. Open a terminal and run ```
sudo apt-get install startupmanager
``` or use Synaptic  to install startupmanager. Once installed you can open it by System > Administration > Startup-Manager or open a terminal and run ```
gksu startupmanager
```.

---

### Post by -kg- on 2009-06-06
If Presence hadn't beat me to it, that's exactly what I was going to suggest.  Startupmanager will configure quite a few things in GRUB and works quite nicely.

You can even configure GRUB to automatically start with the last OS booted.

---

### Post by Idefix82 on 2009-06-06
> **dougcumiskey123 said:**
> I entered the line above using the terminal and only got the error "file not found"???

Doug...

Please copy and paste the line. The first letter of the extension of the file is a lower case L, not a 1.

---

