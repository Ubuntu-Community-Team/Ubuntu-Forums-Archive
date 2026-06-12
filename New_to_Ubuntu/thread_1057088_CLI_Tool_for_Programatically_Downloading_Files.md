---
title: "CLI Tool for Programatically Downloading Files"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by oxsyn on 2009-02-01
Anyone know of a CLI tool that i can feed a URL and it will download all files that are linked on that page?

---

### Post by handydan918 on 2009-02-01
> **F4RR4R said:**
> Anyone know of a CLI tool that i can feed a URL and it will download all files that are linked on that page?
It looks like wget is capable of this if I understand you correctly. See man wget.

---

### Post by jimmy the saint on 2009-02-01
Just to clarify, that would mean open the terminal and type in
```
man wget
```

here is a good lifehacker tutorial, the first section has to do with what I think you are trying to do
[http://lifehacker.com/software/downloads/geek-to-live-mastering-wget-161202.php](http://lifehacker.com/software/downloads/geek-to-live-mastering-wget-161202.php)

heres another one that deals with the basics and has lots of examples
[http://linuxtuts.blogspot.com/2008/03/tutorials-on-wget.html](http://linuxtuts.blogspot.com/2008/03/tutorials-on-wget.html)

---

### Post by oxsyn on 2009-02-01
That's perfect.

wget -r --level=1 [http://futuretg.com/FTHumanEvolutionCourse/FTLearningKits/Linux%20and%20UNIX/](http://futuretg.com/FTHumanEvolutionCourse/FTLearningKits/Linux%20and%20UNIX/)

:)

---

