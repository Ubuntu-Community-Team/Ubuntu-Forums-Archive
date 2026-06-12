---
title: "Can OpenOffice.org open excel documents and visa versa?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Artemis Fowl on 2010-09-07
Someone I know is considering switching to ubuntu, but this is a big problem, so far.

---

### Post by Paddy Landau on 2010-09-07
Yes.

OO can open MS Office documents (except Publisher), and can save in their formats, too.

It may have formatting problems with very complex layouts, but for general use (as I use them) I've never had a problem.

MS has promised to support open standards. If MS is being sincere, we should see the new version (not yet released) supporting OO documents, too.

OO does have a batch converter to convert all the MS documents into OO format. I would recommend doing that once your friend has successfully converted to Ubuntu, because OO will open and save files faster, and in my experience takes less disk space.

---

### Post by migs73 on 2010-09-07
Yes, OO can open Excel docs and can save docs as in Excel format to allow opening in MS Office. This is not 100% guaranteed to give correct formatting though and there will be problems with more complicated functions.

EDIT; Paddy beat me to it

---

### Post by philinux on 2010-09-07
> **Artemis Fowl said:**
> Someone I know is considering switching to ubuntu, but this is a big problem, so far.

Open office is installed by default.

[http://en.wikipedia.org/wiki/OpenOffice.org_Calc](http://en.wikipedia.org/wiki/OpenOffice.org_Calc)

and 

[http://www.openoffice.org/](http://www.openoffice.org/)

---

### Post by Artemis Fowl on 2010-09-07
Thanks, guys. Consider the ubuntu population +1.

---

### Post by col48 on 2010-09-07
On the size issue, my experience suggests that OO Writer (the bit of OO corresponding to Word) creates .doc (Word 97 version) documents which are bigger than the corresponding .odt (OO's format) document is.  But they are fully openable by Word.  Opening a .doc in Writer then immediately saving it as .odt the resulting file is normally smaller (sometimes a third the size) but not always.  OO even can generally handle .docx but not some complex stuff.

My experience with Excel and (OO's) Calc is less but with similar results.  Note that macros will not be automatically converted but if you have a little experience with writing macros in Excel the Excel macro is fairly straightforward to adapt for Calc.  (Both are similar dialects of Basic).

Version of (other people's) MS Office: usually 97, some later
Version of my MS Office: 1995
Version of OO: 2.4

---

### Post by Hagar Delest on 2010-09-08
For the .doc/.odt file size, that's normal behavior. The .doc format is a binary format whereas the .odt format is made of XML files zipped into an archive. It's therefore compressed and doesn't need any further compression BTW. So the file size decreased is noticeable, except if your document is mostly made of pictures.

If Writer is more powerful than MS Word IMHO (especially because of styles), Calc can have less features. For example, the equivalent of the pivot table has only 8 fields, it can be a serious limitation if you've an extensive use of big pivot tables.

Better try first with a live CD if OOo matches the needs and then install it. Note that Ubuntu ships the Novell version instead of the vanilla version from Sun. But the latter can be installed in place of the former if needed.

---

