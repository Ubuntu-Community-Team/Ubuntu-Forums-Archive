---
title: "PDF Editing ...."
date: 2009-06-27
forum: New to Ubuntu
---

### Post by expatCM on 2009-06-27
I have a large pdf file.  I wish to delete a number of pages.  I have opened PDFedit and selected a page and pressed delete.  Not a lot happens.  I see the following message

```
Warning: This document is linearized PDF!
> deleteObjectsInTree()
! In script '/usr/share/pdfedit/menu.qs', line 213:
! Error. Exception in TreeItem.remove : Document is read-only
```

I looked at the document permissions and there is read / write set for user and group.  I have also tried to open pdfedit as sudo but the same message appears.

Any ideas how to delete pages in a pdf?

---

### Post by kaibob on 2009-06-27
> **expatCM said:**
> Any ideas how to delete pages in a pdf?

I don't know precisely what that error message means. It's funny that it gives the read-only error message when the file is not read only. 

If all else fails, and you're a bit desperate, you can try the PDFtk command line utility. It doesn't allow you to delete pages as such--instead you have to show the pages to include.

By way of example, to delete pages 5 and 10 of a 20-page document, use the following:

```
pdftk input.pdf cat 1-4 6-9 11-20 output output.pdf
```

I don't believe that PDFtk is installed by default, but it's easily installed with the Synaptic Package Manager.

---

### Post by PGScooter on 2009-06-27
pdftk is great!!! and I think there might be away to make the above code a little more general by using "end" (or something like that) instead of 20. I don't know why what I suggested would be useful but thought I would throw it in :)

---

### Post by expatCM on 2009-06-27
Well I have just installed it. Now is time for playing to see what it will do.

Thank you for the suggestion and for the specimen syntax.

---

### Post by mediax on 2009-08-15
Apologies for joining this so late, but I've just discovered the solution to the original problem.

In pdfedit (without the file open), select Tools, Delinearize. This prompts you to select a file to open - select the file you wish to work with and press Open.  You will then be prompted to Save File As - enter a suitable file name and hit Enter.

You should then be able to open and edit the (new) file to your heart's content.

Now, if only I can work out how to mass delete all these headers and footers . . .  ](*,)

---

### Post by scorp123 on 2009-08-15
> **mediax said:**
>  Now, if only I can work out how to mass delete all these headers and footers . . .  ](*,) I installed this package: "openoffice.org-pdfimport"

```
sudo apt-get install openoffice.org-pdfimport
```

It allows you to open PDF files in OpenOffice ... as if they were normal ODF documents. Editing PDF's gets _really_ easy this way.

[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

---

### Post by mediax on 2009-08-16
Thanks Scorp, I'll have a look at it.

My only reservation is that I'm looking to tweak scanned books, so the note about potential problems with files more than 20 pages long looks ominous.

---

### Post by shakma on 2010-04-27
Just wanted to say thanks for the "pdftk" tip.  I had to extract 1 page from a multi-page PDF, and because it was saved as "read-only", PDF Mod wouldn't open it.  God bless the command line!  After 2 hours playing with GUI apps yesterday, a single command did it in 5 seconds today.:guitar:

Peace.

---

