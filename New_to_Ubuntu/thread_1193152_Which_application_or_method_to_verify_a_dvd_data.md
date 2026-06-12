---
title: "Which application or method to verify a dvd data ?"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by ubfu on 2009-06-21
I had a few dvd data and some backup movie dvd burned few months ago.

I remember I forgotten to verify disk using window application Nero burner.

I was wondering is there any application for Ubuntu or terminal function to check the sector by sector ?
Data are allocated and save at NTFS partition and I burned it into a dvd.I would like to verify them again.

Thank you very much

---

### Post by bhadotia on 2009-06-21
> **ubfu said:**
> I had a few dvd data and some backup movie dvd burned few months ago.

I remember I forgotten to verify disk using window application Nero burner.

I was wondering is there any application for Ubuntu or terminal function to check the sector by sector ?
Data are allocated and save at NTFS partition and I burned it into a dvd.I would like to verify them again.

Thank you very much

Why don't you use nero itself for that. If you saved the projects then you might be able to verify the disk integrity.

---

### Post by ubfu on 2009-06-21
> **bhadotia said:**
> Why don't you use nero itself for that. If you saved the projects then you might be able to verify the disk integrity.

How do I verify the disk integrity ? 
I was wondering any alternative on sector check on ubuntu.

---

### Post by niteshifter on 2009-06-21
Hi,

The program "cdck" will check the integrity of of a cd/dvd. Install via Synaptic or use the command line:
```
sudo apt-get install cdck
```

Run it from the command line. Instructions for use:
```
man cdck
```

---

### Post by bhadotia on 2009-06-21
> **ubfu said:**
> How do I verify the disk integrity ? 
I was wondering any alternative on sector check on ubuntu.
 I don't remember how to do that in nero (haven't used it for a year and a half now). You can check the help in nero to find out how to do that.

The above post by niteshifter tells you how to do that on ubuntu ;)

---

### Post by ubfu on 2009-06-22
> **niteshifter said:**
> Hi,

The program "cdck" will check the integrity of of a cd/dvd. Install via Synaptic or use the command line:
```
sudo apt-get install cdck
```

Run it from the command line. Instructions for use:
```
man cdck
```

So let say I wanted to compare media files like a.mp3 at :N to a dvd 
How to write the command ?

---

### Post by niteshifter on 2009-06-22
Hi,

cdck is used to verify an entire cd / dvd. It doesn't perform a file check, it reads a cd / dvd sector by sector and looks at the read timings of each. Sectors which are going bad - but still readable - will present with longer times. cdck compares the timings, letting you know a cd / dvd is A) readable, B) that is has sectors that are slow reading (disc is failing).

For verifying files you have choices. For text files the program "diff" is frequently used. It compares files line-by-line and has many options to control how the compare is done and how the output is made. The man page on diff covers all the options.

"Binary" files - media like .avi, mp3 or binary executables - can be checked using the program  md5sum. This program reads the file and computes a hash (like a checksum) on the data. If even a single bit of a byte is different a different hash result will be had. To compare two files with md5sum is to run it twice: 

```
md5sum /home/user/somefile.mp3
md5sum /media/dvd-mount/somefile.mp3
```

and compare the output of the two runs. md5sum can also be used on text files, but can't tell you where the difference(s) are as opposed to diff, which will show the differences.

---

### Post by scrooge_74 on 2009-06-22
> **niteshifter said:**
> Hi,

The program "cdck" will check the integrity of of a cd/dvd. Install via Synaptic or use the command line:
```
sudo apt-get install cdck
```

Run it from the command line. Instructions for use:
```
man cdck
```

Since you are on the subject, if I check a cd/dvd and I find it has errors is there any chance of recovering the affected files?

---

### Post by niteshifter on 2009-06-22
> **scrooge_74 said:**
> Since you are on the subject, if I check a cd/dvd and I find it has errors is there any chance of recovering the affected files?

Maybe. cdck will report I/O errors and excessive times. If excessive times the file(s) are still readable and you're OK. I/O errors are another story.

For that ddrescue is handy. Note that there are two versions floating around:
ddrescue - The GNU version
dd_rescue - The Debian project.

What complicates things is some distros rename dd_rescue to ddresuce. The two are somewhat different. I've always favored the GNU version, although both are supposedly the same. GNU ddresuce comes with a terse man page, the full manual is an info file.

ddrescue doesn't stop in I/O errors it keeps reading and copying (and a logfile). After a pass - and if the kernel supports RAW I/O (Ubuntu does) RAW I/O can be set up and ddrescue run again, this time working from it's log file where it will attempt to read down to the byte level. IOW rather than missing whole blocks /  sectors the loss can be cut to some-odd bytes.

For files where each and every byte must be present like a binary executable one still has work (tedious work at that) trying to determine the missing data. For multimedia files such small gaps can be tolerated.

One thing about either version: /var/logs can wind up with some impressive sized log files - each and every I/O error is logged. Think hundreds of megabytes or even 1GB plus. Can be a problem for those with a small mount for /var or cramped on disk space.

---

### Post by scrooge_74 on 2009-06-22
Thanks for giving me some lights into my problem, what I have is a DVD of some concert (actually this is a favor for a friend) and it wont read any more.

Internally the DVD has to files (seems is two concerts in one DVD), I managed to read the DVD by mounting it  -t iso9660 that way I managed to copy out the second part, but the first part is still gives and I/O error.

Using dd I managed to copy the problem file out of the DVD, but still is not readable, I'll give ddrescue a try and will report back.

Thanks

---

### Post by scrooge_74 on 2009-06-23
After many hours of data crunching it seems the file may be to damage to repair, it says it has lots of errors, most of the video dosen't run, there are a few parts that video and audio is choppy, but that is all. Unless there is a magic option I can use I dont see I can save the file.

rescued:    65699 kB,  errsize:   1007 MB,  current rate:        0 B/s
   ipos:     1073 MB,   errors: 1982285,    average rate:     2962 B/s
   opos:     1073 MB

---

### Post by ubfu on 2009-06-23
> **scrooge_74 said:**
> After many hours of data crunching it seems the file may be to damage to repair, it says it has lots of errors, most of the video dosen't run, there are a few parts that video and audio is choppy, but that is all. Unless there is a magic option I can use I dont see I can save the file.

rescued:    65699 kB,  errsize:   1007 MB,  current rate:        0 B/s
   ipos:     1073 MB,   errors: 1982285,    average rate:     2962 B/s
   opos:     1073 MB

There are other ways you try out.What dvd reader you are using ? 
Some dvd reader may have strong laser reader which can help to read more files than yours.Try with different dvd-rom.

Second , try and put the cd into the refrigerator at the lower part for like 5 min take it out and let it cool down for a min and try to let it read.Not sure whether it's possible.

Third , shutdown your pc for overnight to let your dvd-rom rest.And the next day , the min after your pc starts put the disc and rescue those data.

---

### Post by scrooge_74 on 2009-06-23
Well DVD I'm using is the one inside this laptop so not much luck there, owner of CD has tried to read it using a couple different machines or DVD readers with no luck (that is why he handed it to me).

Ok, so I would put it in fridge in bottom part for 5 mins, then out wait 1 min then try to read it right? Here is a bit warm (Ok is pretty warm at 30°C or so) will that have any effect?

I could try the last one on a laptop that has being off since last night.I'll try that one first....this method did not work (that one can dual boot) cant copy the file out.

---

### Post by ubfu on 2009-06-23
> **niteshifter said:**
> Hi,

cdck is used to verify an entire cd / dvd. It doesn't perform a file check, it reads a cd / dvd sector by sector and looks at the read timings of each. Sectors which are going bad - but still readable - will present with longer times. cdck compares the timings, letting you know a cd / dvd is A) readable, B) that is has sectors that are slow reading (disc is failing).

For verifying files you have choices. For text files the program "diff" is frequently used. It compares files line-by-line and has many options to control how the compare is done and how the output is made. The man page on diff covers all the options.

"Binary" files - media like .avi, mp3 or binary executables - can be checked using the program  md5sum. This program reads the file and computes a hash (like a checksum) on the data. If even a single bit of a byte is different a different hash result will be had. To compare two files with md5sum is to run it twice: 

```
md5sum /home/user/somefile.mp3
md5sum /media/dvd-mount/somefile.mp3
```

and compare the output of the two runs. md5sum can also be used on text files, but can't tell you where the difference(s) are as opposed to diff, which will show the differences.

Thanks , I did a md5sum check through it one by one.Did check all and all of it match.I went back to window and download a program cdcheck and install it.After verify and compare , both data was successfully match.

Just for some questions , to be clear , did the md5sum check data sector by sector on a dvd ? I know it'll compare both file size but can it actually check whether at some part minute or second which it's readable ?

---

### Post by KIAaze on 2009-06-23
md5deep is also great for checking directories/CDs/DVDs for integrity:
[http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)
```
sudo apt-get install md5deep
```

It's basically a recursive md5sum. :)

cf also:
[https://www.linuxquestions.org/questions/linux-general-1/error-checking-cds-with-recursive-md5-335372/](https://www.linuxquestions.org/questions/linux-general-1/error-checking-cds-with-recursive-md5-335372/)
[http://www.thelinuxblog.com/recursive-md5-sum-script/](http://www.thelinuxblog.com/recursive-md5-sum-script/)

And if you burned the DVD from an .iso file and still have it:
```
md5sum image.iso > md5.txt
```
Replace "image.iso" in md5.txt with "/dev/cdrom" and then:
```
md5sum -c /dev/cdrom
```

You may have to replace /dev/cdrom with the device corresponding to you DVD drive.

---

