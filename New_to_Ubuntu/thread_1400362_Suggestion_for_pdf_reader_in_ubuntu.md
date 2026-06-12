---
title: "Suggestion for pdf reader in ubuntu"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Isyaltut on 2010-02-06
[FONT=Lucida Grande][SIZE=2]Hi, I've been using ubuntu karmic exclusively for a few days now. While the choice of software that ubuntu has is really great, I still wondering why there is no good pdf reader out there (that i'm aware of).?[/SIZE][/FONT]
  [FONT=Lucida Grande][SIZE=2]I mainly use pdf reader for viewing pdf file (what else[/SIZE][/FONT][FONT=Lucida Grande][SIZE=2]?[/SIZE][/FONT]:wink:[FONT=Lucida Grande][SIZE=2]), and some annotating capabilities like highlighting text, add bookmark, and add comments and notes. I need those features because i'm a student and have to read my textbook in pdf format. [/SIZE][/FONT] 
  [FONT=Lucida Grande][SIZE=2]Back in the Windows day, I use foxit reader and pretty satisfied with it. But in linux version that i've tried, it missing the features that I mention above. I've tried other pdf reader; evince (installed by default, but has very limited capabilities), kpdf, xpdf, and okular. I read about adobe reader available in linux, but I won't install those bloated crapware in my old windows, let alone ubuntu. The closest thing pdf reader that met my requierement is okular, but it has funny behavior when I tried to read in full screen. It displays only one page, and the zoomed to best fit. I tried to look around and there is no preference/settings that can change those behavior because I want to read in full screen and zoom the documents. 
[/SIZE][/FONT]
[FONT=Lucida Grande][SIZE=2]So, 					are there any suggestions for me? Or that okular can be 					configured in full screen? I know that it seems like a little 					problem, but it can be really frustating for not be able to find 					software that doesn't meet your needs. [/SIZE][/FONT]

---

### Post by durand on 2010-02-06
You could run foxit in wine. I really liked foxit when I used windows.

Wine is a windows compatibility layer for linux so it allows you to run windows programs on ubuntu. If you install wine (search for it in the software center), and then download and run the windows version of foxit, you should be able to use it quite well.

---

### Post by s3a on 2010-02-06
Get xournal through synaptic or open a terminal and do:

sudo apt-get install xournal

P.S.
There are other programs such as jarnal that do the same job.

---

### Post by Temposs on 2010-02-06
Not to be unhelpful, but pdf is not meant as an editable document. pdf was designed as a document format for viewing and printing ONLY. The annotation and form filling and other such features are wretched hacks, in my opinion. Ubuntu does this part extraordinarily well.

If you absolutely need those peripheral features for pdf, I would recommend to just install the Adobe Acrobat Reader(I know you said you don't like it), as it's going to give you the best behavior for those features. 

There isn't a perfect alternative for Linux because geeks tend to know that pdf is made for viewing, and thus use it that way and don't have an interest in perpetuating the hackish features that Adobe is profligating in the pdf format in order to make more money for itself.

If you have a choice, I'd recommend you use a proper editing format, like odf, doc, txt, rdf, tex, etc.

---

### Post by samantha_ on 2010-02-06
> **Isyaltut said:**
> [FONT=Lucida Grande][SIZE=2]Hi, I've been using ubuntu karmic exclusively for a few days now. While the choice of software that ubuntu has is really great, I still wondering why there is no good pdf reader out there (that i'm aware of).?[/SIZE][/FONT]
  [FONT=Lucida Grande][SIZE=2]I mainly use pdf reader for viewing pdf file (what else[/SIZE][/FONT][FONT=Lucida Grande][SIZE=2]?[/SIZE][/FONT]:wink:[FONT=Lucida Grande][SIZE=2]), and some annotating capabilities like highlighting text, add bookmark, and add comments and notes. I need those features because i'm a student and have to read my textbook in pdf format. [/SIZE][/FONT] 
  [FONT=Lucida Grande][SIZE=2]Back in the Windows day, I use foxit reader and pretty satisfied with it. But in linux version that i've tried, it missing the features that I mention above. I've tried other pdf reader; evince (installed by default, but has very limited capabilities), kpdf, xpdf, and okular. I read about adobe reader available in linux, but I won't install those bloated crapware in my old windows, let alone ubuntu. The closest thing pdf reader that met my requierement is okular, but it has funny behavior when I tried to read in full screen. It displays only one page, and the zoomed to best fit. I tried to look around and there is no preference/settings that can change those behavior because I want to read in full screen and zoom the documents. 
[/SIZE][/FONT]
[FONT=Lucida Grande][SIZE=2]So, 					are there any suggestions for me? Or that okular can be 					configured in full screen? I know that it seems like a little 					problem, but it can be really frustating for not be able to find 					software that doesn't meet your needs. [/SIZE][/FONT]

Open the pdf in openoffice.
Save it as a doc or odf.
kapow. done.

---

### Post by mechro on 2010-02-06
There's a Foxit Reader .deb package available here...

[http://www.foxitsoftware.com/pdf/desklinux/download.html](http://www.foxitsoftware.com/pdf/desklinux/download.html)

I've just downloaded and installed it myself and it works fine.


Edit... er... OK... maybe doesn't fit all your requirements :oops:

---

### Post by zerubbabel on 2010-02-06
PDF Xchange Viewer is hard to beat, and runs very well under Wine. 
[http://www.docu-track.com/](http://www.docu-track.com/)

---

### Post by Isyaltut on 2010-02-06
> **Temposs said:**
> Not to be unhelpful, but pdf is not meant as an editable document. pdf was designed as a document format for viewing and printing ONLY. The annotation and form filling and other such features are wretched hacks, in my opinion. Ubuntu does this part extraordinarily well.

If you absolutely need those peripheral features for pdf, I would recommend to just install the Adobe Acrobat Reader(I know you said you don't like it), as it's going to give you the best behavior for those features. 

There isn't a perfect alternative for Linux because geeks tend to know that pdf is made for viewing, and thus use it that way and don't have an interest in perpetuating the hackish features that Adobe is profligating in the pdf format in order to make more money for itself.

If you have a choice, I'd recommend you use a proper editing format, like odf, doc, txt, rdf, tex, etc.

I know that pdf files are intended to be permanent, but i got my textbook as scanned pdf, and it's hard to convert to proper editable format such as odf. I like to think that my pdf as a physical book, and that i can add my notes in there, put a bookmark, etc. It isn't the kind of thing that will change the main contents of the file.

> Open the pdf in openoffice.
Save it as a doc or odf.
kapow. done. 	

I didn't know that OO can open pdf files. But i tried to open my pdf file with OO, there is nothing happened. It just start blank.

Anyway thanks for the suggestions, i'm using foxit in wine now, and so far so good.

Cheers.

---

### Post by samantha_ on 2010-02-06
> **Isyaltut said:**
> I know that pdf files are intended to be permanent, but i got my textbook as scanned pdf, and it's hard to convert to proper editable format such as odf. I like to think that my pdf as a physical book, and that i can add my notes in there, put a bookmark, etc. It isn't the kind of thing that will change the main contents of the file.



I didn't know that OO can open pdf files. But i tried to open my pdf file with OO, there is nothing happened. It just start blank.

Anyway thanks for the suggestions, i'm using foxit in wine now, and so far so good.

Cheers.

hmm. weird.
mine works....

wait. hang on a moment.

I know why it doesnt work.
I installed this extension: [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

to make it work. However, i forgot about it and just took it working for granted :)

---

### Post by pararoly on 2010-02-06
Hello [Isyaltut]("http://ubuntuforums.org/member.php?u=1012711")

Could you not just buy a copy of the proper (paper) text book?

Best Wishes
Roly

---

### Post by samantha_ on 2010-02-06
> **pararoly said:**
> Hello [Isyaltut]("http://ubuntuforums.org/member.php?u=1012711")

Could you not just buy a copy of the proper (paper) text book?

Best Wishes
Roly

its cheaper + you instantly get the pdf book instead of waiting days/weeks for it.

---

### Post by Orion8 on 2010-02-06
I've had no trouble with the latest adobe reader.  It may have been bloated at one time but my impression is this is not the case any more. Give it a shot and see what you think -- worst case just remove it if you hate it.  In any case, I have no trouble with Adobe these days and switch back and forth between Evince and Adobe Reader depending on what I am doing.

---

### Post by Isyaltut on 2010-02-06
> **pararoly said:**
> Hello [Isyaltut]("http://ubuntuforums.org/member.php?u=1012711")

Could you not just buy a copy of the proper (paper) text book?


Well, that brings up another problem isn't it? I don't really wanna bring my big, heavy, and overpriced textbook to school everyday anymore. My old laptop is Acer Aspire 4710, and that isn't really compact laptop to brought everyday in my backpack. And now i just got a new laptop (actually it is an old one, my father just gave it to me) Fujitsu Esprimo Mobile U 9200, and it is pretty light and compact:grin:. So now i want to use this laptop on everyday basis in school.

---

### Post by s3a on 2010-02-06
Use xournal. And I feel your pain because I go through it myself ;).

---

### Post by DZ* on 2010-02-06
> **Isyaltut said:**
> [FONT=Lucida Grande][SIZE=2]I read about adobe reader available in linux, but I won't install those bloated crapware in my old windows, let alone ubuntu. The closest thing pdf reader that met my requierement is okular, but it has funny behavior when I tried to read in full screen. It displays only one page, and the zoomed to best fit.[/SIZE][/FONT]

By full screen, do you mean "presentation mode" or a maximized window? If later is the case, you can use "Ctrl -", "Ctrl +" to zoom in and out, and "continuous" option under "View" menu. There is also an option to see multiple pages there. BTW, if you copy a file annotated by okular to a different drive, you'll lose annotations. To make them stick, use File -> Export_as -> Document_archive.

Also, Adobe Reader doesn't provide any editing or annotation beyond a simple form filling.

---

### Post by DZ* on 2010-02-06
> **samantha_ said:**
> hmm. weird.
mine works....

wait. hang on a moment.

I know why it doesnt work.
I installed this extension: [http://extensions.services.openoffice.org/project/pdfimport](http://extensions.services.openoffice.org/project/pdfimport)

to make it work. However, i forgot about it and just took it working for granted :)


I was intrigued and installed the extension. I cannot open PDFs with OpenOffice (writer?). I'm getting a "General error" box...

---

### Post by samantha_ on 2010-02-06
> **DZ* said:**
> I was intrigued and installed the extension. I cannot open PDFs with OpenOffice (writer?). I'm getting a "General error" box...

works for me... (which is normally what we say here when something doesnt work on someone elses machine.....)
what version are you using?

---

### Post by DZ* on 2010-02-06
> **samantha_ said:**
> works for me... (which is normally what we say here when something doesnt work on someone elses machine.....)
what version are you using?

9.10 with all updates applied. Ok, I can open some files with OO Writer. It seems to choke on PDFs produced by LaTeX (pdflatex).

---

### Post by dolphinaura on 2010-02-06
> **DZ* said:**
> 9.10 with all updates applied. Ok, I can open some files with OO Writer. It seems to choke on PDFs produced by LaTeX (pdflatex).

thats cause openoffice by default doesnt support LaTeX.
Youll need to install [http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/)

---

### Post by DZ* on 2010-02-07
> **dolphinaura said:**
> thats cause openoffice by default doesnt support LaTeX.
Youll need to install [http://ooolatex.sourceforge.net/](http://ooolatex.sourceforge.net/)

It's not that. 

I do have installed and use ooolatex extensively.

---

### Post by mechro on 2010-02-07
> **s3a said:**
> Use xournal...

Cool! :D

+1 for xournal.

---

### Post by ugujjwal on 2010-02-15
xournal seems really good...
Lets see how it behaves in the long run...  :)

---

### Post by canislupus360 on 2010-03-21
Another option is to use Mendeley.  It is a nice pdf organizer in which you can also highlight and annotate.  It works well for me.

---

