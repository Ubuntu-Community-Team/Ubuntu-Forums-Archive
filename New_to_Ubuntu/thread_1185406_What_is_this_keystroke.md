---
title: "What is this keystroke"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2009-06-12
I am trying to configure OpenBox but I don't know what my Fn+Left Arrow key should be labled as in the config file. Is there a program I can run to tell me what the computer will interpret that as?

---

### Post by ashmew2 on 2009-06-13
I think you should give xev a try. Itll tell you all sorts of things like keycode etc about the key you press. Just open a terminal and do :

```
xev
```

A small Window will open. Now press any key you want to and there will be information output about that key in the terminal!

---

