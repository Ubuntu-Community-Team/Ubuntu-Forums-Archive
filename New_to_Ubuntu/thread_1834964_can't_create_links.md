---
title: "can't create links"
date: 2011-08-28
forum: New to Ubuntu
---

### Post by canam101 on 2011-08-28
With ubuntu, I can drag a file or folder someplace else, hold down the alt key and get a menu asking if I want to move, copy, or link. I choose what I want and take my finger off the mouse, and it does what I wanted.

But when I press the alt key in Lubuntu and take my finger off the mouse, it moves the file. I tried using the ctrl key and that copies it.

Any ideas?

Thanks

---

### Post by wojox on 2011-08-28
If your talking about doing this in the file managers, Ubuntu uses Nautilus and Lubuntu uses PCManFM

---

### Post by canam101 on 2011-08-28
> **wojox said:**
> If your talking about doing this in the file managers, Ubuntu uses Nautilus and Lubuntu uses PCManFMI noticed that but do not see anything describing how to create a link.

---

### Post by kartabosh on 2011-08-28
> **canam101 said:**
> I noticed that but do not see anything describing how to create a link.

respond like that and you'll probably not going to get any help

one way of creating links is via command line

```
ln -s /path/to/real/file /path/to/link (~ not allowed)
```

another way would be, like wojox said, to install an alternate file manager and run that instead of pcmanfm

my favorite is thunar, in my opinion it's much better than pcmanfm 

```
sudo aptitude install thunar
```

---

### Post by N00b-un-2 on 2011-08-28
typically I just do symlinks with the terminal
```
sudo ln -s /path/to/file /path/to/link

```

I use it frequently for making command shortcuts, eg;
```
sudo ln -s /home/ryan/Android/platform-tools/adb /usr/bin/adb
sudo chmod o+x /usr/bin/adb

```

---

### Post by canam101 on 2011-08-28
> **kartabosh said:**
> respond like that and you'll probably not going to get any helpWhat response would you expect? wojox did not say that pcmanfm could not create links - he seemed to me to be saying nothing.

> 
one way of creating links is via command line

```
ln -s /path/to/real/file /path/to/link (~ not allowed)
``` Thanks.

> 
another way would be, like wojox said, to install an alternate file manager and run that instead of pcmanfmToo bad he did not say that.

> 
my favorite is thunar, in my opinion it's much better than pcmanfm 

```
sudo aptitude install thunar
```Thank you again.

---

### Post by wojox on 2011-08-28
> **canam101 said:**
> I noticed that but do not see anything describing how to create a link.

Sorry, I figured if I brought to your attention you had been comparing two different file managers a light bulb would go off. :P

---

