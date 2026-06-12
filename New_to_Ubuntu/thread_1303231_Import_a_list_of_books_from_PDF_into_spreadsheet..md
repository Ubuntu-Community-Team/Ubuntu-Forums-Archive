---
title: "Import a list of books from PDF into spreadsheet."
date: 2009-10-28
forum: New to Ubuntu
---

### Post by hanzj on 2009-10-28
Please see attached the first page of a "Recommended Reading" list of books.

I want to import/convert the list into OpenOffice Spreadsheet (and ultimately to Google Spreadsheets) where each title is in its own cell.

I don't know how to manipulate the "Text Import" options in OpenOffice Spreadsheet to my goal.

I wish there was a way for us to do some minor programming, telling Oo.o that a new row should be made after a number and the period symbol (since each title ends with a year and the period/full-stop symbol.) Or, period that is followed by a new line/line-break.

The ideal would be for there to be three columns in the spreadsheet. 1st column has the author name. 2nd column has the title. 3rd column has publishing info (city: publisher, year). But I'd be content for each complete entry just to be in its own cell.

Is this possible? Or, how can I accomplish what I seek?

The complete list is 8 pages long, so I didn't want to do this manually.



[COLOR="Sienna"]
[FONT="Verdana"]SOLVED: Thanks to [COLOR="Red"]**Lavinog**[/COLOR] for his amazing skills.[/FONT][/COLOR]=D>=D>=D>=D>

---

### Post by falconindy on 2009-10-28
Under 'Separated By', select only "other" and put in a period. Should look something like this.

[img]http://i38.tinypic.com/kyemf.jpg[/img]

It'll require a little bit of cleanup aftwards but this is probably the simplest way given the small number of entries you're dealing with.

---

### Post by hanzj on 2009-10-28
falconindy,
i've thought of that option, but it separates too many "periods". For example, after author names. In other words, it's probably more messy than no automatic separators.

---

### Post by lavinog on 2009-10-28
> **hanzj said:**
> 
I wish there was a way for us to do some minor programming, telling Oo.o that a new row should be made after a number and the period symbol (since each title ends with a year and the period/full-stop symbol.) Or, period that is followed by a new line/line-break.


it could be converted to text, then a script could be used to break it up into a csv file.

I can attempt something in a couple of mins.

---

### Post by falconindy on 2009-10-28
It's 24 lines. No offense, but you could spend an hour trying to figure out how to best import it, or take 10 minutes to format the work of a rough import manually.

---

### Post by hanzj on 2009-10-28
no, not 24 lines (one page). it's 24 lines * 8 pages.

---

### Post by lavinog on 2009-10-28
> **falconindy said:**
> It's 24 lines. No offense, but you could spend an hour trying to figure out how to best import it, or take 10 minutes to format the work of a rough import manually.

8 pages

---

### Post by hanzj on 2009-10-28
lavinog, 
great!
pls note my ideal.
> The ideal would be for there to be three columns in the spreadsheet. 1st column has the author name. 2nd column has the title. 3rd column has publishing info (city: publisher, year).

For example,
Column 1: Adair, John

Column 2: Founding Fathers: The Puritans in England and America
 
Column 3: Grand Rapids: Baker, 1994



(sorry for double-post. Chromium browser issues.)

---

### Post by iMisspell on 2009-10-28
How do you import a file with OpenOffice Spreadsheet ?
Just was peaking around and could not find the option.
Downloaded and installed the extension:
[http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

Restarted openoffice and cant find the option (there is a PDF export option, but dont see the import).
_

---

### Post by hanzj on 2009-10-28
iMisspell,
From the PDF, I just copied the text, went to OpenOffice Spreadsheet (new/blank), clicked on the first cell and did "Paste" (Ctrl+V or Paste button).

---

### Post by iMisspell on 2009-10-28
Ohh... so there is not a "true" import option in OpenOffice (im new to this :) ) ?
What menu/window did 'falconindy' use ?

How that PDF is formatted you could use the following delimiters
\r (or \n) to get the line, then the period (.) with array(0) column one  array(1) column two and  array(2) column three, by the looks of things.

Knowing how OpenOffice works seams to be the trick.

_

---

### Post by hanzj on 2009-10-28
iMisspell,
i'm new to openoffice, too (I use Google Docs most of the time). To see what falcoindy has, just do as I've instructed and that window will pop-up.

I would like to try your suggestion, but I don't understand. Could you explain what you wrote:

> \r (or \n) to get the line, then the period (.) with array(0) column one array(1) column two and array(2) column three, by the looks of things.

---

### Post by lavinog on 2009-10-28
lines such as below make delimiting difficult.  I am making progress on a script though.
```
Bromiley, G.W., ed.
```

---

### Post by hanzj on 2009-10-28
> **lavinog said:**
> lines such as below make delimiting difficult.  I am making progress on a script though.
```
Bromiley, G.W., ed.
```


Thank you very much

---

### Post by lavinog on 2009-10-28
save the attached script to a folder.

copy and paste the text from the pdf to a text file named books.txt in the same folder as the script.

remove anything that isn't a book like the "recommended reading" title and the page numbers.

use this command:
```

python oobooks.py

```
you should see the data parsed
afterwards you can use:
```

oocalc books.csv

```

Let me know if there are any issues.

---

### Post by lavinog on 2009-10-28
Updated the script to ignore page numbers, blank lines and lines that say "recommended reading"

also you can use pdftotext to convert the pdf to the text file instead of copy and paste:
```

pdftotext -layout recommended_reading.pdf books.txt
python oobooks.py
oocalc books.csv

```

if you don't have pdftotext available, it is part of the poppler-utils package.

---

### Post by hanzj on 2009-10-28
lavinog,
Thank you so much. I am at the "oocalc books.csv" stage. Under Separator options, I'm using "separated by" "comma". 

Things look great!

(The only problem was that ubuntuforums renamed your oobooks.py to oobooks.download. But that was not a big problem.) Thanks!!!

---

### Post by hanzj on 2009-10-28
Thank you once, again,=D>=D> **[COLOR="Red"]lavinog[/COLOR]**!=D>=D>=D> I did all 8 pages in 2 minutes.


Wow, the power of python/programming.

---

