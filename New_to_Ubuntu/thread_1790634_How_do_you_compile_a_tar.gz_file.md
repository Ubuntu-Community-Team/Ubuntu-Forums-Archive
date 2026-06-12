---
title: "How do you compile a tar.gz file?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-06-25
I just downloaded cheese-3.0.1.tar.gz from the Cheese website because I want to have the latest version. The Ubuntu Software Center Doesn't have the latest version, 3.0.1. cheese-3.0.1.tar.gz is in my Downloads folder in Home. I would really appreciate elementary steps on how to get this annoying file under control. :)

---

### Post by Neoncamouflage on 2011-06-25
Simply type tar -zxvf (filename).

---

### Post by doppel.ganger on 2011-06-25
Does that also install Cheese?

---

### Post by haqking on 2011-06-25
> **doppel.ganger said:**
> I just downloaded cheese-3.0.1.tar.gz from the Cheese website because I want to have the latest version. The Ubuntu Software Center Doesn't have the latest version, 3.0.1. cheese-3.0.1.tar.gz is in my Downloads folder in Home. I would really appreciate elementary steps on how to get this annoying file under control. :)

the tar.gz file is a compressed file (zipped up) which needs to be extracted first.

then in the extracted folder the source (binaries) should be located.

there should be a readme/install .txt file if the developers were nice which will give you more info but usually you would do a 
./configure
./make

but depends on the contents

read here first
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by smarmytime on 2011-06-25
There is almost certainly a README in that tarball.

---

### Post by Paqman on 2011-06-25
You can't run Cheese 3.0 on the current version of Gnome in Ubuntu. You need to be running Gnome 3, and Ubuntu only uses Gnome 2. The next version of Ubuntu will be based on Gnome 3 however, or you could install the [Gnome 3 PPA]("https://launchpad.net/~gnome3-team/+archive/gnome3") and grab Cheese from there (don't run any other upgrades and remove the PPA straight after). There's a high chance this could mash your system up completely though, so try it at your own risk.

I would advise just holding off for Oneiric, it'll be out in a few months.

---

### Post by Neoncamouflage on 2011-06-25
Also, for future notice, you can also go to Downloads under your Places menu, find the compressed file, right click and choose extract here.

---

### Post by haqking on 2011-06-25
> **Neoncamouflage said:**
> Simply type tar -zxvf (filename).

The OP question was "how to compile"

i am guessing he is not familiar with what a .tar.gz file is.

So he needs to extract by right clicking and choosing extract or indeed using the command at terminal

 tar -zxvf 

then he needs to compile contents if the contents need compiling

---

### Post by doppel.ganger on 2011-06-25
Thank you, paqman! I'll stick with the Ubuntu Software Center version until Oneiric!

---

