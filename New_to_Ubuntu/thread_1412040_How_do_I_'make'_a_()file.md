---
title: "How do I 'make' a (?)file"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by brawd on 2010-02-20
Hi all,

I'm trying to install a RTL-8185 pci wireless card in my pc. I'm using Hardy on an AMD64 bit motherboard.

So far lspci indicates the wireless, I have downloaded a tar file and extracted it. Now I have to 'make' the file. Where would I get directions to do this please?

I am a bit concerned because after I extracted the file it turned out to be a folder with several files inside so I hope the 'make' bit tells me which one to use. 

regards,

brawd.

---

### Post by J V on 2010-02-20
navigate to the folder (cd directory) then run make, easy as cli

---

### Post by nmaster on 2010-02-20
look at this:
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

### Post by nmaster on 2010-02-20
btw, you might want to try checking google.com/linux or
[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=]("http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=") (a custom google search of ubuntu related sites)

---

### Post by brawd on 2010-02-20
Thanks for your replies.
I did cd to directory and make.

Hey presto!

But it came back with Error 1 and Error 2.
Does that mean it didn't like something but gave me the 'made' files or does it mean it didn't give me the files?

And I went to the link and bookmarked it for the future.

brawd

---

### Post by lkraemer on 2010-02-21
Check to see if you have build-essential installed.
Just open Synaptic Package Manager and search for
build-essential.  Mark for install, then apply.
Then try the following commands again:
```

cd directoryoffiletocompile
make clean
make
sudo make install

```
You may also need ./configure as the first command, but the drivers I
have compiled didn't use the first command.

lk

---

