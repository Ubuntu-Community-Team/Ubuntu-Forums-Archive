---
title: "Word docs"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by patrik k on 2010-10-18
Cannot open Word docs imported from MS Office Word in my xp with Open Office.
Have no trouble opening and working with .xls spreadsheets un Open Office though.
Any suggestions?

---

### Post by Hippytaff on 2010-10-18
might they be docx files?

---

### Post by cavh on 2010-10-18
You might try with AbiWord, which I prefer to OpenOffice Write

---

### Post by Melon Bread on 2010-10-18
> **Hippytaff said:**
> might they be docx files?
If thats the case open them in word then save as .doc.

Or you could up them to Google docs and go form there

---

### Post by patrik k on 2010-10-18
No success with Abiword either.
I understand the formatting issues here but find it odd Open Office will allow me to work with .xls but not .doc
However, I have much to learn about Linux os.
So if I understand correctly, Open Office cannot open any .doc's?
Abiword just shuts off when I attempt to open the .doc's as does Open Office.

---

### Post by Hippytaff on 2010-10-18
> **patrik k said:**
> No success with Abiword either.
I understand the formatting issues here but find it odd Open Office will allow me to work with .xls but not .doc
However, I have much to learn about Linux os.
So if I understand correctly, Open Office cannot open any .doc's?
Abiword just shuts off when I attempt to open the .doc's as does Open Office.

can open doc files but not docx which is the 'new' doc format. microsoft being...um...innovative? so if thats the problem convert them by opening them in word save as and choose doc from the format drop down thing

---

### Post by patrik k on 2010-10-18
If only it was that simple Hippytaff.
No, they are not .docx extensions, .doc's
Hmmm.
Still looking.

---

### Post by Hippytaff on 2010-10-18
> **patrik k said:**
> If only it was that simple Hippytaff.
No, they are not .docx extensions, .doc's
Hmmm.
Still looking.

wishful thinking :-) sometimes it works out...

---

### Post by coffeecat on 2010-10-18
> **patrik k said:**
> No success with Abiword either.
I understand the formatting issues here but find it odd Open Office will allow me to work with .xls but not .doc
However, I have much to learn about Linux os.
So if I understand correctly, Open Office cannot open any .doc's?

I've not encountered problems opening .doc files with either Abiword or OpenOffice - except for occasional formatting issues. Since you can't open the files with Abiword either there may be something wrong with your Microsoft Word. It might be worth recruiting some friends and acquaintances to try your .doc files with other versions of Microsoft Word, with Open Office in Windows and in MacOS, with iWork Pages in MacOS and with any other word processors you can find that can open .doc files.

Why not attach a short .doc document that you can't open to your next post to let forum members have a go with whatever they've got?

> **Hippytaff said:**
> can open doc files but not docx which is the 'new' doc format.

Recent versions of Open Office can open .docx files but not save them.

---

### Post by Hippytaff on 2010-10-18
I keep learning new stuff :-)

> 
Recent versions of Open Office can open .docx files but not save them.


---

### Post by coffeecat on 2010-10-18
> **Hippytaff said:**
> I keep learning new stuff :-)

Support for docx was introduced with OO 3.0:

[http://www.openoffice.org/dev_docs/features/3.0/#Microsoft_Office_2007_Import_Filters](http://www.openoffice.org/dev_docs/features/3.0/#Microsoft_Office_2007_Import_Filters)

... but interestingly the features list for version 3.2:

[http://www.openoffice.org/dev_docs/features/3.2/#general_file](http://www.openoffice.org/dev_docs/features/3.2/#general_file)

... is still referring to Microsoft Word/Office 2007. Which makes me wonder if the OP is using Word 2010. I have no experience of Word 2010 (nor do I have any intention of so doing), but I wonder if MS have done another of their tricks in making the latest Word's .doc non-backwards-compatible.

---

### Post by Hippytaff on 2010-10-18
> 
 MS have done another of their tricks
wouldn't surprize me

just had a look and apparently 
[LEFT][COLOR=#000000]Microsoft Word 2010 uses the 

> 
.docx file extension to save documents



Read more:  [Microsoft Word 2010 File Extension]("http://www.word-2010.com/microsoft-word-2010-file-extension/#ixzz12kbPtbBc") [http://www.word-2010.com/microsoft-word-2010-file-extension/#ixzz12kbPtbBc](http://www.word-2010.com/microsoft-word-2010-file-extension/#ixzz12kbPtbBc) 
- all about Word 2010 [/COLOR][/LEFT]

---

### Post by patrik k on 2010-10-18
Getting a bit bizarre.
Went into my xp side, wrote the test doc.doc I have attached and saved to my external drive.
Closed out and opened Linux and imported test doc.
It WILL open with Open Office.
But .doc file that were imported during Ubuntu install will not.
Hmmm again.

---

### Post by patrik k on 2010-10-18
Think I have the reason.
Original .doc I was attempting to open was a Word Template.
Cannot open any of those files.
But any generic .doc opens fine w/ Open Office.
Still working.

---

### Post by coffeecat on 2010-10-19
> **patrik k said:**
> Think I have the reason.
Original .doc I was attempting to open was a Word Template.
Cannot open any of those files.
But any generic .doc opens fine w/ Open Office.
Still working.

But a document template would be a .dot, .dotm or .dotx file, wouldn't it? Open Office should be able to open them as well. Are you saying that OO wouldn't open a .dot/.dotx file or did you save a template as .doc?

---

### Post by HermanAB on 2010-10-19
Howdy,

I have encountered cases where clueless users will rename a file from .dox to .doc or whatever and then wonder why their wordprocessor goes gaga.

---

### Post by mastablasta on 2010-10-19
> **Hippytaff said:**
> wouldn't surprize me
just had a look and apparently 
[LEFT][COLOR=#000000]Microsoft Word 2010 uses the [/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]Read more: [Microsoft Word 2010 File Extension]("http://www.word-2010.com/microsoft-word-2010-file-extension/#ixzz12kbPtbBc") [http://www.word-2010.com/microsoft-word-2010-file-extension/#ixzz12kbPtbBc](http://www.word-2010.com/microsoft-word-2010-file-extension/#ixzz12kbPtbBc) [/COLOR][/LEFT]
 
[LEFT][COLOR=#000000]- all about Word 2010 [/COLOR][/LEFT]

 
 
what i don't undertstand (because i am not a programmer) is why is so hard to make open office to save or open docx? because docx is actually a zipped XML file.
 
change the ending of a .docx into .zip and you can unzip it and see exactly how the file is made.

---

### Post by Lakez on 2010-10-19
Even so if you change it to .zip that doesn't really solve the problem, the problem still exists. Even though I didn't face this problem with .docx on my OO

---

### Post by TNT1 on 2010-10-19
> **coffeecat said:**
> 



Recent versions of Open Office can open .docx files but not save them.

Weird. My Open Office 3.2 can open, save and create from scratch documents with the extra x... as in .xlsx, .docx, .pptx, and so on...  apt-get upgrade there, boys...

---

### Post by coffeecat on 2010-10-19
> **TNT1 said:**
> Weird. My Open Office 3.2 can open, save and create from scratch documents with the extra x... as in .xlsx, .docx, .pptx, and so on... 

You're quite right. I hadn't scrolled far enough down the file type list in save as. :oops:

All rather hypothetical for me as I save all my documents as .odt. :cool:

---

### Post by patrik k on 2010-10-19
Success.
Yes, the template was saved as a .doc by default.
Went into xp side, saved as .dot, transferred over and can open in OO.
Thank you to all who helped out.
"Clueless user?" 
Aren't we all at one time?
I guess if I was, I would not be here would I?
But, thanks again and am marking this solved.

---

