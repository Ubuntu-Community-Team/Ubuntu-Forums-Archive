---
title: "What are the default settings for .conkyrc?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by anthony62490 on 2009-05-16
I just installed Conky a few hours ago. The first time I opened it, it ran just fine. I decided to get straight to work on modifying it. I found a template that was close to what I wanted and plugged it into .conkyrc. Then I decided that I would rather work from the default settings, so I deleted all the text in the file. I ran "killall conky" and started it back up again. Now, I am getting a message:
```
Conky: missing text block in configuration; exiting

```

My guess is that this means I deleted ALL settings. Anyone know how I can get the default settings back?

---

### Post by egalvan on 2009-05-16
I would normally give a more detailed

"here it is"

answer,

 but these two websites taught me so much about conky,
that I encourage you to check them out...



[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

[http://conky.sourceforge.net/documentation.html](http://conky.sourceforge.net/documentation.html)

---

### Post by m_duck on 2009-05-16
+1 for reading those links. The thread in my sig is also useful for a whole load of conky stuff. For your specific problem, it looks like you still have your file in ~/.conkyrc so it is being read by conky, but there is nothing in it, hence the error. I think the default config file is in /etc/conky/conky.conf so if you want to begin with the default one, copy that to your home folder then start configuring!
```
cp /etc/conky/conky.conf ~/.conkyrc
```

---

