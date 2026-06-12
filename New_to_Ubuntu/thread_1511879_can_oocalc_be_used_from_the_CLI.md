---
title: "can oocalc be used from the CLI?"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by jr56 on 2010-06-17
Hi Forum, I'm a recent convert from the non-Linux world. I've decided to learn it as best I can, especially wrt the CLI. Here's my question:
 
What's the easiest way to do the following, from the command line:
 
Open an existing spreadsheet file, find the rows that have at least 8 columns of data, and print the data in those rows to a txt file.
 
In pseudocode, I assume the expression would look something like this:
 
oocalc jr.xls { print{ find count[#]>8, jr.txt} } ?
 
Thanks for the help! Sorry if I've sounded like I have no idea what I'm talking about (bc that's very true! Lol.)
 
-jr

---

### Post by Hospadar on 2010-06-17
I suspect probably not.

But! you can probably dump the ods file to a csv (which is a text format), then search for and print out the data with any number of tools (bash:grep/sed/awk, python, octave, etc).  I'm not sure if OO provides a direct way to dump csv's on the command line, but I'm sure there are other things to do that for you.  I discovered this with a little googling:

[http://www.artofsolving.com/opensource/jodconverter](http://www.artofsolving.com/opensource/jodconverter)
(goto gude->use as a command line tool)

---

### Post by jr56 on 2010-06-17
Losing formatting in a .ods to .csv conversion will casue more problems to the data I'm trying to extract than I'd like.   
 
Maybe I should backup a step and ask this question instead:
 
Does anyone know of any spreadsheet operations that can be issued from the command line?
 
I also notice that a similar topic remained unsolved [here]("http://www.linuxquestions.org/questions/linux-newbie-8/command-line-text-file-viewing-and-editing-odt-etc-719095/"), so extra bonus beans to anyone who can provide a fix!
 
Thanks!

---

### Post by fatality_uk on 2010-06-17
No it can't. Ooo can take cli parameters, see wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Getting_Started/Starting_from_the_command_line
but pretty sure not what you want to do

---

### Post by jr56 on 2010-06-17
Hmm...   Ok well, I need to access spreadsheet data without using GUI.  From what it sounds like, I assume I'll need to write a script (perl, python, etc.) to do this.
 
Could someone please recommend a command/function in one of those languages that would be able to read a spreadsheet file & store the cell data as native numbers/strings?
 
Thank you...

---

### Post by EssexEagle on 2010-06-17
Have you looked into writing macros in Calc to do this?  (I've never done any macros in OpenOffice so I wouldn't know where to start I'm afraid, but hopefully someone here will be able to point you in the right direction.)

---

### Post by sdennie on 2010-06-17
As stated above, you will probably have to save the file as a .csv.  At that point, you have an entire universe of tools to do what you want.  Perl, awk, sed, cut, etc...

---

