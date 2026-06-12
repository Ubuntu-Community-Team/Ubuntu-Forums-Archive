---
title: "Moving from Windows to opensource"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by Jumbo73 on 2009-07-22
Hello All -
 
In the late '80s, I was doing a lot of work in a BSD environment and became quite proficient on the command line.
 
Changes in workplaces moved me into the Windows world, where I've been for a while, appreciating the convenience of the mouse while understanding that a lot of power was missing.
 
I now have a need to do some things that I used to do in the unix world - diff files, use stdin, stdout, pipe, grep, do shell scripting, etc.
 
Some very basic questions that need to be asked as I look to get back to the capability that I once had:
 
Is the set of commands available on the CLI pretty much functionally equivalent to what I was used to?
 
Will I need to run MS Office (Word, Excel) files through a processor to compare them to files created under ubuntu?
 
Can you confirm that moving between CLI and GUI is straightforward?
 
Anything else that I should be thinking of right now?
 
Many thanks.

---

### Post by Dougie187 on 2009-07-22
> **Jumbo73 said:**
>  
Is the set of commands available on the CLI pretty much functionally equivalent to what I was used to?

Yes, you can always use man if you don't know how to use a specific command.
> **Jumbo73 said:**
>  
Will I need to run MS Office (Word, Excel) files through a processor to compare them to files created under ubuntu?

No, openoffice does a good job of converting them for you. Also, google has google docs which is free and online and can read office files as well. And Microsoft is supposed to be coming out with a competing program with a free version of office that is onine (though not as featurefull as the real office)
> **Jumbo73 said:**
>  
Can you confirm that moving between CLI and GUI is straightforward?

Yes.
> **Jumbo73 said:**
> 
Anything else that I should be thinking of right now?

No, unless you need some other functionality that you are not mentioning.

---

### Post by philcamlin on 2009-07-22
open office is way better then ms word

---

### Post by NightwishFan on 2009-07-22
In Ubuntu, you can use a terminal emulator on the graphical desktop. In the standard GNOME desktop you can even drag and drop files into the terminal emulator so I would say it is quite seamless.

As for office, Openoffice.org supports MSOffice files quite well. It can open and save to Word, Excel, Powerpoint.

As for the command line being similar, I recognize all the commands you mentioned, however I am not sure how **they** will work with msoffice files, if that is what you want.

---

### Post by Jumbo73 on 2009-07-22
Thanks all.
 
Most of my files are in MSWord - those are the ones that I need to work on.

---

### Post by SunnyRabbiera on 2009-07-22
> **Jumbo73 said:**
> Thanks all.
 
Most of my files are in MSWord - those are the ones that I need to work on.

.doc is well supported in Open Office

---

### Post by stalkier on 2009-07-22
> **SunnyRabbiera said:**
> .doc is well supported in Open Office

Agreed. I attended a college that required the use of Windows and MS Office. Being the sly dog I am I used Ubuntu and OpenOffice. Worked like a charm for me. They never once had problems opening files I submitted.

---

### Post by poosietgp on 2009-07-22
> **stalkier said:**
> Agreed. I attended a college that required the use of Windows and MS Office. Being the sly dog I am I used Ubuntu and OpenOffice. Worked like a charm for me. They never once had problems opening files I submitted.

There's a cafe near my college that use openoffice, never had problems submitting papers :) 

Some guys even thought they are just using MSOffice.

---

### Post by sneeks on 2009-07-22
iv'e used open office for a long time now,even before i went totally Linux,it converts with no problem matey,abiword is also a good alternative for a change too,this also converts well.use and enjoy

---

### Post by niteshifter on 2009-07-22
Hi,

> Will I need to run MS Office (Word, Excel) files through a processor to **compare** them to files created under ubuntu?


Taking the above as written: Yes. A .doc or .xls file from OOo, even though it is content equal to a MSO file will fail on byte-to-byte comparison. It's the metadata that does it in (paper, printer, fonts, etc.). For that matter, MSO files from different versions will fail simple binary comparison.

Here's the thing about OOo and MSO compatibility from a long time user of both and a freelance technical writer:

"Text Documents": As long as the document is of simple to moderate complexity of formatting and style features MSO won't have a problem with OOo exported docs and OOo won't have a problem with MSO docs. "Advanced" formatting / styles - things like footnotes, bibliographies, TOCs, TOAs, indices, and the like will likely require some cleanup or regeneration when moving from one to the other. Complex documents (embedded objects) will lose the linkage at a minimum, they may not carry over at at all. Depends upon the source software of the embedded object.

For spreadsheets, OOo's Calc and Excel match up on "core" functions, there are some differences in the more esoteric functions: array formulas, data pivots and with optional parameters to a function.

Database: OOo can read Access dbs. It's not compatible with Access forms.

Presentation: I'm no expert at this. I don't do PowerPoint / Impress unless I just absolutely have to (and I use Impress).

Math: OOo does math markup separate and it embeds cleanly into Writer and Impress, MSO does it in Word (and it sucks at it). For technical docs heavy on math check out Texmacs.

MSO and OOo documents of whatever kind are not macro compatible at all, the macros will require rewriting. Good news: BASIC is BASIC, the two dominant macro languages (MSO:VBA, OOo:OOo Basic) are keyword same. Bad news: The document object models are totally different.

---

### Post by Jumbo73 on 2009-07-24
Thanks Niteshifter and all -
 
I guess that the question now is where does one find these preprocessors if they are needed?
 
I'm hoping that won't be the case as I will mostly just need to diff older MS Word files against ones that I'll be generating in OOo.

---

