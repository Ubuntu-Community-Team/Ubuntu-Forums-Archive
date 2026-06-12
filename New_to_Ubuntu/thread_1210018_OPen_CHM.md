---
title: "OPen CHM"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by murryastika on 2009-07-10
Dear ...
 I was newbie in linux world, i so enchanted with jaunty performance and appearance but i going mad when i try to read my ebook or some programs that go normal in XP. Several of my CHM extended *e*book could open by CHMviewer but mostly not. Others document formatted  like pdb and DJVU made me tired to find the right one to open that documents.  
 I have heavy programs that goes well on XP, its need netframework before its installation. I think to use wine, but not yet try, i doubt. As student i most depend to that ebooks and programs. I couldn't do the tasks without it. Someday i think to buried jaunty but i wont. I've fallin love, and I remember the jaunty said Linux for human being, and I human being as well. Help me, thanks for your appreciate.

---

### Post by earthpigg on 2009-07-10
i have never used a CHM file, but one thing you may want to consider is that *linux is case sensitive*, and windows is not. renaming it from mybookname._CHM_ to mybookname._chm_ could do the trick - since windows is not case sensitive, it wont make a difference when you try reading them in windows again.

alternatively, there is a firefox addon that claims to read chm files:

[https://addons.mozilla.org/en-US/firefox/addon/3235](https://addons.mozilla.org/en-US/firefox/addon/3235)

as another alternative, several ubuntu applications claim to be able to read chm files:

applications -> add/remove programs -> search for 'chm'


several apps in add/remove also claim to be able to read djvu and pdb. again, linux sees filename.PDB as completely different than filename.pdb.

---

### Post by murryastika on 2009-07-11
thanks a lot, i'll try.

---

### Post by earthpigg on 2009-07-11
> **murryastika said:**
> thanks a lot, i'll try.

when i first got ubuntu, i racked my brain for quite a while figuring out why standard .jpeg pictures weren't loading...

.... well, they weren't standard .jpeg pictures, they where .JPEG files :P

---

### Post by Clorow on 2009-07-11
There's a program called chmsee, though I don't know if it's in Ubuntu's software repository, or if you'll have to add a PPA (mini-repository for a specific purpose).

Try this:
```
 sudo apt-get install chmsee
```

I don't know if it is there or not, though.

---

### Post by ikt on 2009-07-19
There are multiple applications for opening chm files,

Applications > Add/Remove Programs

[http://img217.imageshack.us/img217/5428/chm.png](http://img217.imageshack.us/img217/5428/chm.png)

---

### Post by kwacka on 2009-07-19
Also try archmage - it decompresses CHM to HTML

---

### Post by dilantha on 2010-11-20
```
sudo apt-get install xchm 
```Worked for me.

---

### Post by drpjkurian on 2010-12-14
Hi
Please go through my [blog]("http://ubuntucrack.blogspot.com/2010_07_11_archive.html")

---

