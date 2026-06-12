---
title: "Urgent! Need to convert 100s of pdfs to text for project data input."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by jdisalive on 2009-05-05
Hi, I'm doing a project on text mining and need to append the text in several tens of pdf files in a single text file as input to my program. 

All my pdfs are scattered throughout my system. Is there any way to create this big text file using a shell script and the 'pdftotext' command line utility?

A quick reply would be much appreciated.

Thanks

---

### Post by benj1 on 2009-05-05
what like 

```
for f in *.pdf
do
    pdftotext $f
done
```

?

edit :
then you can use cat to join them together

cat file1 file2 file3 >> bigfile

---

### Post by jdisalive on 2009-05-05
for f in *.pdf
do
    pdftotext $f
done

Thanks for the prompt reply :).

Isn't the usage of 'pdftotext' like 'pdftotext <pdf file> <text file>' ?

My pdfs are all scattered within /home/jubuntu/input\ data/ and its sub-directories.

Would your script work for those within the sub-directories also...

---

### Post by HermanAB on 2009-05-05
Use 'find' to search for files and invoke pdf2text.  Read the find man page.  It is easy to use.

---

### Post by blazemore on 2009-05-05
There's a PDF to HTML converter here:
[http://pdftohtml.sourceforge.net/](http://pdftohtml.sourceforge.net/)

There's an HTML to Text converter here:
[http://jsoftco.8m.com/download.html](http://jsoftco.8m.com/download.html)

I haven't tried these programs, and I got the information from this thread:
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/33788-convert-pdf-text-files.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/33788-convert-pdf-text-files.html)

---

### Post by decoherence on 2009-05-05
UPDATE: sorry, I didn't read your first post well enough. The following command will convert all PDFs under the current directory (and sub directories) and send the output to the file 'bigfile.txt'. It should be exactly what you need.

Go to the directory which your PDFs are under and run

```

find . -name "*.pdf" -exec pdftotext '{}' - >> bigfile.txt \;

```

See? No need for a shell script. But yes, all of those weird extra symbols are required.

---

### Post by finer recliner on 2009-05-05
> **benj1 said:**
> 
cat file1 file2 file3 >> bigfile

easier to do:

```
cat file* >> bigfile
```

:)

---

### Post by jdisalive on 2009-05-05
for f in 'find ~/ -name "*.pdf" -print'
do 
      pdftotext $f hi.txt; cat hi.txt >> corpus.txt
done

This is what you mean right... I'm in windows right now since my wireless internet stick will work only in windows so will reboot later and try ...

Thanks anyway

---

