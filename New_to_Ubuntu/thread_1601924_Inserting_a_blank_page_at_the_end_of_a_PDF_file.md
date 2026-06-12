---
title: "Inserting a blank page at the end of a PDF file"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by greffenstette on 2010-10-20
Hi,

I want to merge a several PDF files into a single file to, afterwards, print it (double size)

The problem is that the first document has an odd number of pages (17), so if I use pdftk with the standard "cat" option, the next document will start in the page 18, and it will be a "printing mess."

So, in brief, how could I automatically add a blank page to every document with a odd number of pages?? (bear in mind that I have also documents with an even number of pages). Afterwards, I could merge them using pdftk. Any other idea? 

Thank you!
Gref.

---

### Post by sanderd17 on 2010-10-20
LaTeX isn't designed for it, but you can use it for that purpose. I don't know if it could be done automatically, but I guess it could.

In fact, LaTeX is a typesetting program, so I'll wait before I search on how to automatise it. Maybe there's a better solution which doesn't need lots of LaTeX libraries.

---

### Post by greffenstette on 2010-10-21
> **sanderd17 said:**
> LaTeX isn't designed for it, but you can use it for that purpose. I don't know if it could be done automatically, but I guess it could.

In fact, LaTeX is a typesetting program, so I'll wait before I search on how to automatise it. Maybe there's a better solution which doesn't need lots of LaTeX libraries.

Well... I have worked a lot with LaTeX, and to be honest, I don't see how LaTex can solve this situation.

Basically I need a programme which (automatically) transforms PDF with a odd number of pages, into a PDF with a even number of pages...
  
Afterwords, the merge would be easy.

---

### Post by sanderd17 on 2010-10-24
Sorry for the late reply, didn't have time to search the right commands.

You can make a LaTeX file with the code

```

\documentclass[a4paper]{article}
\usepackage{pdfpages}

\begin{document}

\includepdf[openright]{doc1.pdf}
\includepdf[openright]{doc2.pdf}
\includepdf[openright]{doc3.pdf}
\includepdf[openright]{doc4.pdf}
...

\end{document}

```

then pdfLaTeX it and you get the output.

---

### Post by NESFreak on 2010-10-26
You wouldn't need latex. A simple shellscript would be enough.

to get you started:
```

for file in *.pdf
do
  #get the number of pages
  numberofpages=`pdftk $file dump_data | sed -e '/NumberOfPages/!d;s/NumberOfPages: //'`
  echo -n $file 'has' $numberofpages 'pages, '
  
  uneven=$(($numberofpages % 2))
  if [ $uneven == 1 ]
  then
    echo 'which is uneven'
  else
    echo 'which is even'
  fi
done

```

which returns something like
```

Colley_VectorCalc3_ch01.pdf has 69 pages, which is uneven
Colley_VectorCalc3_ch02.pdf has 67 pages, which is uneven
Colley_VectorCalc3_ch03.pdf has 44 pages, which is even
Colley_VectorCalc3_ch04.pdf has 42 pages, which is even
Colley_VectorCalc3_ch05.pdf has 66 pages, which is even
Colley_VectorCalc3_ch06.pdf has 32 pages, which is even
Colley_VectorCalc3_ch07.pdf has 61 pages, which is uneven
Colley_VectorCalc3_ch08.pdf has 22 pages, which is even
Colley_VectorCalc3_fm.pdf has 6 pages, which is even

```
for a random directory with pdf's that i have

you could simply replace the echo commands with your own append commands.

---

### Post by sanderd17 on 2010-10-26
> **NESFreak said:**
> You wouldn't need LaTeX. A simple shellscript would be enough.


I though it would be possible with a shell script, I just didn't know how.

---

### Post by greffenstette on 2010-10-27
> **NESFreak said:**
> You wouldn't need latex. A simple shellscript would be enough.


Nice! thank you!

---

