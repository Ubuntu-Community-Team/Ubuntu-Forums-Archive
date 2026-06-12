---
title: "Neither Kile nor TexMaker not find new Latex packages"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by conormw on 2011-05-18
Hi folks,
I am a relatively new user of Ubuntu, and I've been able to solve many of my problems thusfar by reading these forums.  So thanks to those here who provide such useful feedback.

Unfortunately, I was unable to find a solution to my problem in previous threads.  Neither Kile nor Texmaker seems to find xy.sty.  Here's what I've tried:

1.  I copied the folders containing xy.sty (and all of their contents, including xy.sty) into the directory

/usr/local/texlive/2010/texmf-dist/tex/latex

This is where I found the folders containing the other packages I use (e.g. there is a folder for amsmath, which contains the amsmath.sty).



2.  I ran the command

sudo texhash /usr/local/texlive/2010/texmf-dist/tex/latex

to rebuild the ls-R file ; I also ran the texhash command on all directories containing this one.  After each command was issued, I opened the ls-R file to check that it listed xy.sty in the correct folder.

Yet both Kile and TexMaker tell me that xy.sty is not found.

Do I need to do something to these applications in order for the new Latex packages to be found?

I am running 11.04.

---

### Post by tdupu on 2011-06-07
I had the same problem. I didn't try copying things over but I thought kile was supposed to find the packages that you wanted to automatically.

edit: I'm using old tex files that worked fine on Karmic to Ubuntu 11.04. In particular 

{{ \usepackage[all,cmtip]{xy} }}

doesn't work.

---

### Post by iclestu on 2011-06-07
you guys using texlive, yeah?

Did you use the step-by-step here:

[https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

?

If so, where is it falling down?

---

### Post by iclestu on 2011-06-07
> **tdupu said:**
> ...I thought kile was supposed to find the packages that you wanted to automatically.

Not to my knowledge....

---

### Post by tdupu on 2011-06-07
OK so this might fix it. I need to wait a little but I essentially found it here:

[http://www.latex-community.org/forum/viewtopic.php?f=20&t=1602](http://www.latex-community.org/forum/viewtopic.php?f=20&t=1602)

In the synaptic package manager you can find some packages to install. This might work. I need to wait for it to install but I will let you know if it works for me.

Edit: This worked for me. You can actually check which latex packages are going to be installed with each of the synaptic packages before you try them. I just installed a bunch and it worked (although I shouldn't have in hindsight... I should have just installed the xypic package)

---

### Post by frisket on 2011-07-02
**Never** modify the installation directories, because an update may erase what you have added. 

**Always** put new LaTeX packages in your personal TeX tree at ~/texmf/tex/latex/<packagename>

You do not need to run texhash, because LaTeX will always check this path first, before trying the system installation directories, so you can put updates here too. 

(If you are adding to a shared installation, put them at /usr/local/share/texmf/tex/latex/<packagename> instead, and then run sudo texhash.)

Installation of additional packages should be a rarity if you have installed texlive-full anyway.

**Read The Fine Documentation**, especially the TeX FAQ at [http://www.tex.ac.uk/faq/](http://www.tex.ac.uk/faq/)

---

