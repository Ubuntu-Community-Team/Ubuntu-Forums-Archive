---
title: "delete pages in openoffice writer"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by jrev on 2010-11-15
Hello,
In a new writer document I inserted a table that run on about 10 pages numbered in the page foot
I then suppressed a number of lines from this table so that I got only the first two pages filled.
But I could not find How to erase the empty pages ?
May be you can tell me what to do
Thanks for your answer :)

---

### Post by theozzlives on 2010-11-15
> **jrev said:**
> Hello,
In a new writer document I inserted a table that run on about 10 pages numbered in the page foot
I then suppressed a number of lines from this table so that I got only the first two pages filled.
But I could not find How to erase the empty pages ?
May be you can tell me what to do
Thanks for your answer :)

Should highlight the cells, right-click and go to delete cells.

---

### Post by nns2006 on 2010-11-15
I suppose You want to delete the unwanted pages that are still there after you have removd the rows from table.
Put your cursor at the end of document and press delete button. Hold it for few seconds . I think it will helps.

---

### Post by jrev on 2010-11-15
I cannot put my cursor at the end of the document : there is no rows or sign or space sign in the pages
these are empty pages I can only put the cursor in the foot of page 
I put some spaces after the title of the document before the table and the table went down 
But I cannot move the table at the beginning of the document again

---

### Post by Hagar Delest on 2010-11-15
Can you upload a sample file?

---

### Post by jrev on 2010-11-16
How do I do that ?

---

### Post by Hagar Delest on 2010-11-16
You can attach here or use a 3rd party file sharing web site like mediafire.com.

---

### Post by jrev on 2010-11-17
Thank you hagard, I solved the problem :
[http://forum.ubuntu-fr.org/viewtopic.php?id=428965](http://forum.ubuntu-fr.org/viewtopic.php?id=428965)
:)

---

### Post by simormate on 2011-07-07
The solution I found [here]("http://noahlittle.wordpress.com/2010/10/27/delete-blank-page-after-table-in-open-office-writer/"):

In OpenOffice writer it seems that tables insist on being followed by a new line. This means that you cannot get rid of new line characters between tables. It also means that you cannot get rid of a new line character when it follows a table at the end of a document.

This latter case can mean that you need to reduce the size of the bottom page margin just to make sure then new line character doesn’t get printed on a new page. What ought to happen is that there should be no new line of text after a table unless you actually want one.

Other solution: Go to end of paragraph in right bottom cell. Push Ctrl+Shift+Delete. On a Mac that’s cmd + shift + delete

---

