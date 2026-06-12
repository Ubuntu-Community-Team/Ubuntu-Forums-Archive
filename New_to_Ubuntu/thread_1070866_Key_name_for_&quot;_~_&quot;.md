---
title: "Key name for &quot; ~ &quot;"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Noctiferis on 2009-02-15
Hi i'm trying to remap my Caps-Lock key to  ~ using [this]("http://www.terminally-incoherent.com/blog/2007/08/02/remapping-the-caps-lock-key/") guide. What do I have to input to achieve this? I don't know what this>>  ~  << is called in english so I can't even make an educated guess.


Any help would be appreciated:KS

---

### Post by ww711 on 2009-02-15
~ is the tilde key.

---

### Post by Bright_View on 2009-02-15
Don't know how to map the key, but it is called a tilda.  Good luck.

---

### Post by Bright_View on 2009-02-15
Sorry, I meant 'Tilde'.

---

### Post by Noctiferis on 2009-02-15
xmodmap:  /home/tbjh/.Xmodmap:2:  bad keysym name 'tilde' in keysym list
 this is what it gives me
anybody know a workaround for this?

---

### Post by ptg21 on 2011-09-21
It's asciitilde

use e.g.
>  keycode 66 = asciitilde
in your .Xmodmap and you should be fine.  Hope this helps.

---

### Post by sisco311 on 2011-09-21
Necrobumping.

Thread closed.

---

