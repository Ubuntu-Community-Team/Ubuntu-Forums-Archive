---
title: "Pdf Converter?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Liko o Maui on 2009-04-05
Hi, I am just getting started with Ubuntu.  Can anyone tell me if there is a pdf conversion program either via Ubuntu, or campatable with Ubuntu?

I love the idea of shareware.  A schoolmate of mine became a huge proponent of shareware when the feds busted his company for having given other employees use of old computers/software when they bought new computers.

Instead of just contacting his company, they made front page news "busting" them, and costing him a hundred thousand in fines.  He is the least digitially interested person you ever met, but as a result he threw out everything MS, and replaced all his computers with non MS freeware.

He has become a spokesperson for the entire "free digital" world and says his business is run much more efficiently now that his employees are surfing the web during work hours! 

Mahalo!

---

### Post by s.fox on 2009-04-05
Hello and welcome to the forum.

What do you want to convert your pdf to?  

I know open office can handle PDFs and export in a fair few formats.

---

### Post by presence1960 on 2009-04-05
> **Liko o Maui said:**
> Hi, I am just getting started with Ubuntu.  Can anyone tell me if there is a pdf conversion program either via Ubuntu, or campatable with Ubuntu?

I love the idea of shareware.  A schoolmate of mine became a huge proponent of shareware when the feds busted his company for having given other employees use of old computers/software when they bought new computers.

Instead of just contacting his company, they made front page news "busting" them, and costing him a hundred thousand in fines.  He is the least digitially interested person you ever met, but as a result he threw out everything MS, and replaced all his computers with non MS freeware.

He has become a spokesperson for the entire "free digital" world and says his business is run much more efficiently now that his employees are surfing the web during work hours! 

Mahalo!

Shareware is for Windows  ](*,) Linux is open source, which means you can use it how you want, modify it if you want and on as many computers as you want. That = free.

:lolflag:

---

### Post by halitech on 2009-04-05
are you wanting to convert from pdf to another format or another format to pdf? if you want to create a pdf and the document is a plain text document in open office, simply use the export to pdf feature that is built into open office.

---

### Post by superzorro on 2009-04-05
Hi, welcome to Ubuntu

If want to convert different files to pdf, Ubuntu comes with a preinstalled PDF printer, you just have to print to this "printer" in any program and it will appear in a folder under your home folder with the name PDF /xxxx/PDF.

Also, if you want to scan something to PDF you can use either Xsane or gscan2pdf.

Good luck

---

### Post by llamabr on 2009-04-05
> **presence1960 said:**
> Shareware is for Windows  ](*,) Linux is open source, which means you can use it how you want, modify it if you want and on as many computers as you want. That = free.

:lolflag:

That's not entirely accurate, either.  Both closed source, and shareware, software run on linux.  Shareware is just one of many licenses that are available to protect software developers and users:

[http://en.wikipedia.org/wiki/Shareware](http://en.wikipedia.org/wiki/Shareware)

Back on subject, what do you want to convert your pdf's to?  Openoffice 3.0 has a plugin that allows editing of, and then export of, pdf's.

---

### Post by kevmitch on 2009-04-05
If you want to convert something from pdf you can use the convert command (this is a very powerful image processing tool)

On the command line you would use
```
convert file.pdf file.png
```
it automatically figures out what you want to convert from or to via the file extension. Just about any image format you can dream up is supported. 

If you're converting to and from postscript you can use ps2pdf and pdf2ps

```

ps2pdf file.ps file.pdf

```
```

pdf2ps file.pdf file.ps

```

Finally if you want to do something involving word processor documents, spreadsheets,etc I would recommend OpenOffice as it can both import and export pdf.

---

### Post by presence1960 on 2009-04-05
> **llamabr said:**
> That's not entirely accurate, either.  Both closed source, and shareware, software run on linux.  Shareware is just one of many licenses that are available to protect software developers and users:

[http://en.wikipedia.org/wiki/Shareware](http://en.wikipedia.org/wiki/Shareware)

Back on subject, what do you want to convert your pdf's to?  Openoffice 3.0 has a plugin that allows editing of, and then export of, pdf's.

not according to this : [http://en.wikipedia.org/wiki/Shareware](http://en.wikipedia.org/wiki/Shareware)

shareware is a free trial after which a fee must be paid for the license. Maybe it may run on Linux, maybe with wine- but it is not opensource. was trying to make a point that open source is for linux. Maybe I should have said "generally" shareware is for Windows. I am not aware of any shareware in the repositories, at least I have never had a trial after which a fee is due to use the software.

---

### Post by llamabr on 2009-04-05
> **presence1960 said:**
> not according to this : [http://en.wikipedia.org/wiki/Shareware](http://en.wikipedia.org/wiki/Shareware)

shareware is a free trial after which a fee must be paid for the license. Maybe it may run on Linux, maybe with wine- but it is not opensource. was trying to make a point that open source is for linux. Maybe I should have said "generally" shareware is for Windows. I am not aware of any shareware in the repositories, at least I have never had a trial after which a fee is due to use the software.

Sorry.  That you've never done it isn't evidence that it can't be done.  From that same page you quote:

> Shareware is available on all major computer platforms including Microsoft Windows, Macintosh, Linux, and Unix. Titles cover a very wide range of categories including: business, software development, education, home, multimedia, design, drivers, games, and utilities.

As I said, shareware is just one of many licenses that is available to software developers to protect their work.  A software developer can write code for any platform, and protect it with any license he/she likes.

Though you are correct, you won't find any in the standard repositories that comes with your distribution.

---

### Post by presence1960 on 2009-04-05
> **llamabr said:**
> Sorry.  That you've never done it isn't evidence that it can't be done.  From that same page you quote:



As I said, shareware is just one of many licenses that is available to software developers to protect their work.  A software developer can write code for any platform, and protect it with any license he/she likes.

Though you are correct, you won't find any in the standard repositories that comes with your distribution.

Thanks for the info, I learn something every day. Today it was from you!
That's one of the reasons I love this community so much. It's helping my knowledge increase.

---

### Post by asmoore82 on 2009-04-05
Might I suggest using the term "Free Software." [http://www.fsf.org/licensing/essays/free-sw.html](http://www.fsf.org/licensing/essays/free-sw.html)

To the OP, Welcome, you've taken your first step into a larger world.

"Everybody falls the first time."

---

### Post by llamabr on 2009-04-05
> **asmoore82 said:**
> Might I suggest using the term "Free Software." [http://www.fsf.org/licensing/essays/free-sw.html](http://www.fsf.org/licensing/essays/free-sw.html)


Most of the software that runs on your ubuntu system is free as in beer, and free as in speech.  But software that's not free runs on your ubuntu system, too.  Software that's neither free as in speech, nor free as in beer.

---

### Post by Liko o Maui on 2009-04-05
Thanks for everyone's responses.

Yes, I was looking for the ability to take normals docs and convert them to pdf format to email as an attachment.

Sorry about the sloppy nomenclature, yes, he converted to open source systems.  His name is Sterling Ball, and he is the owner of Ernie Ball Guitar Strings.   If you search his name you'll get his story.  Probably the biggest promoter of open source who doesn't know anything about programming! 

And the last line on my original post had an error.  It should have read "his business is more profitable and efficient because now he doesn't have employees surfing the web when they should be doing accounting (orders etc..).  They only have the programs they need to execute their job, not the windows potpourri.

Thanks to all again, aloha!

---

### Post by superzorro on 2009-04-07
I'm glad you problem worked out.

Always remember to mark the thread as solved when it is.

---

### Post by egalvan on 2009-04-07
> **Liko o Maui said:**
> T His name is Sterling Ball, and he is the owner of **Ernie Ball Guitar Strings.   **If you search his name you'll get his story.  Probably the biggest promoter of open source who doesn't know anything about programming! 


Excellent banjo strings. Best I've tried.

Good to hear he's on the OSS/FOSS bandwagon.

And as for almost all software for Linux being open sourse/no cost...
do remember that some software authors wouldn't mind a donation...
I've donated to several authors whose software I use on a regular basis... such as PartedMagic.

TANSTAAFL

"Don't forget to tip your software authors"

ErnestG

---

