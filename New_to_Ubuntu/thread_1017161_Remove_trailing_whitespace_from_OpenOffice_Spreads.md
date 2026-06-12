---
title: "Remove trailing whitespace from OpenOffice Spreadsheet cell"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Craigy90 on 2008-12-20
Hi everyone,

I've been trying to figure this one out for a while now:

When I copy a table from a certain website into OpenOffice 'Calc', the table comes out ok, except when I try to sum up columns. The problem is, for some reason the website inserts four spaces after each numeric value, turning it into a string which OOo cannot sum. I frequently have to add up these numbers, so it is a real pain to remove all of the spaces first.

Is there a way to automatically remove whitespace like this from a column? I have tried Format Cells > Number, but that did not change anything.

Thanks, and Merry Christmas! :)

---

### Post by MrWES on 2008-12-20
in another column, try =trim(cell)


Bill

---

### Post by Craigy90 on 2008-12-20
That appears to take away the whitespace, but I am still not able to sum the values. Do I have to convert to numbers somehow?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=97090&stc=1&d=1229820636[/IMG]

Thanks for the quick reply.

---

### Post by kat_ams on 2011-08-24
Sorry to wake the dead, but there is an easier way of doing this.

In LibreOffice, OpenOffice or Gnumeric (or any other spread sheet that supports find and replace using regular expressions)

[LIST]
[*]Find and Replace (CTRL+F)
[*]Click More Options
[*]Click Regular Expressions
[*]Copy and paste the following to the Search For: box
[*]```

^[ \t]+

```
[*]Leave the Replace box empty
[*]put a tik mark in front of Regular Expression 
[*]Try it first with replace
[*]If you are happy with the result then 
[*]Replace All.
[/LIST]

---

