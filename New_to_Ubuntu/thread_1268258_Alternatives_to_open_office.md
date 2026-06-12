---
title: "Alternatives to open office"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-09-16
Ok, so after days of struggling to fix the problems I'm having with open office, I give up. What alternatives are out there, and are they any good? I've heard of Abiword, but I've heard it's worse than open office. Any advice?

---

### Post by astrakhan on 2009-09-16
what problems are you having? i haven't found anything that i'd rather use instead of openoffice.
IMO abiword, although a fine program, isn't as extensive.

---

### Post by natravis on 2009-09-16
Abiword is a smaller footprint word processor similar to WordPad in Windows, or a less featured (at least from a "default" view) version of OpenOffice writer. I haven't heard of any problems with it.

Kate is another, but I don't think that would be the right way for you to go. 

What issues are you having with OpenOffice? Perhaps we can help with that to solve the problem rather than going to an alternative.

---

### Post by rahrahmah on 2009-09-16
Well, I can't figure out the spell check, which after a look around the web seems to be a pretty common problem. I'm not sure if there is a solution (other than having to constantly use an outside source of validation), since the steps I took (installing the canadian dictionary and making sure all the settings were for it) was the only advice to solve the problem I could find at the open office site, and that didn't work (despite the fact that I seem to have done it properly). I also can't open .docx files.. This doesn't matter whether it's being opened to the tmp folder from a website, or if I save the file and try to open it from the home directory. the little package I downloaded that claimed to be a program to allow this looks like it was a file for something totally different, and I shouldn't need it anyway since I'm working from 3.1 which seems to open these files for everyone else.

These are big problems for me, since I'm in college right now, and not only to I have to type perfectly spelled assignments, I also have to submit them online and read other people's online. Many of them just bought shiny new laptops with Vista and a large percent of what's getting posted is in the .docx format.

---

### Post by Chronon on 2009-09-16
Maybe talk to the teacher and see if s/he will agree that a standard (open) format would be better for class communication.  It seems to me that if the purpose is for people to prepare documents for other people to read then everyone should prepare PDFs.  There are free PDF export utilities available for Windows and obviously OSX and linux can print to PDF.

Sorry, I don't really use Open Office, so I can't help you on that.  KOffice is an office suite for KDE but I don't have experience with that either -- certainly not with its Microsoft document importing abilities.

---

### Post by Viva on 2009-09-16
If your problem is MS Word compatibility, then there is no solution other than installing Microsoft Word using wine or virtualbox.

---

### Post by LowSky on 2009-09-16
What version of openoffice are you using?

---

### Post by 73ckn797 on 2009-09-16
> **Viva said:**
> If your problem is MS Word compatibility, then there is no solution other than installing Microsoft Word using wine or virtualbox.


I have used MS office 97 with no problems in Wine before. I know it is old. I believe Office XP will work also.

As already asked, What version OO are you using? The included version with Ubuntu or their latest package from OO?

---

### Post by Temposs on 2009-09-16
For spellcheck, there are two buttons for it on the main toolbar. They both have "ABC" with a check underneath. This is the default setup for the version of OpenOffice that comes with Ubuntu 9.04. 

I personally have been able to open docx files. Maybe you can post an example of a docx file that you can't seem to open?

---

### Post by starcannon on 2009-09-16
Install MS Office 2007 using Wine; I use MS Word all the time using this method. 
Heres the Icon on the desktop:
[[IMG]http://img42.imageshack.us/img42/9591/wordicon.th.png[/IMG]]("http://img42.imageshack.us/i/wordicon.png/")
And heres MS Word running on my Ubuntu desktop.
[[IMG]http://img156.imageshack.us/img156/4796/wordrunning.th.png[/IMG]]("http://img156.imageshack.us/i/wordrunning.png/")

GL and HF

---

### Post by rahrahmah on 2009-09-16
As I said, I'm using 3.1. And yes, I know what a spell check IS. The problem is it doesn't work. It doesn't recognize even the most obvious of spelling errors. I can flail on the keyboard like so: sldkjfldkjf and it won't pick up on it. 

I guess I'll have to try and figure out WINE. Thanks for the advice.

---

### Post by corncob on 2009-09-16
> **Temposs said:**
> For spellcheck, there are two buttons for it on the main toolbar. They both have "ABC" with a check underneath. This is the default setup for the version of OpenOffice that comes with Ubuntu 9.04. 


Why are there two spell check buttons?  Only one appears to work on my installation.  Actually, I don't use them anyway; when a word is red lined I right click on it and that gives me a dropdown list of possible substitutes.

---

### Post by superzorro on 2009-09-16
Well, I also use Openoffice and Office through Wine.

However, Openoffice is a great app. You can open office 2007 (docx, pptx, xlsx) files.

As for the language and grammar correction. I also had a bit of trouble. And the best results I have had are using the US English dictionary, and for other languages the "main" country dictionary. Using local variants is a hit or miss for me.

As for the grammar and other improvements, such as templates, check out the extensions webpage at Openoffice.org:

[http://extensions.services.openoffice.org/]("http://extensions.services.openoffice.org/")

There you can find Language Tool. It is an extension that adds grammar check.

Also here is a blog entry with some extensions for Openoffice:

[http://maketecheasier.com/12-must-have-openoffice-extensions/2008/02/11]("http://maketecheasier.com/12-must-have-openoffice-extensions/2008/02/11")

Good luck

---

### Post by morningcrafter on 2009-09-21
[rahrahmah]("http://ubuntuforums.org/member.php?u=880813"): I don't know if you've solved this problem since posting this dilemma, but I've had a similar if not identical problem and am also in college typing papers that if not grammatically correct, can undermine the integrity of my writing. 

I doubt you want to use MS Word, and I don't blame you. So here are the work arounds I've found in Open Office 3.0:

I've found with 3.0 (even my glitchy install) that you can open .docx files just fine, but that it helps to save them afterward as .odf files for editing. People using Windows Vista and that fancy new MS Word can open doc files since it is backwards compatible. So when you're sending files to your professors or fellow students, try saving them as .odf files for your editing purposes and sending the finalized versions as a newly saved .doc files. This should make everyone happy.

As for the spellcheck issue (which was a huge hassle for me last night, in fact) I would double check your language settings as explained[COLOR=Red] [here]("http://www.8daysaweek.co.uk/forums/viewtopic.php?t=758")[/COLOR] . . . Mine was somehow set in Czech! 

If that still doesn't work, the repositories and extensions listed [COLOR=Red][here]("http://extensions.services.openoffice.org/dictionary")[/COLOR] were a *huge* help.

I hope this solves your problems, if they still persisted!

---

### Post by A_M_S on 2009-09-21
I use office 2007 in virtual box with no problems.

---

### Post by 73ckn797 on 2009-09-21
> **rahrahmah said:**
> As I said, I'm using 3.1. And yes, I know what a spell check IS. The problem is it doesn't work. It doesn't recognize even the most obvious of spelling errors. I can flail on the keyboard like so: sldkjfldkjf and it won't pick up on it. 

I guess I'll have to try and figure out WINE. Thanks for the advice.


I have OO 3.0.1 which comes with Ubuntu. Version 3.1.1 is available on the OO site. You stated you have 3.1 so I assume you have installed it instead of the packaged version?

---

### Post by RedRat on 2009-09-21
> **corncob said:**
> Why are there two spell check buttons?  Only one appears to work on my installation.  Actually, I don't use them anyway; when a word is red lined I right click on it and that gives me a dropdown list of possible substitutes.

There are two buttons that are identical. One button, the first one, is to call Spelling and Grammer, the second button is to turn on autospellcheck. That is depressed by default.

---

### Post by jamesman on 2009-09-21
Lotus Symphony is available as a free download from IBM
[http://symphony.lotus.com/software/lotus/symphony/home.nsf/home](http://symphony.lotus.com/software/lotus/symphony/home.nsf/home)
It works on Linux, Windows, and Mac

---

### Post by stinger30au on 2009-09-22
all you need to know about open office dictionary on version 3 like whats in 9.04

[http://wiki.services.openoffice.org/wiki/Dictionaries](http://wiki.services.openoffice.org/wiki/Dictionaries)

---

### Post by corncob on 2009-09-22
> **RedRat said:**
> There are two buttons that are identical. One button, the first one, is to call Spelling and Grammer, the second button is to turn on autospellcheck. That is depressed by default.

Did you hear that, rahrahmah?  Could your problem with the spell checker be that your second button isn't depressed?

---

