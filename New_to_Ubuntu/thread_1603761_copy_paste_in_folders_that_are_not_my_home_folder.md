---
title: "copy paste in folders that are not my home folder"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-10-23
Hello,

I am quite new to Ubuntu. I like to install a LeTeX package, that has not been automatically loaded. Therefore I want to copy paste a the package to a directory, where LaTeX can install it. I think the folder /usr/share/texmf/tex is right for that. Now, if I want to copy paste the package to that directory, it simply does not work. I think I do not have the user rights for that. Does someone know, how to change that?

---

### Post by planet81 on 2010-10-23
you must work in root mode,

in terminal just typing:

gksudo nautilus

and nautilus will be open in root mode, so copy paste what you want :)

---

### Post by Peter.Paul on 2010-10-23
ok. thx. That worked. I really have some trouble reading the manual for the package ngerman. And I do not really know what to do or what is meant to contribute to my general knowledge of LaTeX. 

In the manual it says that the file gnhyph01.tex is needed and that the lines 
```

german   ghyph31.tex
ngerman  gnhyph01.tex

```

Need to be in the configuration file language.dat. Where can I find this file? I just gooled and found at [CTAN ]("http://www.ctan.org/tex-archive/language/hyphenation/dehyph/")that ghyph31 and gnhyph01.tex are out of date. Shall I then write ```

ngerman dehyphn.tex

```

---

