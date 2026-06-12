---
title: "Finding Duplicate instances of a word within a single document and between 2 docs."
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Kat of Zion on 2009-04-24
I have a batch of usernames I must sort for my company.  I have a text file (called orig.txt) that contains multiple names, clustered in groups of 25, with each name seperated by a comma and space.So this file contains all names of people I have done a particular action for.

Now, I have another set of names that came in from my employer.  There is a scant possibility that this new list (call it "list2.txt") has names that were also in orig.txt, and thus need to be eliminated.  Secondly, it is possible that list2.txt has duplicate names within its file alone.  

How would I run a check for duplicate names between the two files? How would I check for duplicate entries just within the second list(list2.txt)?  Can I do it without losing the 25-name long clusters?  I dont mind if I get a way to find all the duplicate names and remove them from list2.txt?

Hope that is not too confusing.

---

### Post by coffeeaddict22 on 2009-04-24
Depends what you're most comfortable with.
I'd import the files into Calc- you've said they're essentially a set of CSV's already; from there you can use a formula to find duplicates pretty easily.  The groups of 25 shouldn't be too much of a problem to keep.

---

### Post by Kat of Zion on 2009-04-24
> **coffeeaddict22 said:**
> Depends what you're most comfortable with.
I'd import the files into Calc- you've said they're essentially a set of CSV's already; from there you can use a formula to find duplicates pretty easily.  The groups of 25 shouldn't be too much of a problem to keep.

Yeah. Would I have to remove any notes (paragraph descriptions I set in there to remember certain keynotes), carriage returns/blank lines before doing so?  I remember trying to have OpenOffice open it as a CSV and it understood commas denote seperate "cells" but it still maintained the carriage returns.

What would be the formula to find duplicate cells not only within its own document but within the second document?

---

### Post by coffeeaddict22 on 2009-04-24
Should be able to leave the notes.  Use your favourite text editor and a find & replace function to make sure the row separator is unique.
In Calc, merge the first and last names if you have to (if first name is column A, last is B, then A1 &" " & B1, copy it down the row); then the next column from row 2 down would be something like =COUNTIF(C$1:C15, C15); that'll give you a list of duplicated rows which you can then fix however you want.  

I tend to copy/paste_value to get rid of the formula, then sort; another option(especially if you want to keep notes as well) would be to use an =if() function to copy over to another column only the data you want to keep, then cut& paste into a new worksheet.  The above formula marks each unique line with a 1.  It wouldn't be too hard to copy notes down from duplicated lines by using a MATCH() function. 

 You can then export into a CSV if you need it back in that format.

---

### Post by Kat of Zion on 2009-04-24
> **coffeeaddict22 said:**
> Should be able to leave the notes.  Use your favourite text editor and a find & replace function to make sure the row separator is unique.
In Calc, merge the first and last names if you have to (if first name is column A, last is B, then A1 &" " & B1, copy it down the row); then the next column from row 2 down would be something like =COUNTIF(C$1:C15, C15); that'll give you a list of duplicated rows which you can then fix however you want.  


In the way I imagine, I would be able to first open orig.txt as a csv in Calc, than open file2.txt (the text file that I want the dups removed from, orig.txt contents need to not change or be removed) as a CSV.  Copy the file2 contents from its doc into the spreadsheet that has orig.

Then do the Data>Filter>Standard... and have it remove dups.  

My only question is that if dups get removed, does it just leave that cell blank or does it delete the cell's contents and move everything to the right of it over?

---

