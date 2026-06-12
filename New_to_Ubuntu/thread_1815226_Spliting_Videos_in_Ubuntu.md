---
title: "Spliting Videos in Ubuntu?"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by sillyboy on 2011-07-30
Is there a way to split videos into emailing size (less than 10 MB) with Ubuntu?

Thanks

---

### Post by Redblade20XX on 2011-07-30
You can always use the software center to find a program. FFMPEG, I think is a good CL program.

---

### Post by idoitprone on 2011-07-30
> **sillyboy said:**
> Is there a way to split videos into emailing size (less than 10 MB) with Ubuntu?

Thanks



first compress the file

> You should use the tar command at the command line like:
tar -cvjf <filename.tar.bz2> <files you want to be in the archive>

-c is Create
v is Verbose
j is bz2 file
f is filename

For instance if I have files called test1 and test2, and want the tar file to be called test.tar.bz2 I would do:

```
tar -cvjf test.tar.bz2 test1 test2
```At least, I'm fairly sure that's the command.  Type 'man tar' at the  command line to see detailed info about how to use the tar utility.   Good luck.curtosy of PrOeliuM

[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-make-a-tar-bz2-file-307637/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-make-a-tar-bz2-file-307637/)



then split it

```
man split
``````
split --bytes=10m <filename> <new filename>
```there is many options to choose from

[http://fedoraproject.org/wiki/User:Jmbabich/Split](http://fedoraproject.org/wiki/User:Jmbabich/Split)

---

### Post by sillyboy on 2011-07-30
> **idoitprone said:**
> first compress the file

curtosy of PrOeliuM

[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-make-a-tar-bz2-file-307637/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-make-a-tar-bz2-file-307637/)



then split it

```
man split
``````
split --bytes=10m <filename> <new filename>
```there is many options to choose from

[http://fedoraproject.org/wiki/User:Jmbabich/Split](http://fedoraproject.org/wiki/User:Jmbabich/Split)


Thanks will try.

---

