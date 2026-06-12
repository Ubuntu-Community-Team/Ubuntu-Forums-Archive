---
title: "which latex package to use?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by orky7 on 2011-06-10
hi i want to work with latex i search the repository there are many packages like 
1-tex live
2. texmaker
3. lyx
etc...
so which one will be good or any other awesome package which i did not found? also have table making capability and graph making capapility(if it is possible)

thanks.

---

### Post by Chronon on 2011-06-10
Are you looking for an editor?  I don't have a huge preference here.  I use Kile currently, but I have been happy working with Geany, Winefish and Gedit in the past.

You can use PSTricks code directly in your LaTeX document to render various graphs.  I haven't reached any great proficiency with this, however, so I usually use a graphics program called LaTeXDraw.  It provides a GUI to create drawings and allows you to export the image as EPS, PSTricks code, PDF, etc.  One nice feature is that it uses LaTeX to render text boxes, so you can insert properly rendered equations and other text into your images.

---

### Post by iclestu on 2011-06-10
> **Chronon said:**
> ..... a graphics program called LaTeXDraw.  It provides a GUI to create drawings and allows you to export the image as EPS, PSTricks code, PDF, etc.  One nice feature is that it uses LaTeX to render text boxes, so you can insert properly rendered equations and other text into your images.

:)

Thanks for this. Sounds really useful for me. Never dreamt such a thing existed. Off to do some google research

---

### Post by frisket on 2011-07-02
The answer is that you should install the following:

texlive-full — this is the full TeX system

emacs or kile (better: both) — these are editors for creating your documents

okular (better: kpdf and kdvi) — WYSIWYG previewers

jabref — a bibliographic database manager for your references

gimp — a bitmap graphics editor for your photographs

inkscape — a vector graphics editor for your diagrams

As has been pointed out, there are lots of other systems for doing diagrams that you can try out and use if you prefer, but I would regard the above as the minimum to be properly-equipped.

---

### Post by tommpogg on 2011-07-03
> **frisket said:**
> The answer is that you should install the following:

texlive-full — this is the full TeX system


I suggest to avoid installing texlive-full: it is a really huge package containg stuff that you will never use (e.g. language support and documentation for each language spoken in this world and more).

Just open synaptic and choose the texlive packages you need. Don't forget Beamer if you want to create presentations.

Concerning the editor, there is a huge list of possibilities. Personally, I prefer gvim.

---

