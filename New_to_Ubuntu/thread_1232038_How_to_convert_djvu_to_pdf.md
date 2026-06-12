---
title: "How to convert djvu to pdf"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Tapas Bose, India on 2009-08-05
_Step - 1 : _Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
 

 _Step - 2 : _Install
 
[LIST=1]
[*]djvulibre-bin
[*]libdjvulibre21
[*]okular-extra-backends
[*]evince
[*]libevdocument1
[*]libevview1
[/LIST]
 

 _Step - 3 :_ Goto terminal and write


               	sudo apt-get install libtiff-tools
 

 _Step - 4 :_ Goto the directory where the djvu file is present. Click the right mouse button. Goto “Open In Terminal” option. Click on it. A terminal will open.
 

 _Step - 5 :_ In that terminal write
 

               	ddjvu -format=tiff file_name.djvu file_name.tiff
 	
 	
               	tiff2pdf -j -o file_name.pdf file_name.tiff
 

 


 The djvu to pdf conversion is done. :) :)

 

 N.B. file_name means name of your djvu file.

---

### Post by Tapas Bose, India on 2009-08-05
[U]Correction :

djvu2pdf???? see how to convert djvu to pdf
[/U]

---

### Post by Sef on 2009-08-05
merged threads.

---

### Post by Geraba on 2010-02-23
I tried this, and I got the message:

```
Aborted (core dumped)
```

Using verbose mode, it seems it gives this error in the middle of the document... So the .tif file is incomplete.

---

### Post by redbook4574 on 2010-02-23
> **Geraba said:**
> I tried this, and I got the message:

```
Aborted (core dumped)
```

Using verbose mode, it seems it gives this error in the middle of the document... So the .tif file is incomplete.


Admittedly I have never used Djvu but would it not be possible to simply open the djvu file with djvu viewer and then print to a pdf printer (ie cups-pdf).

---

### Post by Geraba on 2010-02-23
It seems it worked... Thanks!

But is there a way to convert using the command line only?

---

### Post by ubunterooster on 2010-02-23
why can't you just cntrl+p, print to file, and have that file be pdf?

---

### Post by Genitruc on 2010-03-12
Here how I did.
1) open file.djvu with evince
2) use ctrl+p to go in the print option and choose "print to file". This convert your file in .ps
3) open okular and use "import to pdf" in the file menu to import your .ps file.
4) use "save as" to save your document in pdf

Genitruc

---

### Post by cor3huis on 2010-04-27
What about simply using DJView and export as PDF?

Step - 1 : Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
Step - 2 : Install  DJview4
Step - 3 : Run DJview (Applications - Graphics - DJView4)
Step - 4 : Open your .djvu document
Step - 5 : Menu - Export As: PDF

Done! A simpler method I cannot think of :-) Good luck!

---

### Post by gazazello on 2010-08-14
> **cor3huis said:**
> What about simply using DJView and export as PDF?

Step - 1 : Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
Step - 2 : Install  DJview4
Step - 3 : Run DJview (Applications - Graphics - DJView4)
Step - 4 : Open your .djvu document
Step - 5 : Menu - Export As: PDF

Done! A simpler method I cannot think of :-) Good luck!

Nice! It worked swiftly and smoothly! Thank you!

---

### Post by ivan.p on 2010-08-18
Using Djview4 worked for me too. Thank you.

---

### Post by ivan.p on 2010-08-18
> **ubunterooster said:**
> why can't you just cntrl+p, print to file, and have that file be pdf?

> **redbook4574 said:**
> Admittedly I have never used Djvu but would  it not be possible to simply open the djvu file with djvu viewer and  then print to a pdf printer (ie cups-pdf).

I suspected Djview4 would keep text as text when generating a PDF file. This would have been a strong argument in favour of Djview4 vs cups-pdf. Apparently, Djview4 exports everything as images, which means that it generates huge PDF files, even when the original Djvu files are small.

However, evince does not render some Djvu files properly. To use your method (printing the file as PDF), you may need to use a Djvu viewer other than evince. But yes, in principle, your method would work just fine, and it has the advantage of not requiring the installation of new software.

It remains to be seen if there's an alternative solution in which the text in a Djvu file is exported as text in a PDF file.

---

### Post by naught101 on 2010-09-09
None of the methods here keep the underlying text in an OCR'd djvu when converting to a pdf. Anyone know how to do that?

---

### Post by cmcanulty on 2010-09-24
I agree a simple utility hopefully with a GUI is really needed for this conversion

---

### Post by mahy on 2010-09-30
> **Genitruc said:**
> Here how I did.
1) open file.djvu with evince
2) use ctrl+p to go in the print option and choose "print to file". This convert your file in .ps
3) open okular and use "import to pdf" in the file menu to import your .ps file.
4) use "save as" to save your document in pdf

Genitruc

Works in most cases, but I had a djvu document with some portrait and some landscape pages. This method resulted either in all pages portrait or all pages landscape...

---

### Post by mahy on 2010-09-30
> **Tapas Bose, India said:**
> 

               	ddjvu -format=tiff file_name.djvu file_name.tiff
 	
 	
               	tiff2pdf -j -o file_name.pdf file_name.tiff
 


I succeeded in creating the TIFF file, but then the subsequent PDF file was okay viewed in Evince, but Adobe Reader and Foxit Reader displayed it all RED! ](*,)

The only option was to leave out the "-j" JPEG encryption. However, the resulting PDF was more than 10 times as big... :)

---

### Post by rndmusr on 2010-10-17
[http://0x2a.at/s/projects/djvu2pdf](http://0x2a.at/s/projects/djvu2pdf)

command line tool for djvu to pdf conversion

---

### Post by bariskeskin on 2010-12-11
> **cor3huis said:**
> What about simply using DJView and export as PDF?

Step - 1 : Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
Step - 2 : Install  DJview4
Step - 3 : Run DJview (Applications - Graphics - DJView4)
Step - 4 : Open your .djvu document
Step - 5 : Menu - Export As: PDF

Done! A simpler method I cannot think of :-) Good luck!


I tried the other solutions but only this one worked for me thank you very much :)

---

### Post by cmcanulty on 2010-12-11
That works great does anyone know of a similar tool to convert chm files to pdf hopefully a graphical tool.

---

### Post by Hrexen on 2011-01-20
I did it in other way.
I just printed it to file twice by default Document Viewer.
For first time to *.ps* and after to *.pdf*.

P.S. *.ps* to *.pdf* conversion takes a lot of time. :)

---

### Post by luisjaime on 2011-02-25
Thanks, the last sugestion is very efficient and practical.
:D

---

### Post by luisjaime on 2011-02-25
Thanks, the last post gave me the solution, it's very efficiently and practical

---

### Post by airtonix on 2011-03-01
hilarious, turned an 8mb djvu file into a 300mb pdf.

---

### Post by Rushyang on 2011-03-10
> **airtonix said:**
> hilarious, turned an 8mb djvu file into a 300mb pdf.

Same case here.. My 5MB djvu file turned out as 614MB pdf..:shock: I deleted it after conversion.. 8-[

---

### Post by haydoni on 2011-05-31
> **naught101 said:**
> None of the methods here keep the underlying text in an OCR'd djvu when converting to a pdf. Anyone know how to do that?
I'd also like to know this! :confused:

---

### Post by Varad Vyapari on 2011-06-05
> **cor3huis said:**
> What about simply using DJView and export as PDF?

Step - 1 : Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
Step - 2 : Install  DJview4
Step - 3 : Run DJview (Applications - Graphics - DJView4)
Step - 4 : Open your .djvu document
Step - 5 : Menu - Export As: PDF

Done! A simpler method I cannot think of :-) Good luck!
thanks bro, it really is too simple..will u assist me as to how to post queries on ubuntu forums? i m a school-going boy and am not adept to ubuntu forums.
thanks a lott

---

### Post by honeybear on 2011-09-06
> **Tapas Bose, India said:**
> _Step - 1 : _Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
 

 _Step - 2 : _Install
 
[LIST=1]
[*]djvulibre-bin
[*]libdjvulibre21
[*]okular-extra-backends
[*]evince
[*]libevdocument1
[*]libevview1
[/LIST]
 

 _Step - 3 :_ Goto terminal and write


               	sudo apt-get install libtiff-tools
 

 _Step - 4 :_ Goto the directory where the djvu file is present. Click the right mouse button. Goto &#8220;Open In Terminal&#8221; option. Click on it. A terminal will open.
 

 _Step - 5 :_ In that terminal write
 

               	ddjvu -format=tiff file_name.djvu file_name.tiff
 	
 	
               	tiff2pdf -j -o file_name.pdf file_name.tiff
 

 


 The djvu to pdf conversion is done. :) :)

 

 N.B. file_name means name of your djvu file.

djview4 has amazing export options. it is x11 and gtk. great

[http://djvu.sourceforge.net/djview4.html](http://djvu.sourceforge.net/djview4.html)

---

### Post by b77665 on 2011-12-20
There is no need for the djvu2pdf script. You can also convert a djvu file to pdf with the following terminal command:
 
 ddjvu -format=pdf input.djvu output.pdf

Nevertheless the filesize is bloated as mentioned. Maybe this is caused by a missing compression of internally used imagefiles.

---

### Post by Varad Vyapari on 2012-05-16
install DjView4, open the djvu document then click on file-export as and proceed..it is indeed simple and efficient though it can blow up the file size considerably

---

### Post by selinger on 2012-11-27
The "export to PDF" option in djview worked fine, except that it lost the searchable text. The djvu file I am looking at consists of some scanned pages of text, with the "encoded" text behind it so that it is searchable. In the PDF, there are just the scanned image, all the character info is lost.

Does anyone know how to convert it to PDF and preserve the searchability?

---

### Post by VirtualPirate on 2013-02-19
Quote:
Originally Posted by cor3huis  
What about simply using DJView and export as PDF?

Step - 1 : Goto Synaptic Package Manager (System - Administration - Synaptic Package Manager)
Step - 2 : Install DJview4
Step - 3 : Run DJview (Applications - Graphics - DJView4)
Step - 4 : Open your .djvu document
Step - 5 : Menu - Export As: PDF

Done! A simpler method I cannot think of  Good luck!


This worked great thanks.):P

---

### Post by oldos2er on 2013-02-19
Old thread closed.

---

