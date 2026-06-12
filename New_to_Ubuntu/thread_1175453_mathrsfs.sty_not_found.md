---
title: "mathrsfs.sty not found"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2009-06-01
I am using ubuntu hardy version, but I am unable to use mathrsfs.sty in latex. I have searched in ubuntu package search, but in vain. Can anyone help me out?

---

### Post by sauravbhaumik on 2009-06-01
I think I got it ... it is in texlive-latex-recommended
anyway, thanks

---

### Post by C. M .Hughes on 2009-06-10
I know this is an old post, but just thought I'd write anyway. 

You can always search

[http://ctan.org/](http://ctan.org/)

for your sty file, then put it into an appropriate folder in

/usr/share/texmf-texlive/tex/latex

and then run

sudo mktexlsr

---

### Post by sauravbhaumik on 2009-06-12
> **C. M .Hughes said:**
> 
You can always search

[http://ctan.org/](http://ctan.org/)

for your sty file, then put it into an appropriate folder in

/usr/share/texmf-texlive/tex/latex

and then run

sudo mktexlsr

Thanks! But how can I guess a priori the name of the folder where the .sty file is to be pasted? Please explain in detail.

I have searched out that the folder in which mathrsfs.sty is found is .../latex/jknapltx - but where I find the mathrsfs file is in [this page]("http://tug.ctan.org/cgi-bin/ctanPackageInformation.py?id=mathrsfs"), where there is no mention of the name of the folder it is to be pasted in.

---

### Post by unutbu on 2009-06-12
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Go to the second search form, entitiled "Search the contents of packages".

Type in "mathrsfs", and check the third radiobutton -- the one entitled "packages that contain files whose names contain the keyword".

Click the search button and you will be sent to this page:
[http://packages.ubuntu.com/search?searchon=contents&keywords=mathrsfs&mode=filename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=mathrsfs&mode=filename&suite=jaunty&arch=any)

This shows you that you can install the mathrsfs.sty file by installing the texlive-latex-recommended package.

---

### Post by C. M .Hughes on 2009-06-12
[QUOTE=sauravbhaumik;7444487]Thanks! But how can I guess a priori the name of the folder where the .sty file is to be pasted? Please explain in detail.

The beautiful thing is that it doesn't matter what folder you name it as, provided that it is in a directory where LaTeX knows to look in (cd /usr/share/texmf-texlive/tex/latex)

If I were doing it, I would 

1. cd /usr/share/texmf-texlive/tex/latex

2. mkdir mathrsfs   (you might need to do this as sudo)

3. Now put mathrsfs.sty in this directory

4. mktexlsr    (this tells LaTeX to update its search paths)

---

### Post by glennric on 2009-06-12
One nice way to find if a file is in a package in the repositories, what package it is, and where the file is installed, is to use apt-file.
Install the apt-file package to use it, and then run 
```
sudo apt-file update
```
to update its package information (much like with apt-get).
Then to find the file mathrsfs.sty type
```
apt-file search mathrsfts
```
In this case it returns
```
texlive-latex-recommended: /usr/share/texmf-texlive/tex/latex/jknapltx/mathrsfs.sty
```

---

