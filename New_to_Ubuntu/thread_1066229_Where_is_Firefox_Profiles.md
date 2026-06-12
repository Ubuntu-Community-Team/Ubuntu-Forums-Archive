---
title: "Where is Firefox Profiles?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-10
Hi all - did a search - results say home>user name>MozillaFF etc

Problem - the home>user folder on my new install of 8.10 only has some default folders for Templates, Examples and Desktop and such.

I am running the stock default user FF out of the Ubuntu box. I want to overwrite Profiles with a copy of my existing (other OS) Profiles folder.

Any ideas?

Thanks

dmc

---

### Post by lisati on 2009-02-10
There may be some hidden files. On my machine, if I go to Places->Home folder, and then enable view->"show hidden files" it reveals a .mozilla folder where Firefox stores its settings.

---

### Post by ww711 on 2009-02-10
in terminal

```
ls .mozilla/firefox
```

the Firefox profiles are there.

---

### Post by deadmanschest on 2009-02-10
> **lisati said:**
> There may be some hidden files. On my machine, if I go to Places->Home folder, and then enable view->"show hidden files" it reveals a .mozilla folder where Firefox stores its settings.

Thanks lisati - Hidden files did the trick.

Cheers

dmc

---

### Post by deadmanschest on 2009-02-10
> **ww711 said:**
> in terminal

```
ls .mozilla/firefox
```

the Firefox profiles are there.

Hi ww711 - gotta admit, I'm more of a file explorer gui guy than a command line guy. I found the default priofile folder as above, should be good to go.

But thanks for the 'ls' command. Problem is it just returned the name of the default folder, no tip as to its location. Maybe a search tool, but when I tried to use the file search tool for Mozilla it gave me nothing. That could be upper case, don't know.

Thanks

dmc

---

