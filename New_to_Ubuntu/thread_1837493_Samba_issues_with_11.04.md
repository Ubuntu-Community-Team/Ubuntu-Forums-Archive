---
title: "Samba issues with 11.04?"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by jedispork on 2011-09-01
I've been trying to share a folder in my home directory with 11.04. I installed the samba gui. I tried allowing guest access and creating user accounts but the only thing that would happen is I could browse the files from a win 7 machine but not access them. I've been googling for guides and others seem to be having the same issue with 11.04. 

Previously when I had ubuntu installed I was able to get samba working fine. Obviously I'm a beginner but out of the box folder sharing needs a lot of work. I'm thinking of running ubuntu in a virtual box on windows that way I can have my shared folder work consistently and much easier to access games.

---

### Post by snip3r8 on 2011-09-01
Have you made sure everything looks like the attached screen-shot?

---

### Post by jedispork on 2011-09-02
Yes. I will post my samba config when I'm back home. Thanks!

---

### Post by Morbius1 on 2011-09-02
> I installed the samba guiLet's all hope and pray it's not gadmin-samba.

There's 2 completely different methods of creating a samba share. They  place share definitions in 2 completely different locations. And it appears from this post you are using both methods so you might want to post the output of both commands:
```
testparm -s
``````
net usershare info --long
```

---

### Post by jedispork on 2011-09-02
I created a new txt file as a test and it worked fine. However if I drag a file from my ntfs partition to the shared folder in my home directory I could not access it from the windows pc. I went to the properties of the file and assigned read and right access for group and other and now it seems to work.

So does this mean it was a issue with permissions? Will I have to do this with every file I copy from the ntfs drive? I would like to use a ntfs folder as my main share and I seem to remember before that I had to add uid 1000 in the samba config file somewhere. Now that browsers have bookmark syncing dual booting should be much easier for me.


thanks for the help! I can still run those commands and post results if you need them.

---

### Post by jedispork on 2011-09-09
This works

[http://ubuntuforums.org/showthread.php?t=1536630&page=1](http://ubuntuforums.org/showthread.php?t=1536630&page=1)

The only complaint now is that the pc can enter sleep mode while samba is in use.

---

### Post by audiomick on 2011-09-09
For anyone else still looking for a solution to Samba problems, this thread is very good

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

