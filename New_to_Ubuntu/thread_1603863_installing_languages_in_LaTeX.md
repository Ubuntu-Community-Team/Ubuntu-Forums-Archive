---
title: "installing languages in LaTeX"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Peter.Paul on 2010-10-23
Hello,
I am trying to install another language in LaTeX because the hyphenation does not work for German. I tried to follow the instruction of the ngerman manual and the instructions of this website [http://www.tex.ac.uk/cgi-bin/texfaq2html?label=newlang](http://www.tex.ac.uk/cgi-bin/texfaq2html?label=newlang)
both without success. 

I think I created the folder "german" at he right location, which is /usr/share/texmf-texlive/tex/generic but thenI do not know what to do. The manual says to open the babel language.dat file and edit it with the line "ngerman gnhyph01.tex"
. I do not know where to find this file. (And CTAN says that the file gnhyph01 is out of date anyway. ) Does someone know, how to precede?

---

### Post by NESFreak on 2010-10-23
How did you install latex? What latexdistribution are you using?

In the repositories there is a package called texlive. That should provide you a basic latex environment. The package texlive-lang-german should provide you all the german stuff. You could also choose to simply install texlive-full, which should provide you with everything you'd might possibly ever need.

Also what arguments did you provide to babel? ```
\usepackage[germanb]{babel}
``` should work.

---

