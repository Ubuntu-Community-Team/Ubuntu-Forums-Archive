---
title: "wipe or format hard-drive"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Papa-san on 2009-01-14
This laptop, (a Dell Inspiron 1525 ) as well as the other two of them I bought, are JUNK.
I have to send this one back, as I have had way too many problems with it. 
(Motherboard replaced twice, media bar once, front cover once, hinges twice, LCD screen once...) And now the hard-drive is going on it. (This doesn't even consider the fact that this thing (as well as the other two) shocks us through the chassis and earphones, still) {Nice, solid static (?) discharge through the ears is something that really gets your attention!}

Anyways, I need to completely wipe the contents of the damaged hard-drive before I send it back. How would I go about doing this? I have some pretty sensitive financial information on it, and I am pretty sure it is recoverable at this point. How do I make it go away for certain?

Please let me know if there is a program and/or a process to make this happen. 
As I am not really all that computer savvy, I'll need some step-by-step instructions.
Thanks in advance!

---

### Post by iaculallad on 2009-01-14
Boot from your Ubuntu LiveCD and issue the command below:

```
sudo shred -n2 -v /dev/xxx
```

Where xxx is your drive.i.e: sda, sdb....

---

### Post by jpkotta on 2009-01-14
Boot from a Live CD, and install shred if it isn't on the CD image already.

```
sudo aptitude install shred
```

Then assuming your HD is /dev/sda, 
```
sudo shred /dev/sda
```

---

### Post by hyper_ch on 2009-01-14
don't use shred, rather use DBAN

---

### Post by Rhubarb on 2009-01-14
> **hyper_ch said:**
> don't use shred, rather use DBAN
[http://www.dban.org/](http://www.dban.org/)

There may be a good tool you can use in the **secure-delete** package from the ubuntu repositories as well.

---

