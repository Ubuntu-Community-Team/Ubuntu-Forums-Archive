---
title: "KDenlive and Kino problems in Karmic(&amp;computer spontaneously shut down)."
date: 2009-11-14
forum: New to Ubuntu
---

### Post by annie227 on 2009-11-14
While I was typing the title my computer just switched off suddenly,never had that one.
At the time I was also importing a file(trying) into Kino,66mb mpeg (28 minutes and counting..),anyway,KDenlive kept closing,video would freeze and it repeatedly shut down before I could finish any task at all.That's why I tried importing a small mpeg into kino just to see if it performed any better.
The computer spontaneously switching off is a worry.It's booted up ok,fingers crossed.
Thanks

---

### Post by annie227 on 2009-11-15
Hello?????

---

### Post by laidback on 2009-11-16
I've had both Kdenlive and Kino "crash" on me whilst editing a video but Ubuntu remains OK. Normally I'll go into system monitor and kill the process. I've put it down to the clip itself as I have been able to repeat the problem with the same clip. It seems to happen when I cut a clip and then start to move one part around. But as I'm a novice at video I've concluded that it was me at fault. I know this doesn't answer your question but at least you know that similar things happen elsewhere.

---

### Post by ukripper on 2009-11-16
Can you post output of the following command:
```
tail -n 200 /var/log/Xorg.log.0 
```

---

### Post by bumanie on 2009-11-16
Never had an issue with kino on gnome, but have never been able to get kdenlive working on gnome for more than a couple of miutes before it crashes - stick with kino or try avidemux or possibly lives, which is a capable video editor, although does not like large files.

---

