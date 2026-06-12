---
title: "network .exe file??"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by mltom on 2009-01-27
I'm trying to execute a Win .exe file so as to try & implement a pc to pc network via a dsl modem.. 
But I can see the .exe on the Xubuntu floppy but so far nothing I've tried will execute the file.
Any ideas all???????????????????????/

tks tom

---

### Post by bwang on 2009-01-27
You need to install wine to run Windows programs:

```
sudo apt-get install wine
```

---

### Post by snova on 2009-01-27
What kind of program is this?

Wine can run a lot of Windows programs, but if this is a network device driver, it won't help at all.

---

### Post by redseventyseven on 2009-01-27
Good news and bad news.

Bad news, you probably won't be able to run that .exe file. At least, even if you did manage to run it, it probably wouldn't do what it would if it was run in Windows.

Good news, there is probably a different (and better!) solution for implementing your pc to pc network. If you could start a new topic describing what you'd like to achieve, then we might be able to help you solve your problem!

---

### Post by lisati on 2009-01-27
> **mltom said:**
> I'm trying to execute a Win .exe file so as to try & implement a pc to pc network via a dsl modem.. 
But I can see the .exe on the Xubuntu floppy but so far nothing I've tried will execute the file.
Any ideas all???????????????????????/

tks tom

Windows programs usually don't work without help (see [here]("http://ubuntuforums.org/showpost.php?p=6628376&postcount=2") and [here]("https://help.ubuntu.com/community/Wine")) - it might be more useful to reseach something like Samba to get your PCs talking to each other (see [here]("https://help.ubuntu.com/community/SettingUpSamba"))

---

