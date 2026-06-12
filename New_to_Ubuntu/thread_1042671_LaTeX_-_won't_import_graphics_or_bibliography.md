---
title: "LaTeX - won't import graphics or bibliography"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2009-01-17
I have my texfile written up in texmaker:

[http://www.ugrad.physics.mcgill.ca/resources/latex/template/template.tex](http://www.ugrad.physics.mcgill.ca/resources/latex/template/template.tex)

The relevant lines being:

```
\begin{figure}[H]
\begin{center}
\includegraphics[scale=0.65]{pendulum.eps}
\end{center}
\caption{Variation of period of a pendulum as a function of length.}
\label{FIG-PEND}
\end{figure}
```

```
\bibliographystyle{unsrt}	% Order by citation
\bibliography{report}
```

For some reason, it seems like the graphics nor the bibliography are being imported. The .eps files and the .bib file are all in the same directory as the .tex file. I definitely have the graphicx package and I'm pretty sure I have the unsrt package. I've been looking at this for the past hour or so and haven't gotten anywhere =/.

---

### Post by llamakc on 2009-01-17
You may need to run latex first, then bibtex, and latex twice more.

So:

latex FILENAME
bibtex FILENAME
latex FILENAME
latex FILENAME

I haven't looked at your .tex file but make sure your preamble has 

\includepackage{graphicx}

EDIT: I looked at the template & see you do have the above in the template.

Are you running latex or pdflatex?

---

### Post by I[AM]SMRT on 2009-01-17
> **llamakc said:**
> You may need to run latex first, then bibtex, and latex twice more.

So:

latex FILENAME
bibtex FILENAME
latex FILENAME
latex FILENAME

I haven't looked at your .tex file but make sure your preamble has 

\includepackage{graphicx}

EDIT: I looked at the template & see you do have the above in the template.

Are you running latex or pdflatex?
I'm using texmaker so I think it's using latex.

EDIT: Using the command line seems to have made the bibliography work (so I now know it's a texmaker problem) but the graphics still won't import.

---

### Post by llamakc on 2009-01-17
What does texmaker output? The dvi, ps, or pdf?

---

### Post by I[AM]SMRT on 2009-01-17
The command I'm currently using outputs a dvi and a ps.

EDIT: The bibliography now works with texmaker, it seems that texmaker was having a problem "linking" the bib file with the tex file.

---

### Post by llamakc on 2009-01-17
Are you pressing the LaTeX button only?

Or a combination of buttons in texmaker? (I'm installing it now).

---

### Post by llamakc on 2009-01-17
When viewing the dvi you will see an empty space where the figure would be. You must convert from dvi to ps to pdf. If you print the ps you will see the figure. 

Are you married to using eps files? It may be easier to convert to pdf instead (and run pdflatex instead).

---

### Post by I[AM]SMRT on 2009-01-17
There's a "quick build" button that's outputting the dvi/ps. I just tried the LaTeX button but it doesn't seem to make any difference in the dvi file, I mean why should it, the command line latex didn't work.

> **llamakc said:**
> When viewing the dvi you will see an empty space where the figure would be. You must convert from dvi to ps to pdf. If you print the ps you will see the figure. 

Are you married to using eps files? It may be easier to convert to pdf instead (and run pdflatex instead).
Wow, why is that I can't see it in the dvi? Is that just how dvi files work?

I mean, I'll probably in the end convert everything to pdf so it's not a huge deal. Thanks for the help!

---

### Post by Ng Oon-Ee on 2009-01-20
I'm no LaTeX expert, but been using it this couple of weeks. Only using pdftex, though, since the syntax of some things change, and I think I'll only ever need to output pdf files for my publications and reports.

Oh, and I'm using an IDE =). Texlipse, plugin to Eclipse. Never had a problem with including graphics, I think it does most of the work for me, though.

---

