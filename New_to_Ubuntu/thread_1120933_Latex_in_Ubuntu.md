---
title: "Latex in Ubuntu?"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by cfogelberg on 2009-04-09
Hello,

A dumb question, but how do I install latex in ubuntu? All the threads and posts I see seem to refer to texlive, but when I install that (I also installed latex209 hoping it would be latex209e) I don't get a latex in my path, just latex209.

Thanks for your help :)
Christo

---

### Post by cfogelberg on 2009-04-09
Correction:
I hadn't installed texlive-base, I had installed latex209-bin, latex209-base and latex-beamer. Installing texlive-base now though doesn't give me the binaries and there are a million and one texlive packages so I'm not sure the best way to proceed... I want to be able to do latex, bibtex, and so long as it has the basic styles (article, report) I have the styles and classes for the other things I want to do :)

Thanks again,
Christo

---

### Post by unutbu on 2009-04-09
When you installed texlive, it should also have installed the texlive-latex-base package. The texlive-latex-base package provides /usr/bin/latex.

```

% which latex
/usr/bin/latex
% dpkg -S /usr/bin/latex   # Find which package provides /usr/bin/latex. 
**texlive-latex-base**: /usr/bin/latex
% apt-cache show texlive
...
Depends: texlive-fonts-recommended (>= 2007-11), texlive-latex-recommended (>= 2007-11),** texlive-latex-base** (>= 2007-11)
...
```

I think the easiest thing to do is install the textlive metapackage. This will draw in all the needed packages.
From the "apt-cache show texlive" description:
```

 This metapackage provides a decent selection of the TeX Live packages
 which should suffice for the most common tasks.
```

So I would recommend removing those latex209-bin, latex209-base packages and running
```

sudo apt-get install texlive
```

---

### Post by cfogelberg on 2009-04-09
I take that back - you're right it does appear to be installed, and exactly where you suggest. Not sure how I missed it earlier, but thank you for your help :)

Christo

---

### Post by leandromartinez98 on 2009-04-09
I use:

sudo apt-get install latex-beamer

the "beamer" is the latex style for building presentations. Since
it depends on everything latex is built on, this, for satisfying
dependencies, installs everything I ever need from a latex instalation.

---

### Post by acimmarusti on 2009-04-09
You can just get all the texlive packages supported by canonical. That's all you need, unless you are doing something very very specific (look them up with synaptics).

Or the easy way is to install texmaker (a really nice tex/latex editor). By getting this program you get all the other things to need for latex.

```

sudo apt-get install texmaker

```

---

### Post by mitsoulis on 2009-05-01
Please could you tell me which is the packet for graphic environment of texlive ?

I have already installed it from terminal  but I have no idea how to "run" it ...

---

### Post by waspbr on 2009-05-01
When I used to work with Latex, and I hope I never have to work with that thing again, I used an editor called winefish.


```
sudo apt-get install winefish
```

 It made the experience a little less painful.

---

### Post by llamabr on 2009-05-01
> **waspbr said:**
> When I used to work with Latex, and I hope I never have to work with that thing again, I used an editor called winefish.


```
sudo apt-get install winefish
```

 It made the experience a little less painful.

Sorry you had a painful experience.  I use LaTeX for everything I write.  I edit in nano, which does syntax highlighting for tex.  For gui, I occasionally use kile, which is a kde app.

---

### Post by Stefan_K on 2009-05-03
Hi mitsoulis,

> **mitsoulis said:**
> Please could you tell me which is the packet for graphic environment of texlive ?


I'm working with [Kile]("http://kile.sourceforge.net/"), you could install it by Synaptic or by:
```
sudo apt-get install kile
```
It will install some KDE libs. If you don't want that you could install [Texmaker]("http://www.xm1math.net/texmaker/"), another good LaTeX editor, also by Synaptic or
```
sudo apt-get install texmaker
```
I'm preferring Kile.

Stefan

--
[TeXblog.net]("http://texblog.net")

---

