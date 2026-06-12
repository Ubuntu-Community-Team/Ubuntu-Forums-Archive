---
title: "File Associations 101 -- I need help"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by cwmoser on 2009-07-09
One thing that I have not fully understood is how to associate an opening application with a file extension type.

For example, if I right click on a PDF file and select Properties -> Open With, I have 2 choices Adobe Reader 9 and Document Viewer.  

If I select Document Viewer, when I double click on an *.pdf file, the document opens in Document Viewer as I expect.

But, within FireFox when I click on a PDF link, I get this error:
"... could not be opened, because the associated helper application does not exist.  Change the association in your preferences"


Within Epithany browser, I get Adobe Reader as the app that handles *.pdf files.

What am I missing here?

Thanks

Carl

---

### Post by kaibob on 2009-07-09
> **cwmoser said:**
> ...But, within FireFox when I click on a PDF link, I get this error:
"... could not be opened, because the associated helper application does not exist.  Change the association in your preferences"...


In Firefox go to *Edit > Preferences > Applications*. That is where the Firefox helper application preferences are set.

---

### Post by cwmoser on 2009-07-09
Thanks for pointing me to Edit -> Preferences -> Advanced

I took your advice and changed the 3 PDF associations to use Documnent Viewer - i.e. evince.  Selected "Use other .." and set it to /usr/bin/evince

Thanks

Carl

---

