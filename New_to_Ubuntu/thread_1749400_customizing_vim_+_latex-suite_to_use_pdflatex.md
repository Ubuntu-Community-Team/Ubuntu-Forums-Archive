---
title: "customizing vim + latex-suite to use pdflatex"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by Wibowit on 2011-05-04
Hi,

I have a hard time figuring out how to force vim to compile LaTeX files to PDF and not DVI. I've tried some suggestions from various sites, involving changes to configuration files somewhere on the disk or creating .vimrc file in home directory but none seems to work. Still, after pressing \ll vim produces .dvi file and after \lv vim runs evince with such .dvi file.

How could I customize Vim to produce PDF files using pdflatex? Note that I use command line version of vim, not gVim.

Update:
I've found a working solution. It's here: [http://stackoverflow.com/questions/3723493/latex-and-vim-usage](http://stackoverflow.com/questions/3723493/latex-and-vim-usage)
Answer:

> If you use vim latex put the following in your .vimrc:

let g:Tex_DefaultTargetFormat='pdf'

and it should compile to pdf by default. (I think the default compilation key is \ll).

---

