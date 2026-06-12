---
title: "LaTeX TDS Packages"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by urban48 on 2008-12-29
I am writing a paper that requires a particular LaTeX style package which is bundled in a *.tds directory (it is called achemso.tds). This directory contains all the style packages, documentation, bibtex styles, etc. I placed this directory in the /usr/share/texmf-texlive directory, ran texhash, but latex was unable to find the files. I moved it to the /usr/share/texmf-texlive/tex directory, ran texhash, and now latex finds the files. However, bibtex does not. I just made a copy of the *.tds directory and placed it in /usr/share/texmf-texlive/bibtex/bst, but this annoys me because the benefit of the *.tds directory is to only have it in one place.

Does anyone know where the *.tds directories are supposed to be stored or have any information on why only the latex portion is working?

---

