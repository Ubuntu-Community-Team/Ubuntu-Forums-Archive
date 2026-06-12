---
title: "LaTeX error - &quot;float.sty not found&quot;"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Pirkiz on 2011-01-26
Hi!
I just updated to ubuntu 10.10, and everything seems to be working fine so far except LaTeX. I installed it by typing the following, as the Terminal recommended me to do:
```
sudo apt-get install texlive-latex-base
```It installed everything without complaints, but when I try to compile any TeX-file I get the following:

```
! LaTeX Error: File `float.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

Enter file name:
```How do I fix this?

Thanks in advance!

---

### Post by Pirkiz on 2011-01-28
Never mind, I fixed it. Turns out I was trying to use a package I didn't have :oops:

---

### Post by Lexje on 2011-06-06
> **Pirkiz said:**
> Never mind, I fixed it. Turns out I was trying to use a package I didn't have :oops:

Hi Pirkiz,

I'm in the same boat, but I've no LateX experience whatsoever.
(trying to use it with org / emacs)
What package did you install to solve this issue?

Thx,

Erwin

---

### Post by artella on 2011-06-26
@Lexje :

Download float.ins from : 

[http://www.ctan.org/tex-archive/macros/latex/contrib/float](http://www.ctan.org/tex-archive/macros/latex/contrib/float)

Login as root & type (in the directory where file is downloaded) : 

sudo latex float.ins

This will create the float.sty file. Then proceed with the instructions given at : 

[http://haifenghep.blogspot.com/2010/07/install-latex-style-file-on-linux.html](http://haifenghep.blogspot.com/2010/07/install-latex-style-file-on-linux.html)

Namely : 

a)cp float.sty /usr/share/texmf/tex/latex
b)texhash

The work is done. Alternatively download texlive-latex-extra through Synaptic Package Manager (total download is large).

[EDIT : I am assuming you have already installed : texliv-latex-base]

---

### Post by frisket on 2011-07-02
The real solution is to install texlive-full, then you won't get these errors (except for very new packages -- for some reason Ubuntu's LaTeX is over a year behind the TeX Live release).

---

