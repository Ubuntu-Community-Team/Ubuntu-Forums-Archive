---
title: "[SOLVED] Lost display driver, boots to command line"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by iminhell on 2008-12-28
How do I get it to work again?
I tried booting from the live cd and re-installing the driver, did nothing. I have no clue how to work from the command line. Nothing in BIOS changed and no new parts where added, the driver just went missing, I don't get it.
It was the driver #173 for Nvidia I was using.
I don't wish to do a fresh install because there are files I wish not to loose.

Help?

---

### Post by taurus on 2008-12-28
What happens when you run these commands from a prompt?

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by mapes12 on 2008-12-28
And you could try ```
sudo apt-get install ubuntu-desktop
```> I don't wish to do a fresh install because there are files I wish not to loose.You don't have to lose anything provided you keep a copy of /home somewhere. This contains all your files, personal settings, firefox bookmarks and the like. To move it to another partition (that's if you need to do a fresh install to get things working) then have a look at this HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by iminhell on 2008-12-28
The first command did not work.

The second line went through and did something. I'm back at the command line now.
What next?  Restart?

---

### Post by mapes12 on 2008-12-28
> **iminhell said:**
> The first command did not work.

The second line went through and did something. I'm back at the command line now.
What next?  Restart?

A restart should help. Give it a go. More importantly, get /home backed up. Once /home is safe then getting your system working again should be easy.

---

### Post by iminhell on 2008-12-28
Restart and all seems well again, i'm posting from there at least :P

ty, marked as solved.

---

