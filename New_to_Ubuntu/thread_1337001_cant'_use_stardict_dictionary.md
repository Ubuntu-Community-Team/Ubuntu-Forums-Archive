---
title: "cant' use stardict dictionary"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by iRounak on 2009-11-25
I installed English-Hindi dictionary using 
```
sudo apt-get -f -y install dict-freedict-eng-hin
```

and it installed properly.

```
The following NEW packages will be installed:
  dict-freedict-eng-hin
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,302kB of archives.
After this operation, 1,606kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com karmic/universe dict-freedict-eng-hin 1.3-4ubuntu1 [1,302kB]
Fetched 1,302kB in 1min 5s (20.0kB/s)                                          
Selecting previously deselected package dict-freedict-eng-hin.
(Reading database ... 161280 files and directories currently installed.)
Unpacking dict-freedict-eng-hin (from .../dict-freedict-eng-hin_1.3-4ubuntu1_all.deb) ...
Setting up dict-freedict-eng-hin (1.3-4ubuntu1) ...

```
But I cannot find it anywhere in the preferences. Nor do I get the meaning in Hindi language when I type in some word. I only get the meaning in English and some chinese language which I am unable to disable.

---

### Post by iRounak on 2009-11-29
please help

---

### Post by ubudog on 2009-11-29
Open a terminal (Applications>Accessories>Terminal) and type```
man dict-freedict-eng-hin
``` If there is a man page on it, it will show up.  Take a look at the man page and see if it helps.

---

### Post by iRounak on 2009-11-29
No, there is no man page. Maybe I should try the stardict forum.

---

### Post by ubudog on 2009-11-29
> **iRounak said:**
> No, there is no man page. Maybe I should try the stardict forum.

Yeah, might work.

---

### Post by iRounak on 2009-11-29
Oh God!! Look how spammed the forum is: [http://www.stardict.org/forum/viewforum.php?f=5](http://www.stardict.org/forum/viewforum.php?f=5)
I cannot expect any help there.

---

### Post by ubudog on 2009-11-29
> **iRounak said:**
> Oh God!! Look how spammed the forum is: [http://www.stardict.org/forum/viewforum.php?f=5](http://www.stardict.org/forum/viewforum.php?f=5)
I cannot expect any help there.

Yeah, that has nothing to do with dictionaries.  Hmm.

---

### Post by iRounak on 2009-11-30
Does anyone want to recommend me any alternative offline dictionary ?

---

### Post by chis@ on 2009-12-07
[COLOR=Blue]No, there is no man page. Maybe I should try the stardict forum.[/COLOR]
[COLOR=Purple]Yeah, might work.[/COLOR]
[COLOR=Blue]Oh God!! Look how spammed the forum is[/COLOR]
[COLOR=Purple]Yeah, that has nothing to do with dictionaries.  Hmm.[/COLOR]:lolflag:
I'm laughing my a** out coz I went through the same thing and was almost giving up and resorting to use babylon with wine until I found goldendict, so try that out.

It works with Babylon (.bgl) dictionaries, StarDict (.ifo/.dict./.idx/.syn) dictionaries and ABBYY Lingvo .dsl dictionary files - [http://goldendict.berlios.de/dictionaries.php](http://goldendict.berlios.de/dictionaries.php)

Because of a bug in Ubuntu Software Center, Goldendict didn't show up when I searched for dictionary. Had I found goldendict before babiloo, qstardict n stardict, it would have saved me a lot of trouble and heartache ](*,)

Good luck to you :)

Install from Ubuntu Software Center, the search now works btw.

---

### Post by iRounak on 2009-12-07
thanks, i will try it out. ( Have you ever clicked on "wiki" in the goldendict link you gave me?)

---

