---
title: "Stuck on this sed command, help appreciated."
date: 2009-04-05
forum: New to Ubuntu
---

### Post by hovzio on 2009-04-05
hi, I'm experimenting a little with sed and some regex basics and like the title states, I' stuck :)  

What I have is the html source of this page:


[http://aruljohn.com/ua/](http://aruljohn.com/ua/)


Heres a snippet of it after downlowded with curl:

```

Wget/1.9+cvs-stable (Red Hat modified)</li><li>Windows NT 5.0; en-US; rv:1.8.1.12) Gecko/20080201 SeaMonkey/1.1.8</li><li>WordPress/2.3.3</li><li>WordPress/MU</li><li>www.SecuProxy.com - Free Web Proxy for Secure Browsing</li><li>WWWOFFLE/2.9a</li><li>yacybot (i386 Linux 2.6.22-14-386; java 1.6.0_03; Europe/en) http://yacy.net/bot.html</li><li>Yeti/0.01 (nhn/1noon, yetibot@naver.com, check robots.txt daily and follow it)</li><li>Yeti/1.0 

```

What I am trying to do is seperate each line; I basically want to replace <li> with a newline or at least append it with a newline.  I put curls output in file, sed_prac, here are a few of my attemts.
```

sed '/<li>/a \ ' sed_prac

sed '/.*<li>/a \ ' sed_prac

sed '/<li>/ s__\ _g' sed_prac

sed '/.*<li>/ s__\
 _g' sed_prac


```

Well none of these work, I thought the "<>" characters needed to be escaped, this didn't help. I don't think this is a problem with the BRE's because I'm trying to use

```
grep --color '<li>' sed_prac
```

and grep correctly outputs the file highlighting all occurrences of <li> red. What am I doing wrong, is this "sed" specific? I've tried more than the above listed commands but they started getting a little to abstract to post here :-|  Any ideas, thanks hovzio   ;)

---

### Post by khelben1979 on 2009-04-05
Maybe you should try [Super Ced]("http://sed.sourceforge.net/grabbag/ssed/") instead?

They claim it's an enhanced version of Sed and from what I can see from the homepage, they also have tutorial documentation. Otherwise if you choose to stick with Sed, then [this page]("http://en.wikipedia.org/wiki/Sed") might give you something and you can also check the man page:

```
man sed
```

---

### Post by asmoore82 on 2009-04-05
```
sed 's/<td>/\n<td>/g' *<file.html>*
```

EDIT: just found this in the `sed` manpage same effect with less work:
```
sed 's/<td>/\n&/g' *<file.html>*
```

friendly info manual browsing with `yelp`:
```
yelp info:sed
```

---

### Post by hovzio on 2009-04-05
> **asmoore82 said:**
> ```
sed 's/<td>/\n<td>/g' *<file.html>*
```

EDIT: just found this in the `sed` manpage same effect with less work:
```
sed 's/<td>/\n&/g' *<file.html>*
```

friendly info manual browsing with `yelp`:
```
yelp info:sed
```

Cool, thank you very much, that did the trick. Yelp is awesome haven't heard of it before, thanks :)

---

