---
title: "first boot fails, movie player vanishes"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Little Bit on 2009-07-21
Hi!

My Ubuntu has the hiccups, and sugar (sweet-talking it) isn't helping, lol. I have two little issues:

First boot sometimes fails, but a "hard restart" makes it finish. It runs fine once it boots and loads though.

And someone sent me a movie clip attached to an e-mail. I chose "Open With..." and selected the movie player. It seems to start loading in a new window like it should, but then it vanishes! The file is still there, but the movie player starts - then aborts and disappears.

Thanks for your help!

Love,
Amy

---

### Post by Little Bit on 2009-07-21
bump? hope that's okay...

Amy

---

### Post by radiocognition on 2009-07-21
Everything on your linux machine generates logs.  One easy way you can check what kind of errors you are having is opening the movie file with a command in the terminal.  Open a terminal (Applications > Accessories > Terminal) and type into the prompt

```

cd /path/to/movie/file
totem filename

```

where filename is the name of the movie file.  If there is any problem with the movie player, you will get some feedback through the terminal.  Similarly enabling a verbose boot (text at login rather than the Ubuntu load screen) can be useful in identifying boot issues.

---

### Post by Little Bit on 2009-07-21
Thank you! Maybe I can take it from there. This forum is wonderful and it's so sweet how you all help newbies!

Hugs,
Amy

---

