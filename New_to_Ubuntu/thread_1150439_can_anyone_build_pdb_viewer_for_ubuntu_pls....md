---
title: "can anyone build pdb viewer for ubuntu pls..."
date: 2009-05-06
forum: New to Ubuntu
---

### Post by manuvaidya on 2009-05-06
hi guys, i am really upset with this issue. we have lot of alternative softwares compared to windows in ubuntu,,,, but when it comes to the pdb viewer, linux is lagging behind from windows. atleast anyone build a simple software to open a pdb files.... i have a lot of text books in pdb format, i am very much annoyed to use windows just to read books in pdb format...

i am requesting all of u guys to give a simple pdb viewing software..... i am a ubuntu newbie... i dont know how to build it... thats why i am requesting all of u guys..... pls....

---

### Post by loell on 2009-05-06
protien data bank viewer!?

---

### Post by nhasian on 2009-05-06
pdb is for palm pilot ebooks.

a quick check on google didnt reveal anything either for me.

---

### Post by loell on 2009-05-06
ah.. for palm..  LOL

you can use **pyrite-publisher** to convert it to text and from there probably convert the text to pdf.

---

### Post by manuvaidya on 2009-05-06
what do i do now????? i am desperate to use these books in pdb format.... i dont wanna go back to windows just for this one reason....

why no one has built a software to view pdb files in ubuntu???? nobody with ubuntu uses palmtop devices/ pdb files???? very strange.... come on guys.... no isilo alternative in ubuntu???? i am begging u people to build a software alternative to isilo pls....

---

### Post by loell on 2009-05-06
or actually use **abiword**

---

### Post by manuvaidya on 2009-05-06
> **loell said:**
> ah.. for palm..  LOL

you can use **pyrite-publisher** to convert it to text and from there probably convert the text to pdf.
hi loell, i installed it from synaptics packet manager... but its not launching from terminal/ its not present in office group... how do i launch it/ use it????

simple guide will be appreciated much... pls...

---

### Post by kingswood71 on 2009-05-07
yeah I have encountered the same issue... I am overcoming it by:
1. opening up the pdb book in isilo using wine.
2. coping entire document.
3. pasting it to open office word doc.
4. exporting from there as a pdf

seems to work, but a lot of rooting around!!
Anyone find a good pdb reader native to linux/ubuntu..let me know!!

---

### Post by oliwek on 2009-05-20
hello kingswood71,
I've tried to use [iSilo&#8482; 5.06 for Windows]("http://www.isilo.com/download/iSiloW32.htm") but couldn't get anything readable from it ;

with this free pdb ebook for example : [http://www.ebooksgratuits.com/newsendbook.php?id=139&format=pr](http://www.ebooksgratuits.com/newsendbook.php?id=139&format=pr)

I get this result :

[IMG]http://img200.imageshack.us/img200/2041/isilopdb.png[/IMG]

any advice?


> **loell said:**
> or actually use **abiword**

abiword can't open this kind of file


edit : I had to use [eReader Pro for Windows]("http://www.ereader.com/ereader/softw...09_pro_win.htm") in wine 

[[IMG]http://img211.imageshack.us/img211/8397/ereader.th.png[/IMG]](http://img211.imageshack.us/my.php?image=ereader.png)

---

### Post by chitowner2 on 2009-09-14
This topic is of interest to me also. I just spent the last several hours trying the following *possibilities*:

abiword- doesn't work on .pdb files. just hangs; my cpu usage goes >90% and I have to reboot to get out of it.

PDBEditor- can't figure how to get it to work. Extracted the files from a .jar archive, but find no executable. 

kpalmdoc- also a loser. does nothing.

FBReader- kinda doubt it will work. Most sources discussing it say it only works on "some" pdb files.

iSilo + WINE ? Oh come ON guys! Can't we get something native to Debian?

DISCUSSION WELCOME!

---

### Post by chitowner2 on 2009-09-14
>> Tested FBReader. I have ~40 .pdb titles; FBReader only found *one* and displayed open text mixed with non-alpha characters.

---

### Post by Excedio on 2009-09-14
> **manuvaidya said:**
> what do i do now????? i am desperate to use these books in pdb format.... i dont wanna go back to windows just for this one reason....

why no one has built a software to view pdb files in ubuntu???? nobody with ubuntu uses palmtop devices/ pdb files???? very strange.... come on guys.... no isilo alternative in ubuntu???? i am begging u people to build a software alternative to isilo pls....


Do you really think that it's as simple as "just make a program?" Not everyone here is a programmer, and those that are, may not have a need for this type of program thus do not make one. I do understand your frustrations, but still .....relax.

---

### Post by Excedio on 2009-09-14
This thread may be useful.

[http://ubuntuforums.org/showthread.php?t=270133](http://ubuntuforums.org/showthread.php?t=270133)

---

### Post by chitowner2 on 2009-09-14
> **Excedio said:**
> This thread may be useful.

[http://ubuntuforums.org/showthread.php?t=270133](http://ubuntuforums.org/showthread.php?t=270133)

Ya, I tried that one too. Couldn't it to work at all. Command would not run from Alt+f2 or shell:

~$ guipdb
bash: /usr/local/bin/guipdb: Permission denied

---

### Post by Jive Turkey on 2009-09-14
> **chitowner2 said:**
> Ya, I tried that one too. Couldn't it to work at all. Command would not run from Alt+f2 or shell:

~$ guipdb
bash: /usr/local/bin/guipdb: Permission denied

```
sudo guipdb
```???
just a thought, though a document reader should not require sudo AT ALL, it may be just a bug that you even need it I dunno. PDB could stand for a few different things though.  I think one of the "pdb" related programs mentioned so far was for designing circuitboards, not reading documents.

---

### Post by cariboo on 2009-09-14
Have a look at calibre, an ebook manager. It is available for Jaunty and Karmic, It will convert from other formats, manage your library, up load to devices and more. Calbre is in the repositories.

---

### Post by roger_1960 on 2009-09-14
Hi

Ereader software [www.ereader.com](www.ereader.com) runs fine under wine.

---

### Post by I WILL DO IT on 2009-09-14
you should try and install some wine weaks

---

### Post by t0p on 2009-09-14
> **manuvaidya said:**
> what do i do now????? i am desperate to use these books in pdb format.... i dont wanna go back to windows just for this one reason....

why no one has built a software to view pdb files in ubuntu???? nobody with ubuntu uses palmtop devices/ pdb files???? very strange.... come on guys.... no isilo alternative in ubuntu???? i am begging u people to build a software alternative to isilo pls....

Why don't *you* write isilo for linux?  It's your itch, *you* scratch it.

---

### Post by niteshifter on 2009-09-14
Hi,

> why no one has built a software to view pdb files in ubuntu????
nobody with ubuntu uses palmtop devices/ pdb files???? very strange.... come on guys.... no isilo alternative in ubuntu???? i am begging u people to build a software alternative to isilo pls....

I use a Palm TX w/ ubuntu daily. I just didn't fall for the plucker db universal reader line of bull. Mainly because - as you've just discovered - it's not so universal.

Use PDFs, friend. Get PalmPDF from [here]("http://metaviewsoft.de/"). Based upon Xpdf, it beats the crap out of the "toy" PDF reader Palm supplied you.

Next, reacquire what ebooks you have in .pdb as .pdf files. Most free ebooks are available as both. Those you can't reacquire do as kingswood71 suggested - copy and paste, make your own .pdf file.

PDF is truly universal and you're using an OS that can let you do pretty much anything with a pdf file once you've installed the tools you need (most of which you already have).

Now, as to writing a viewer - as another poster already put it "scratch your own itch". I'm busy writing one to scratch mine: an app that gives a GUI front end for these tools: pdftk, pdftotext, pdfinfo, pdfimages, pdffonts, pdftops, gv (pdf2ps) and a few more. But it's slow going - that paying job of mine keeps eating time. My wife would occasionally like to see me also ;)

Point is, as the other poster and I are trying to make is a goodly amount of the software in FOSS comes from people working to fix their own problems. That's not to knock corporate sponsored work (which has been a huge help) but rather to point out it's free-market approach. So, if you have programming skills - get to work. If you don't that's fine as well. Just have a little patience - and hope for a bit of luck that some dev with spare time will undertake the task.

But I've got to say that honestly I think you'll be waiting a long time. PalmOS is dead. The new Palm programming paradigm (WebOS) doesn't seem to be looking back much. Hence my advice to move to PDF.

---

### Post by chitowner2 on 2009-09-24
I installed calibre from the repos. It sees PDF's just fine, but none of the PDB files, so that's a dud.

Converting the PDB's to PDF's would frst require being able to open and read those files. But if I/we could do that, then what would a PDF reader be needed for? Duh!

:(

---

### Post by peterthinking on 2009-09-24
gotta be a palm emulator somewhere.
Pretty sure with the palm desktop you could read palm files....still got a disk?

---

### Post by peterthinking on 2009-09-24
[http://kb.palm.com/wps/portal/kb/common/article/33529_en.html](http://kb.palm.com/wps/portal/kb/common/article/33529_en.html)

to download palm desktops.

[http://3d2f.com/programs/27-289-gemini-download.shtml](http://3d2f.com/programs/27-289-gemini-download.shtml)

Some program that can convert palm files...never heard of it but a quick google found it.

[http://www.netmeister.org/palm/POSE/POSE-HOWTO.html](http://www.netmeister.org/palm/POSE/POSE-HOWTO.html)

a thing on palm desktop emulator software

[http://www.giveawayoftheday.com/freeware/palm/emulator](http://www.giveawayoftheday.com/freeware/palm/emulator)

and partway down this page something called "Palm Desktop Utilities" sounds like it could save your stuff.

I didn't check what OS they ran on...probably Windows but if you just wanna save some files it's easy enough to get your hands on one. I hear Windows was quite popular in it's day. You can probably get a copy of Windows at surplusscomputers or tiger direct, they sometimes sell older legacy software pretty cheap.

---

### Post by superJoel on 2009-12-11
calibre does work for .pdb files, but not ones with DRM... you just have to go out to the website and install the newest version

---

### Post by crimius on 2010-01-18
To update this:  you can install eReader Pro under WINE, and it should be able to read the B&N .pdb ebooks just fine.  download the .zip and extract the setup.exe file, then run it with wine.
URL to download zip file:
```
http://www.ereader.com/ereader/software/product/15009_pro_win.htm
```

```
wine setup.exe
```

---

### Post by JEREMIAHBARLOW on 2010-03-29
I love Ubuntu 9.10 ... I have tried all the major linux flavors off and on over the year. Never having the time to make the learning curve all the way.  But this time when my Windows Vista pooped out on me, I chose Ubuntu.  So I am somewhat new to Linux but really impressed with what I have going now.  

**I just loaded up my iSilo 5.05 and Wine just loads it and runs it fine. My files all pull up fine with the right fonts, etc.  **

I love Ubuntu 9.10 ,,, 
cool, cool, cool!   

That is after I did some internet sharing with my Verizon 959 Air Card (now that could be made easier, but there is a lot of help online for Internet Connection Sharing)

:D

---

### Post by daveshep on 2010-04-25
hey thanks for the tip about calibre, i just used it to convert a .pdf to an .epub for my eslick reader. sweet as. nice work.

although there's a couple of funny things about the epub file, eg "Los ngeles" instead of Los Angeles...

---

### Post by dnprastowo on 2011-08-18
with crossover add this archive :[http://hotfile.com/dl/127163521/08b06e9/isilo.cxarchive.html](http://hotfile.com/dl/127163521/08b06e9/isilo.cxarchive.html) already activated

---

