---
title: "LaTeX"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Blueball32 on 2009-01-16
Hey everyone, I'm in need of help here.

I startet using Ubuntu some days ago and now want to install everything required to use LaTeX as I did with windows (protex, Miktex, etc.).

I think I have already installed texlive-full (using apt-get) and an editor (texmaker), what do I have to do now, cause its not running...?

Thanks
Blue

---

### Post by northern lights on 2009-01-16
*texlive* is in any case required and the equivalent to MikTex under Windows.

For a LaTeX specific editor, check out *kile*.
Kile is a decent LaTex front-end and the closest to TexNicCenter or Protex.

However, I'd also consider using emacs with auctex, which is my preference. [Here]("http://www.terminally-incoherent.com/blog/2007/12/13/emacs-with-auctex-as-a-latex-ide/")'s a really good article on the topic. Against hardcore-emacs-user's habits, I'd enable Ctrl+C/X/V copy and pasting, though.

---

### Post by akimatsu123 on 2009-01-16
Why not install a latex writer? Application -> Add/Remove and just install your favorite latex editor. That will usually take care of all the packages you need.

---

### Post by Blueball32 on 2009-01-16
> **akimatsu123 said:**
> Why not install a latex writer? Application -> Add/Remove and just install your favorite latex editor. That will usually take care of all the packages you need.

Well I did install Texmaker with Application -> Add/Remove, but I can't build any file...do I need nothing more?:confused:

---

### Post by northern lights on 2009-01-16
> **akimatsu123 said:**
> Why not install a latex writer? Application -> Add/Remove*kile* is available from *gnome-app-install* ("Add/Remove..." dialog). It will take care of texlive dependencies also.

But seriously look at auctex with emacs. It is IMHO the most powerful combination. And, in addition, a cross-platform solution, as emacs exists for all *nix (including Mac OS) and Windows.

---

### Post by Tibuda on 2009-01-16
Open a terminal and type```
latex -v
```if it displays LaTeX version information, I guess you are missing a plugin to build your document.

About the editor, you can use gedit with (or without) LaTeX plugin.
[http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin)

---

### Post by mister_pink on 2009-01-16
By installing texmaker all the required latex things should have been pulled in. What error are you getting exactly? I'd check the texmaker configuration - I seem to remember the defaults being wrong. (Options, configure texmaker). For example the pdf viewer line should be "evince %.pdf"

---

### Post by Blueball32 on 2009-01-16
> **mister_pink said:**
> By installing texmaker all the required latex things should have been pulled in. What error are you getting exactly? I'd check the texmaker configuration - I seem to remember the defaults being wrong. (Options, configure texmaker). For example the pdf viewer line should be "evince %.pdf"

I tried kile, but I don't like it so I want to set up texmaker right. The error I get has something to do with the nonstopmode, so something must be wrong with the Latex command in Texmaker.

LaTex line in the configuration contains: latex -interaction=nonstopmode %.tex

is that correct...?

---

### Post by zika on 2009-01-16
+1 for Kile (used to be a Win-MikTeX-WinEdit user ... :))

---

### Post by Blueball32 on 2009-01-16
Aaargh, it doesn't work...I followed a step by step instruction and it just won't work...:(

Heres the log file I get:

> 
This is pdfTeXk, Version 3.141592-1.40.3 (Web2C 7.5.6) (format=latex 2009.1.16)  16 JAN 2009 21:10
entering extended mode
 %&-line parsing enabled.
**Test.tex

! Emergency stop.
<*> Test.tex
            
*** (job aborted, file error in nonstop mode)

 
Here is how much of TeX's memory you used:
 3 strings out of 94102
 111 string characters out of 1165833
 47703 words of memory out of 1500000
 3383 multiletter control sequences out of 10000+50000
 3640 words of font info for 14 fonts, out of 1200000 for 2000
 637 hyphenation exceptions out of 8191
 0i,0n,0p,1b,6s stack positions out of 5000i,500n,6000p,200000b,5000s
No pages of output.

Hope you can help

---

### Post by Dougie187 on 2009-01-16
Is this by hand? Why are you using pdflatex?

If this is not by hand, have you tried manually compiling a latex file and converting it to a pdf?

Probably the command you typed and the input file would be helpful.

---

### Post by Blueball32 on 2009-01-16
> **Dougie187 said:**
> Is this by hand? Why are you using pdflatex?

If this is not by hand, have you tried manually compiling a latex file and converting it to a pdf?

Probably the command you typed and the input file would be helpful.

Hey :)

No this is not by hand, just clicked on "Quickbuild" in TeXmaker and posted the logfile here...

This is what I have written:

[QUOTE]
\documentclass[10pt,a4paper]{article}
\usepackage[latin1]{inputenc}
\usepackage{amsmath}
\usepackage{amsfonts}
\usepackage{amssymb}
\author{Stefan}
\begin{document}
Test
\end{document}
[\QUOTE]

How do I compile manually?

---

### Post by Dougie187 on 2009-01-16
To compile manually, just open a terminal, and navigate to where the document it stored. Since it is called Test.tex then you can simply type
```

latex Test.tex
dvipdf Test.dvi
evince Test.pdf

```
and Evince should open and show you the pdf.

---

### Post by Blueball32 on 2009-01-16
...now thats CRAZY!!!!!!!!!!!!! I just found out that the files I saved did not have the extension .tex...so I tried to write .tex when I saved the file...and now it works...it works all...even though I have opened a .tex file before WITH such an extension and it did not work...

---

### Post by Blueball32 on 2009-01-16
> **Dougie187 said:**
> To compile manually, just open a terminal, and navigate to where the document it stored. Since it is called Test.tex then you can simply type
```

latex Test.tex
dvipdf Test.dvi
evince Test.pdf

```
and Evince should open and show you the pdf.

And the manual compilation also worked. Nice! Thanks for the help. :)

---

### Post by frisket on 2009-01-16
> **Blueball32 said:**
> Aaargh, it doesn't work...I followed a step by step instruction and it just won't work...:(

But can you post the test.tex file?

---

### Post by Blueball32 on 2009-01-16
> **frisket said:**
> But can you post the test.tex file?

Hey, it works already, just see above. :)

Thanks

---

