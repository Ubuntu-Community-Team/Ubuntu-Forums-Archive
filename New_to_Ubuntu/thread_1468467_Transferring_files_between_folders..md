---
title: "Transferring files between folders."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by brawd on 2010-05-01
Hi

I want to transfer a whole load of my files from one folder to another.

The source folder is located ~/Fonts and has dozens of font files in it.

The destination folder is /usr/share/fonts/truetype/myfonts.

So I cd to the destination folder OK and then try and transfer all the files in one go using cp ~/Fonts/ ????. But the question is what do I put in to transfer all the files using one command please?

regards,

brawd.

PS. It's sad I know but in DOS I would have used *.* and I did try that but it didn't work.

b

---

### Post by Seal Daemon on 2010-05-01
```
cp ~/Fonts/* /usr/share/fonts/truetype/myfonts

```

** Depending on what you have there, you might want to populate it with -R ..

---

### Post by brawd on 2010-05-01
Thank you, thank you Seal, you are my new superhero.

Incidentally I came within an ace of getting it right.

brawd.

One last thing please, how do I mark the thread solved?

---

