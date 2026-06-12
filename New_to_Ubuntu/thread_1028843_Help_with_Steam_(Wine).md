---
title: "Help with Steam (Wine)"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by SilverPotato on 2009-01-02
I'm running Steam through Wine and for some reason the text is just ugly. My friends list is impossible to read, and on top of that I can't see messages I have sent/received with the chat thing. I wanted to know if there is a way to fix this.

Thanks!

---

### Post by retskrad on 2009-01-02
You know, wine isnt perfect. be glad that it even works lol. Nah man, some programs, the text is ust like that. An example is DVD Flick under wine.

---

### Post by SilverPotato on 2009-01-02
Guess I'm going to have to wait for an update or something. Thanks anyway :)

---

### Post by hambone79 on 2009-01-02
It is most likely a font issue (I had a similar issue with Steam). Make sure you have the msttcorefonts package installed:

```
sudo apt-get install msttcorefonts
```

---

