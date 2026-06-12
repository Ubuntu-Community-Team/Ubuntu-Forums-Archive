---
title: "Latex and multiple Bibtex files"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by simon303 on 2009-01-07
Hi,
I am writing an essay in Latex and want to use two bibtex files, I am told you can do this by simple using two ```
\bibliography{...}
``` commands, but everytime I try this I get an error (Illegal, another \bibdata command).
Any ideas on this?
Also I am trying to get a reference section and a Reading List (from a separate bibtex file if possible, but without having to use the \cite{} command) in my essay, but see no way of doing this.
Thanks

---

### Post by simon303 on 2009-01-07
Also, I seem to be having a bit of trouble using \ref{} to refer to a \label{} in another .tex file from another .tex file that is also not the main file.
It just seems to return a blank space instead of a figure number

---

### Post by simon303 on 2009-01-18
bump

---

### Post by simon303 on 2009-01-20
bump

---

### Post by polmir on 2009-01-20
Present in what is the preamble of your document.

---

### Post by Ng Oon-Ee on 2009-01-20
\bibliography{file1,file2} where your bibtex files are named file1.bib and file2.bib and are in the same directory should always work.

What editor are you using? I use the Texlipse plug-in for Eclipse, simply because I'm already familiar with that IDE and do my development in it, but I know most haven't even heard of it before.

---

### Post by zackbaker on 2010-02-24
Remember to remove all whitespace in the \bibliography command.  

That is, \bibliography{bib1,bib2} not \bibliography{bib1, bib2}

---

### Post by llamabr on 2010-02-24
This thread is more than a year old.  Where would you even find it?

---

