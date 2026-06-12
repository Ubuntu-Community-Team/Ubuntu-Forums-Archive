---
title: "convert pdf to gif or similar"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by stinger30au on 2009-01-19
i have been scanning in some old books of mine and converted them to pdf. one of them is a colour book thats about 30 pages long.
i scanned it at 300 dpi full colour and saved as pdf using gscan2pdf


the file is now about 500 meg long
and i have scanned in other similar books and got the same

the files are *NOT* password protected any anything fancy like that

id like to convert the pages to gif so they are about only a few hundred kilobytes in size instead of the size they are now

can anyone suggest any thing that can do this, be it shell based or wine based or what ever.

---

### Post by kaibob on 2009-01-19
> **stinger30au said:**
> id like to convert the pages to gif so they are about only a few hundred kilobytes in size instead of the size they are now
The convert utility, which is a part of the imagemagick suite, will convert a PDF document to a GIF image. To do this, open a terminal window and change to the directory that contains the image files. Then, enter the following:

```
convert inputfile.pdf outputfile.gif
```

Imagemagick is in the repo's if it's not already installed on your computer.

---

### Post by Kellemora on 2009-01-19
Hi kaibob

WISH I knew about this last week!

I had some PDF's come in that I needed to sign and send back, and they forgot to leave it OPEN so I could do that.  Paste my sig to the document and send it back.

I had to print it out, sign it, scan it, convert back to PDF and resend it back to them.  Lost a LOT in that process, hi hi......

I used to have a program that would capture the print cycle and convert that to Open PDF, but it only works in the DOZE.

TTUL
Gary

---

### Post by stinger30au on 2009-01-20
thanks for the feedback, i will let oyu know how i go

---

### Post by mtausig on 2009-01-20
Imagemagick is an excelent choice.
But if you prefer to use a GUI application, you can also open PDFs in Gimp and save them in any image format you like.

---

### Post by Kellemora on 2009-01-21
Hi MT

Neither Gimp NOR PDF Editor would open LOCKED PDF files for me, I tried both.  It would come up with some error message that 000x0657 blah de blah was unrecognized file format.

After you mentioned Imagemagick, I used it in command line mode (I think it has a GUI mode, although I didn't look for it).
It must not check to see if a file is locked or not, it just converted it no problem, instantly too!

I've since tried it on other locked pdf files and it worked on them too.  Plus it does a LOT of other things as well.

Don't LAUGH, I still have and use, almost daily, a very old Windows 95 program called GraphicsWorkshop95.  We have THOUSANDS of image files in PCX format, held image quality at reasonable file sizes back when HD space was at a premium.  Like Tiff, there are different PCX formats.  It all depends upon WHICH program was used to edit it last.  At the old office we used to have a big sign on the wall, if you Edited a PCX file, open it with such n such and resave it, else it won't work all the time.
A new employee was deleting files that just came up in BLACK figuring they were corrupt.  Luckily we caught her before she deleted too many.  I restored them from the backups!  But out of habit, every Tiff or PCX file is run through GraphicWorkshop95 to rewrite it in format even recognized in Ubuntu!

We also have thousands of WRI files that because they were opened with WordPad and resaved as WRI are no longer readable by WRITE.  We still USE Write3.11 it's POWERFUL for some jobs that take FOREVER to do on msWord or OpenOfficeWriter.  It has a Global Font Increase or Decrease NOT FOUND in ANY other program.
Although, as of today, we are down to only a few hundred not converted over to ODT files yet.  They must be done One at a Time using an OLDE msWord2000 program first, then reread by msWord2003 and saved as XP doc.  THEN Open Office can read them with no phunny characters, hi hi........
I have one person working on doing just that 8 hours a day, while we are a little slow.

TTUL
Gary

---

### Post by kaibob on 2009-01-21
> **Kellemora said:**
> Hi MT

Neither Gimp NOR PDF Editor would open LOCKED PDF files for me, I tried both.  It would come up with some error message that 000x0657 blah de blah was unrecognized file format.

After you mentioned Imagemagick, I used it in command line mode (I think it has a GUI mode, although I didn't look for it).
It must not check to see if a file is locked or not, it just converted it no problem, instantly too! <snip>

I'm glad that worked for you. I seem to recall someone mentioning once that you can open locked PDF files in the Imagemagick display utility. Converting them to another format as you are doing sounds best, but if you want to give display a try, the command is:

```
display filename.pdf
```

You don't hear much about PCX format anymore. It was actually quite useful--perhaps there are licensing issues.

---

### Post by stinger30au on 2009-01-22
if you fireup shell and type in 

display


imagemagic will startup and you can manually scroll thry your hdd and pick what you want as well

---

### Post by Kellemora on 2009-01-23
Thanks kaibob and stinger!

I'm one of those OLDE Diehards!
When I find something that WERKS (sorry Maynard), I rarely change until it becomes an absolute necessity.

Although we've finished converting them over to CD's now, I had thousands of 5-1/4 floppies.  Some were even single sided single density that I punched holes in to use the back side too!
We NEVER lost data from a 5-1/4 ever, even shipping them back and forth through the USPS didn't hurt them.

We had so many problems with the 3-1/2 inch floppies that we swore them off as long as possible.  Where we could send a single 5-1/4 floppy, it often took SIX 3-1/2's to insure at least one of them was readable at the other end.

We had a LOT of problems with TIFF files, and BMP files were too huge for the resolution we needed to work within.  The ONLY image storage system that was loss free and almost problem free and used much less space was the PCX format.  So virtually EVERYTHING here was converted to PCX....  THEN they began changing how PCX was saved by some programs, such that if you used a particular program to edit the image, none of the other programs could open it afterwards.  Then we found GraphicsWorkshop95 which converts images from one file format to another quickly and error free.  Have been using it every since.  I even have it loaded here in WINE on my Ubuntu machines!
I'm still undecided on which format to use next, PNG looks very promising!

Although we have little manufacturers support in Ubuntu, nearly EVERYTHING we do, works better, faster and without delays in Ubuntu, compared to the Doze, once you learn the workarounds for the shortfalls still present in Linux in general.

Have a nice day gang!

TTUL
Gary

---

