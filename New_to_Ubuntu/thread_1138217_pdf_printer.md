---
title: "pdf printer?"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by smileyguy on 2009-04-26
Is there a pdf printer available for Ubuntu? I need to be able to "print" to a virtual pdf printer rather than "export" to pdf as the "export" to pdf feature in OO3 doesn't give me the same options as printing (i.e., printing notes at the bottom of each page/document). I usually use cutepdf in MS Word on Windows for this.

---

### Post by namaku0 on 2009-04-26
Hm, after installing **cups-pdf** package there is
an option to print to PDF on OO Writer. But it won't
output the file on my Jaunty install.

For now, until someone found a better solution, maybe
you want to use the **Print to file** (File > Print >
Print to file). It will output a PS (PostScript) file,
and then you convert it manually from the command line
with **ps2pdf.**

#ps2pdf thefile.ps

---

### Post by smileyguy on 2009-04-26
Yeh thanks - I just found the failed output on mine after some searching too!

It is suppused to be in home\pdf but there ain't nothing there.

Thanks for the convert tip:)

**Does it work with other file formats? and does that mean a different command?**

---

### Post by blueridgedog on 2009-04-26
If you elect to print to file, you will note that you can print to either PDF of PS.

---

### Post by Didius Falco on 2009-04-26
I'm using Open Office 3.0, and the "Export to PDF" is working fine for me. I just tested it with 4 different files.

I can't help with why yours isn't working, but knowing mine does should give you hope that it can. Hopefully, someone more knowledgeable than I will turn up to troubleshoot it.

---

### Post by smileyguy on 2009-04-26
> **blueridgedog said:**
> If you elect to print to file, you will note that you can print to either PDF of PS.
I can only see the **Postscript** option if I print to file . . .

---

### Post by gandaran on 2009-04-26
> **smileyguy said:**
> I can only see the **Postscript** option if I print to file . . .
which ubuntu version you have? if 8.10 or 9.04 look again it's there.

---

### Post by solar george on 2009-04-26
> It is suppused to be in home\pdf but there ain't nothing there.
Make sure that /home/*username*/PDF/ exists and is a directory (just replace *username* with your username

---

### Post by smileyguy on 2009-04-26
Went to File>Print> ticked **Print to File** then **OK** and it definitely had postscript only only.

ALTHOUGH I just tried SolarGeorge's solution and created the PDF directory myself and it worked! I just assumed CUPS PDF would create the output folder itself. THANKS:D

It is a funny output of the notes though (converted to text, not represented as it is in the actual OO app but better than nothing. Still I would love it to do it as well as MS Office as that is justsuch a useful feature for teachers . . .)

---

### Post by smileyguy on 2009-04-26
oh - and i have Ubunto 9.04 with OO 3.01

---

### Post by stwschool on 2009-04-26
Been having the usual problem with cups-pdf but just found a very useful workaround online. Try the following in your terminal..

sudo aa-complain cupsd

No idea what it does but it seems to work. Should give you a nice shiny pdf printer.

---

### Post by gandaran on 2009-04-26
> **smileyguy said:**
> Went to File>Print> ticked **Print to File** then **OK** and it definitely had postscript only only.

ALTHOUGH I just tried SolarGeorge's solution and created the PDF directory myself and it worked! I just assumed CUPS PDF would create the output folder itself. THANKS:D

It is a funny output of the notes though (converted to text, not represented as it is in the actual OO app but better than nothing. Still I would love it to do it as well as MS Office as that is justsuch a useful feature for teachers . . .)
the print to pdf option does not work with open office but check firefox or other apps where it will work.
for open office use export to pdf option instead, there's no need to have cups-pdf installed just to print to pdf on open office!

---

### Post by llamabr on 2009-04-26
> **smileyguy said:**
> Yeh thanks - I just found the failed output on mine after some searching too!

It is suppused to be in home\pdf but there ain't nothing there.

Thanks for the convert tip:)

**Does it work with other file formats? and does that mean a different command?**

Yes, you can convert between most file formats.  You can move from most MS suite formats to nearly anything with the WV suite:

```
wvAbw         wvConvert     wvdialconf    wvDVI         wvLatex       wvPDF         wvRTF         wvText        wvWare
wvCleanLatex  wvdial        wvDocBook     wvHtml        wvMime        wvPS          wvSummary     wvVersion     wvWml

```

And then between nearly anything and anything with their own commands, like:

```
brock@hops:~$ ps
ps             ps2pdf12       ps2ps          psbook         psfstriptable  psmandup       psselect       pstree
ps2ascii       ps2pdf13       ps2ps2         psed           psfxtable      psmerge        psset          pstree.x11
ps2epsi        ps2pdf14       ps2txt         psfaddtable    psidtopgm      psnup          pstopnm        pstruct
ps2pdf         ps2pdfwr       ps4pdf         psfgettable    pslatex        psresize       pstops         
brock@hops:~$ pdf
pdf2dsc    pdfetex    pdfimages  pdflatex   pdftex     pdftohtml  pdftops    
pdf2ps     pdffonts   pdfinfo    pdfopt     pdftoabw   pdftoppm   pdftotext  

```

Check the repositories for something like "rtf to html converter".

---

### Post by solar george on 2009-04-26
Do you have the same problems when printing to an ordinary printer?
If not that sounds like a bug to me, maybe you could post  a screen shot of OOorg and a the PDF viewer showing the output (or even the actual files) so we can see what you mean.

---

### Post by Cybie257 on 2009-04-27
> **smileyguy said:**
> I can only see the **Postscript** option if I print to file . . .

Are you sure you aren't seeing a radio button option for either .ps or .pdf? I've always had that option with a default Install of Ubuntu. The .ps is default, while you have to change it to .pdf

Otherwise, I notice that in Synaptics that poppler-utils and ghostscript are both installed. That might be the ticket to getting .pdf option? Not sure, though, as like I said, I've always had the option from a fresh default install.

-Cybie

---

### Post by llamabr on 2009-04-27
> **Cybie257 said:**
> Are you sure you aren't seeing a radio button option for either .ps or .pdf? I've always had that option with a default Install of Ubuntu. The .ps is default, while you have to change it to .pdf

Otherwise, I notice that in Synaptics that poppler-utils and ghostscript are both installed. That might be the ticket to getting .pdf option? Not sure, though, as like I said, I've always had the option from a fresh default install.

-Cybie

Also, are we talking about printing from firefox, or openoffice?  From the former, I get a pdf button, but by default, i don't get one in the latter (There's an addon for it, I think).

---

### Post by blueridgedog on 2009-04-27
I just did a clean in stall and system printing (and programs that use is such as firefox) have "Print to File" as an option, and when selected you get a choice of two formats "PDF" and "Postscript".

---

### Post by ewisnor on 2009-04-28
The Cups PDF printer is pretty awful. It does one thing, and it does that one thing VERY poorly.

Things it should do that it does not:

1) Prompt user for a directory to save the PDF to
2) Automatically fill the PDF file name with the document's title (within the save dialog)
3) Return any errors

Right now it dumps (from Opera, at least) to ~/PDF/_stdin_.pdf EVERY time. If this file already exists (like if you forget to change the filename manually) then it gets overwritten. No error messages if there are problems (including if the PDF directory does not exist).

Talk about 5 minute crapware...
is there nobody who can correct this?

---

### Post by blueridgedog on 2009-04-28
When I try and print to a file, using the pdf option, I can specify the path and file name:

---

### Post by solar george on 2009-04-29
The people who make the opera browser. Its not CUPS's fault that opera prints to stdin (LPR i think).
If you don't like it get opera to build in a pdf printer or follow advice in this thread about using print to file.

---

### Post by smileyguy on 2009-04-29
In Firefox I get the option to print to pdf (if I print to file). not sure if this is because I have cups installed or just part of Firefox.

I can't seem to attache a file to post a screenshot of what I'mm getting in OOorg (like llamabr's last sentence in his last post - just checked this again) but I can't seem to attach a screenshot. If I click **Insert Image** in replying to this it asks for a URL. I assume it has soemthing to do with permissions on this forum . . .

At least I can get cups doing what i want:)

---

### Post by blueridgedog on 2009-04-29
> **smileyguy said:**
> 
I can't seem to attache a file to post a screenshot of what I'mm getting in OOorg (like llamabr's last sentence in his last post - just checked this again) but I can't seem to attach a screenshot. If I click **Insert Image** in replying to this it asks for a URL. I assume it has soemthing to do with permissions on this forum . . .

At least I can get cups doing what i want:)

To upload an image, use the paper clip icon, which will let you attach something to your post.

---

### Post by stchman on 2009-04-29
> **smileyguy said:**
> Is there a pdf printer available for Ubuntu? I need to be able to "print" to a virtual pdf printer rather than "export" to pdf as the "export" to pdf feature in OO3 doesn't give me the same options as printing (i.e., printing notes at the bottom of each page/document). I usually use cutepdf in MS Word on Windows for this.

Yes, OO does pdf export and you can select print to file with PDF option.

---

### Post by rajaiskandarshah on 2009-05-01
> **smileyguy said:**
> 
ALTHOUGH I just tried SolarGeorge's solution and created the PDF directory myself and it worked! I just assumed CUPS PDF would create the output folder itself. THANKS:D


worked for me as well after creating the PDF folder

---

### Post by mevan_snp on 2009-06-02
thanks for grate info.................

---

### Post by pakki on 2010-04-16
Here occurs my problem!!

> **pakki said:**
> i downloaded cups a virtual pdf printer & then printed several pages frm various sites as pdf files using opera & firefox. I viewed thm wth builtin doc viewer of ububtu & thy were superb
i downloaded portable version of pdf xchangeviewer offered by Tracker software & was able to run it under wine. I used ths viewer bcz i can highligh bookmark the pdf files...
Now the problem is tht when i used to vie pdf files craeted by cups gave error  & didnt opened while i was able to view edit any file tht i had in my collection but ofcourse thy were craeted most in XP
[IMG]http://i44.tinypic.com/347a9ub.jpg[/IMG]
[IMG]http://i44.tinypic.com/11lmzx0.jpg[/IMG]

What could be the problem i really need such files to be UNIVERSAL!!

---

### Post by kenn123 on 2010-06-15
I had a similar problem after upgrading from 8.04 to 10.04.  username/PDF directory existed, as did the PDF printer, but when I tried to print to the PDF printer, no file appeared.  I installed cups-pdf, but still no file appeared when printing.  Eventually I renamed the PDF printer to something else, then removed cups-pdf and then installed it again.  It recreated the PDF printer and then printing to it worked fine.

---

### Post by mike555 on 2010-06-16
when you "print to" pdf , if you don't set a name it saves it as .pdf , a hidden file .......... open your home folder and click view hidden files , you might find it ...

---

