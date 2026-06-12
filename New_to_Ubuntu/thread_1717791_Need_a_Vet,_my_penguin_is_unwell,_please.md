---
title: "Need a Vet, my penguin is unwell, please"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by mikee55 on 2011-03-30
Hi, Ubuntu 10.10

I can boot to desktop, but, I only get wallpaper and intro tune, no Icons Cursor nothing. What have I done?

I had to unplug my HDD temporarily.

Mike

---

### Post by epicoder on 2011-03-30
Sounds to me like Nautilus isn't running when you log in, nor are the panels. I don't really know how you can fix that, and I have no clue what would keep the cursor from showing. Could you give us any more relevant info?

---

### Post by ubudog on 2011-03-30
Some more info would be nice.  You could try this after logging in:

```
killall nautilus
```

and immediately after that:

```
nautilus
```

PS: That goes in a terminal window.  (Applications>Accessories>Terminal)

---

### Post by mikee55 on 2011-03-30
Cant access a thing, it would be easier me thinks to re install. Its a SSD and only holds the OS. Just a case of reinstall all my apps.

Mike

---

### Post by ubudog on 2011-03-30
If you really wanted to, you could I suppose.  There may be someone else here who can help you more though.

---

### Post by Paqman on 2011-03-30
Try hitting Ctrl-Alt-F1 to get yourself to a command line.

---

### Post by doas777 on 2011-03-30
if killing and restarting nautilus from tty1 doesn't do it, you may want to rename your home directory and reboot. if that works, migrate your files into the new home.
hopefully this will work (may not be able to run while you are logged in):
```

sudo mv ~ /home/backup.20110330.bak
sudo reboot
```

---

