---
title: "WUBI Problem"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by mashman on 2009-03-22
Hi i'm new in ubuntu and I install ubuntu using the WUBI installing inside windows and I got also booted in Ubuntu when I restarted the computer, but my question if i really install ubuntu using WUBI why i got this message "No File System Define" and when I hit the ctrl+alt+backspace and he direct me to the ubuntu desktop and I still got "Install Icons" and I can't use the WUBI internet configuration. I would be happy if there's someone know's or even have the same problem as mine. A little great help will very grateful for me... Thanks...

---

### Post by diablo75 on 2009-03-22
I'm a little unclear about what you have going wrong (pardon me, but your English needs some improvement).  Could you give us a little more detail about what's going on?

---

### Post by kimikrishna on 2009-03-22
i talked with him..

he has installed wubi... 

but still when he boots in ubuntu , he   gets install icon on the desktop .. (he has no cd in drive)


then , he cant set his dialup internet connection.....

---

### Post by diablo75 on 2009-03-22
Someone other than me will have to take a shot at the issue with the Install Icon still appearing on the desktop.

As for getting his dialup modem setup...

He should run this command in a terminal window:

```
lspci
```

And copy/paste the output of that command back in here so we can see what kind of modem he has and go from there.

---

