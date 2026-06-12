---
title: "metadata and latex document"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by cosine352 on 2009-11-11
Hello!
I am writing a pdf document in latex (text editor is Kile). Do anyone know how to put metadata in the pdf file. 
thanks

---

### Post by gmjs on 2009-11-11
I've used the 'hyperref' package (as the document typesetter 'LyX' does) in the past to add PDF metadata.  The PDF title, author and subject can be specified as package options (in square brackets) as follows:

```
\usepackage[
   pdftitle=Title\ Goes\ Here,
   pdfauthor=Author\ Goes\ Here,
   pdfsubject=Subject\ Goes\ Here]	
   {hyperref}
```


Rather than using speech marks around the data items (these appear in the metadata) I'd escape the spaces instead (as above).

Hope this helps,

Graham

---

### Post by cosine352 on 2009-11-11
> **gmjs said:**
> I've used the 'hyperref' package (as the document typesetter 'LyX' does) in the past to add PDF metadata.  The PDF title, author and subject can be specified as package options (in square brackets) as follows:

```
\usepackage[
   pdftitle=Title\ Goes\ Here,
   pdfauthor=Author\ Goes\ Here,
   pdfsubject=Subject\ Goes\ Here]	
   {hyperref}
```


Rather than using speech marks around the data items (these appear in the metadata) I'd escape the spaces instead (as above).

Hope this helps,

Graham
 Thanks Graham. I am doing it like this now and working fine with the hyperref
> 
\usepackage{hyperref}
\hypersetup{
  colorlinks = true,
  urlcolor = black,
  pdfauthor = {your name},
  pdfkeywords = {keywords},
  pdftitle = {title},
  pdfsubject = {subject},
  pdfpagemode = UseNone
}

---

