---
title: "Missing Files"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by sylph on 2010-02-02
Hi everyone,

I'm pretty new to Ubuntu and although I'm still finding my way around, I have to say I really like it.

Today when I was trying to dig up an old assignment, I noticed that a couple directories and all of the files in them have disappeared. Since this is school work, I'm a little worried about this happening again at a more inconvenient time. 

Does anyone have any ideas how I can a) figure out what happened to my files b) if there is a way to recover them?

The data was on an internally mounted NTFS partition that's I use to share data between my windows and linux setups. I'm using Ubuntu 9.10 64-bit.

Thanks for your help/advice!

---

### Post by Leppie on 2010-02-02
hi and welcome to the community,

if the files/folders were on a ntfs partition, you could try with some windows apps for file recovery.
in ubuntu there is testdisk, which comes with photorec an app that can recover files from disk. you will have to enable the "universe" repository in order to be able to install testdisk: go to System>Administration>Software Sources and make sure the universe repo is checked.
then issue these commands in a terminal to install testdisk:
```
sudo apt-get update
sudo apt-get install testdisk
```

to run photorec:
```
sudo photorec
```

---

### Post by sylph on 2010-02-02
Thanks a lot Leppie. I'll give those a try. Do you (or anyone else) have any ideas to figure out what could have caused it? I am almost 100% certain I did not delete those files accidentally or otherwise :(

---

### Post by Leppie on 2010-02-02
> **sylph said:**
> Thanks a lot Leppie. I'll give those a try. Do you (or anyone else) have any ideas to figure out what could have caused it? I am almost 100% certain I did not delete those files accidentally or otherwise :(
windows systems are always a bit of a mystery... not shutting down properly is usually one of the first things that comes to mind with data loss... but it could've been a lot of things really

---

