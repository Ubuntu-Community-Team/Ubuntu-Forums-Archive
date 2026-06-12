---
title: "Is there an alternative format to RAR that has survive some data corruption?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by learningcurb on 2009-06-20
I just had an experience where I tried to unzip a .tar archive that had been damaged somehow.  It seems even very minor damage to an archive will make large chunks of it impossible to extract normally.

This makes me want to use a different archive format for my archived documents. They are mostly large bunches of small text and document files and scanned documents. I could just leave them in single files, but then it takes forever to back them up or move them to a USB drive.

I know that RAR archives support parity files which allow you to repair damaged archives. I am wondering if there is an alternative to RAR though (ideally an open source one).  Also, I'm looking for a format that incorporates the parity file into the archive so that you don't have separate PAR files floating around which are easy to lose.  Also, compression ratio isn't that important.  Compressing the text files down a bit would be nice, but the document scans are already compressed, so trying to compress them again would probably just slow things thing.  

I did manage to find a program called [Parchive]("http://sourceforge.net/projects/parchive"), but it turns out that the parity files it creates are is big as the original file!  I do do backups, but it can be a hassle to go try to compare files from several different drives and and then try to figure out which version I should restore. Anyway, thanks for your suggestions.

---

### Post by ramjet_1953 on 2009-06-20
I have found that PeaZip is very good.

It is available for both Windows and Linux and is free.

Here is a link to download.

[http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

Regards,
Roger :D

---

### Post by balachandarlinks on 2009-06-20
Hi,
   Try 7zip.It is extremely good and you can install the 7zip plug in to your ubuntu archiver using synaptic. 
                   cheers,

---

### Post by learningcurb on 2009-06-21
Can either of these programs generate parity data though?  I checked Peazip and I don't think it can, though it can repair damaged ARC files.  I'm not sure anyone really uses ARC files.  I like some of it's checksumming features though.

---

### Post by stinger30au on 2009-06-21
use whatever format you like, but if the data is damaged be it zip or not your going to lose data


you need to look at the media your backing your data to

is it a hdd or cd/dvd???

have you checked the media for errors? eg run some kind of disc tools on he hdd to checkf ro bad sectors?
you can use this to test

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

if your using cd/dvd to backup to, i would suggest try a different brand of media first. if that fails, replace the dvd burner, they are cheap as chips now days, in fact im suprised they are not putting them in corn flakes packets as bonus giveaways for the kids

---

### Post by Wim Sturkenboom on 2009-06-21
No answer to the question but it shows that it's important to verify that backups are OK.

I usually backup and next restore to a different directory and do some random checks against the originals (size mostly, sometimes a diff).

---

### Post by mbsullivan on 2009-06-21
> I know that RAR archives support parity files which allow you to repair damaged archives.

That's true.

> I am wondering if there is an alternative to RAR though (ideally an open source one).  Also, I'm looking for a format that incorporates the parity file into the archive so that you don't have separate PAR files floating around which are easy to lose.

Good question! I'm not sure what the answer is -- it may be that there is not a good solution commonly available right now.


> I did manage to find a program called [Parchive]("http://sourceforge.net/projects/parchive"), but it turns out that the parity files it creates are is big as the original file! 

I believe that this program is available through the repo in the "par2" package, and might be your best bet.

It doesn't sound right that the parity files must be as large as the original file... If properly configured, I think you should be able to create smaller parity files. I don't know how to use the program, but there's a tutorial [here]("http://www.angelfire.com/magic2/hq-audio/par2-guide.htm") that might be a good first step.

While, technically, par2 does some of what you want, I admit that it's not a perfect solution. First off, it creates external files. It also appears to be quite slow, manually intensive, and somewhat confusing.

I'd be interested to hear if somebody comes up with something better. Data loss with corruption is definitely *not* unavoidable.

Mike

---

### Post by Gen2ly on 2009-06-21
learningcurb, i understand the process of wanting to ensure your data integrity is very important.  I've had issues with Mac OS and Windows in the past corrupting zip archives so this is possibly where you are coming from.  Filesystems nowadays are pretty robust particularly Linux's ext#.  Been using Linux 2 years now and never had a problem of a corrupt archive.  A couple tips to make sure you data is kept intact:  Don't uses FAT32 - most people don't have a problem with it most of the time but it doesn't have journaling and that makes it greater prone to damage.  And 2) regularly check your disks.  Linux automatically does this around every 30 boots but if you ever suspect a problem this should be the first thing you do.  

In Linux md5sum is used to check integrity of files, generally it goes like this:

Enter the file(s) directory and create an md5sum file:

```
md5sum <file1> <file2> >> MD5SUM
```

Then to check if the file(s) is/are ok in the future:

```
md5sum -c MD5SUM
```

---

### Post by mbsullivan on 2009-08-17
Bump? It kind of bugs me that there isn't an adequate answer to this one.

Mike

---

### Post by mikechant on 2009-08-17
Take a look at dvdisaster:
[http://dvdisaster.net/en/](http://dvdisaster.net/en/)

and particularly at this overview page
[http://dvdisaster.net/en/howtos60.html](http://dvdisaster.net/en/howtos60.html)

This might be the sort of thing you're looking for.

---

### Post by leguman on 2009-09-27
if you do 

par2 create *

in your directory, it will create a set a par2 files with 5% redundancy for all your files ( defaut setting that you can change of course )

that way if one of your files is deleted or really incomplete you can repair it which would not have been possible if you had a 5% redundancy set for each file seperately


a lot of people in this thread didn't understand the question, AFAIK rar is the only file format with integrated parity information, but this is different than what it's done on usenet : [normal rar file + seperate par2 archive]("http://altbin.net/2009/09/advice-for-posting-par2-and-split-files.html")

---

