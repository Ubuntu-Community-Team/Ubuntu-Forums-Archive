---
title: "Xubuntu on dell x200"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by dandescendant on 2010-09-19
All was working well, then it stopped getting past the login I think its a graphics driver issue as some interesting visuals have been occurring and going into screen-saver necessitates a reboot. No idea how to find out though or what to do about it.  Subsequently I have now got an Ubuntu partition installed which I intend to use as I'm used to it as I run it on my main computer, and battery life for anything longer than about 20 minuets isn't an issue.    However theirs an un-finished essay on the xubuntu partition that I need. I can log in to a terminal session but I cant move my files onto the other partition as access is denied apparently. Also cant get the files I need back when in the ubuntu partition as like a fool I encrypted it. Any ideas or shall I just start typing the essay up again?

---

### Post by cariboo on 2010-09-19
use sudo when trying to copy/move files form a partition you don't have access to eg:

```
mv /home/user/somefile /media/disk/somefile
```

---

