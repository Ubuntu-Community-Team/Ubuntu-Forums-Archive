---
title: "Creating .pdf with cups-pdf"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by Frogbarf on 2009-01-15
When I try to create a PDF file out of OpenOffice spreadsheet by "printing" to the cups-pdf printer, I don't get a PDF. I get a raw PostScript file with extension .ps.

While Document Viewer can open and render this just fine, it's NOT a PDF file and can't be handled by Acrobat Reader under Mac OS/X.

The workaround is to export as a pdf, which works fine, but I'm still left wondering why a pseudo-printer that advertises itself as generating PDF files doesn't do it in fact.

Haven't found anything in options to change this, btw.

PS: Hardy (Ubuntu 8.04) btw.

---

### Post by Titan8990 on 2009-01-15
This is happening because you are checking the "print to file" checkbox. Leave it unchecked.

---

### Post by stchman on 2009-01-15
> **Frogbarf said:**
> When I try to create a PDF file out of OpenOffice spreadsheet by "printing" to the cups-pdf printer, I don't get a PDF. I get a raw PostScript file with extension .ps.

While Document Viewer can open and render this just fine, it's NOT a PDF file and can't be handled by Acrobat Reader under Mac OS/X.

The workaround is to export as a pdf, which works fine, but I'm still left wondering why a pseudo-printer that advertises itself as generating PDF files doesn't do it in fact.

Haven't found anything in options to change this, btw.

PS: Hardy (Ubuntu 8.04) btw.

First off Openoffice has a native export to PDF.  Second when you install the cups-pdf printer you need to select a generic printer and select postscript color.

---

