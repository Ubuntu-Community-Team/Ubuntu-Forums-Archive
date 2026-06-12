---
title: "How to use &quot;None&quot; Visual Effects from cmd line?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Physicist on 2009-04-28
Hi,

I need to disable Visual Effects from command line.

By Visual Effects I mean
  System>Preference>Appearence>Visual Effects>Extra

I have chosen "Extra" as the value for "Visual Effects" using GUI before. Now I need to use "None" but I have to do this from command line. How ?

The reason I have to do this from command line is that after I upgraded from 8.04 to 9.04, as soon as I start the OS, the screen freezes, mouse still respond, but nothing on the desktop respond to clicking.


Strangely, I can boot using the last version of the Linux kernel.

---

### Post by Temposs on 2009-04-28
hi Physicist

the command to do what you want is this:

```
metacity --replace
```

---

