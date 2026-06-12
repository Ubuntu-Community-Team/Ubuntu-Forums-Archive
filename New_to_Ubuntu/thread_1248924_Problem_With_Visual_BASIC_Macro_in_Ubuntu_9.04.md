---
title: "Problem With Visual BASIC Macro in Ubuntu 9.04"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by SillySod on 2009-08-24
I have a spreadsheet which I originally made in Excel about 3 or 4 years ago with macros in Visual BASIC.  It always used to work in Ubuntu 8.10 but it doesn't work in Ubuntu 9.04.

When I run the macro I get the following error message box:

```

BASIC runtime error.
'1'
Type: com.sun.star.container.NoSuchElement.Exception
Message: .

```

and the line highlighted is
```

Sheets(sh$).Select

```

Can anybody help me fix this?

---

### Post by DaithiF on 2009-08-24
Hi,
I think it is saying that there is no sheet in that workbook with the name of whatever is contained in the sh$ variable.  Can you check what that variable contains, and whether or not that sheet does actually exist?

---

### Post by SOULRiDER on 2009-08-24
Maybe its a problem with OpenOffice 3.

Try running any OOo 2 and see fi it works.

---

### Post by SillySod on 2009-08-25
It's a spreadsheet/workbook which I have been using for some years.  I haven't done anything to it in terms of changing the names of the sheets or the code, so I was assuming it was a problem resulting from the upgrade to Ubuntu 9.04.

How do I get back to Openoffice 2 to try this out?

---

### Post by SillySod on 2009-09-20
Fixed it!

It was an incorrect sheet name after all!  But I didn't rename anything.  At some point (possibly when converting the file from an Excel sheet to an Open Office sheet, or when I upgraded from Open Office 2 to Open Office 3) the "-" character in some of the sheet names had been converted to "_" so the macro wasn't finding the sheets it was looking for!

---

