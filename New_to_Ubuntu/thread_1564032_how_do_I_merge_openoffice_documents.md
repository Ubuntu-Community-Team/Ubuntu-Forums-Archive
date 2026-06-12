---
title: "how do I merge openoffice documents?"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by donkyhotay on 2010-08-30
I have a large number of open office word documents. I need these files to remain separate for organisation reasons but for distribution purposes it would be useful to be able to quickly merge them together into one document at need. I can't find a simple way to merge them together beyond simple copy/paste which isn't practical. On another forum I saw a recommendation of using a PDF print system but didn't explain how to actually do it, and that was the closest I could find to an answer. The merged version would be exported to PDF from open office anyways so using a PDF printer would be acceptable so long as the output is one single file. Does anyone know an easy way to merge multiple openoffice word docs into one big file, either PDF or ODT format?

---

### Post by Riffer on 2010-08-30
I would try [http://www.openoffice.org]("http://www.openoffice.org") you'll find tons of help there.

---

### Post by Sam Fallow on 2010-08-30
While at the end of your first document you can select 'Insert' file and add further documents one at a time. AFAIK it only works for one document at a time but it is a bit quicker than cutting and pasting. 

Not the solution you were looking for but it's a start.

---

### Post by gandaran on 2010-08-30
try this
[http://www.gnome-split.org/index.html](http://www.gnome-split.org/index.html)
I haven't tried it yet and don't know if it actually works with any file type.

if merging PDF files will do then install PDF-Shuffler or PDF-Mod from synaptic.

---

### Post by Hagar Delest on 2010-08-30
You should have a look at the master documents in OOo: [Working with Master Documents]("http://wiki.services.openoffice.org/wiki/Documentation/OOo3_User_Guides/Writer_Guide/Master_Documents").

Once the master doc is fine, just export it as PDF.

---

### Post by donkyhotay on 2010-08-30
I managed to figure out how to do a print multiple files to PDF and then merge the documents using the CLI. I wrote a script to automate the process. For those interested in how I did it it's pretty much:
```

cd /path/to/directory
oowriter -pt PDF ./*.odt
cd ~/PDF
pdftk ./*.pdf cat output ~/output/file.pdf

```
Obviously of course this requires having cups-pdf and pdftk installed.

---

