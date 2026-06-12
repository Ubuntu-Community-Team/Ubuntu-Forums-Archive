---
title: "How do I open a directory through the command line"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by RabbitWho on 2010-08-22
Hi!
What I want is /tmp
I can get there in the terminal by typing** cd /tmp** but what I want is to open that folder and view the files through the file manager, not through the terminal, not through "**ls**" 

You know what would be great? if i could type the exact address of where I wanted to go in a bar at the top of the file manager itself. But for some crazy reason best known to whoever designed it that's not an option. Is there a way to put an address bar there? 

Thanks in advance.

---

### Post by howefield on 2010-08-22
> **RabbitWho said:**
> Is there a way to put an address bar there? 

Press Ctrl + L to get the address bar in Nautilus.

The other option is to click on File System in the left pane, and double click in the tmp folder. But as I say, Ctrl + L should do what you want :)

---

### Post by neilms on 2010-08-22
I'm sure you can do it with any file browser like nautilus. You can also do it with firefox - clear the firefox address bar and type // to view your whole filesystem or any directory..

---

### Post by fooman on 2010-08-22
open file manager (nautilus)...in the toolbar,  click: go > location

bingo....type the address in the location bar.

---

### Post by RabbitWho on 2010-08-22
Ctrl + L did it. Thanks! :)

---

### Post by 0004tom on 2010-08-22
You can also do it in terminal with 

```
nautilus /tmp
```

which will open a nautilus window at the place.

---

