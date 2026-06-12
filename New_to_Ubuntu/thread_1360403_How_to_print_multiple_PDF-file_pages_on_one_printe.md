---
title: "How to print multiple PDF-file pages on one printed page?"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by swarup on 2009-12-20
In Ubuntu, can PDF-File pages be manipulated and configured for printing according to custom needs?

I need to print a 400-page PDF file. Is there a way to decrease the size of each page and arrange the pages so that two or even three pages fit on each printed page?

---

### Post by swarup on 2009-12-21
I sent this on Sunday night when very few may have been on line to see it. Sorry for pushing it to the front, but I really need help on this. I'm sure there must be a way to bring 2-3 PDF-file pages onto one page to print-- for example, perhaps by some way bringing the PDF into OO Writer, or into Scribus, and bringing the pages together there. Can someone tell me how?

---

### Post by Marlonsm on 2009-12-21
-Open the file with Evince (Ubuntu's default PDF viewer).
-Go to File > Print...
-In that window, go to the "Page Setup" tab.
-Change the "Pages per side" setting.

---

### Post by swarup on 2009-12-21
Thank you. I'll try it and see how it works.

Add: Yes, I've tried it and it works great.:)

---

### Post by swarup on 2009-12-21
The "page setup" tab gives options for 1, 2, 4, 6, or 9 PDF-pages per printed page. I'd like to put 3 PDF-pages per printed page. I wonder if there is a way to do that? Two per page, and the document is too long. Four per page, and the print is extremely small. Three per page would be perfect-- but there doesn't seem to be anywhere to custom type this preference. Any help?

---

### Post by Marlonsm on 2009-12-22
I've looked around the web and I've found that many people have problems with that, not only in Linux, it seems that very few programs have the option to print 3 pages.

It seems that it's because (at least in an A4 sheet), if you print 3 pages side by side, they will actually be smaller than if you print 4 pages (2 by 2).

---

### Post by swarup on 2009-12-22
That was very kind of you to check around. My thought was not to use an A4 sheet, but rather to turn the page on its side and print as landscape rather than portrait. That way, best utilization of the page could be made. But perhaps when printing PDF-files, this sort of manipulation isn't possible?

In absence of the above, another very good option for me is to do two PDF-pages per printed page, and do double-sided printing. But there's a snag in this plan as well, as my printer only does single-sided printing. I could easily manage such double-sided printing if I were doing one PDF-page per printed page, by simply selecting the option to print only odd pages first. And then once that was done, turning the printed stack backwards and selecting to print the even pages. But if I have two PDF-pages per printed page, then the entire page sequence will be wrong if I select only odd pages! I should think there must be a solution for THIS, somehow. That is, if I select 2 PDF-pages per printed page, then I should be able to opt to print only page 1 & 2, 5 & 6, 9 & 10 etc. That way I could print the stack of paper on one side only, and then turn over the stack and print all the pages on the other side. Do you if this can be done?

---

### Post by entropy1 on 2009-12-22
If the original document has wide margins, I have found gsview can be helpful.  Open the document with gsview.  Click on Media and select "User Defined" and choose the page size you want; i.e., the height of the text and the width of the text.

Next, under File choose "Convert".  Click the "Properties" button.  At the bottom of the dialog box you can enter an X and Y offset to move the upper left corner of text toward the upper left corner of the paper.  Click OK, click OK again, enter an output file name.

You will have to experiment to get the offset numbers right.  Eventually, you can make the output pages with almost no margin.

Now when you print multiple pages per sheet, you will have minimum reduction of the print size.

I don't think gsview is available in the repositories.  So I run the windows version under wine (or under windows if you dual boot).  You will also have to install the windows version of ghostscript.  Google around to find gsview and ghostscript.  One place to get them is
[http://pages.cs.wisc.edu/~ghost/gsview/](http://pages.cs.wisc.edu/~ghost/gsview/)

---

### Post by diesch on 2009-12-22
[http://www.florian-diesch.de/software/pdfrecycle/](http://www.florian-diesch.de/software/pdfrecycle/) can put 3 pages on one sheet, and you can turn and crop the input pages.

---

### Post by swarup on 2009-12-23
@entropy1 & diesch: Thanks to both of you for your I helpful suggestions. I have installed pdfrecycle, and will play with it. As for gsview, there does seem to be a Linux version of both it and ghostscript now. I downloaded and extracted the .gz packages of gsview 4.9, and ghostscript 8.7. But I've forgotten how to install from there! What is the terminal command to install them?? Thanks!

Now, I do have a follow-up question: It seems that both the above applications will allow me to manipulate and configure the PDF files as needed. But once that is done, is there a way for me to tell the printer to print pages 1,2,3, then 7,8,9, then 13,14,15? That way I will be able to manage double-sided printing.

---

### Post by entropy1 on 2009-12-24
Swarup,

The reason I suggested running gsview/ghostscript under wine or windows is that I did not know how to install in linux from downloaded files :(  Maybe someday I'll learn.

Double-sided printing depends on your printer.

However, here's a brute-force way:  Use gsview "convert" to extract odd pages to a new file odd.pdf and extract even pages to a new file even.pdf.  Print odd.pdf.  Take output papers and put them back into the printer (properly oriented) and print even.pdf on the back sides.

---

### Post by swarup on 2009-12-24
> **entropy1 said:**
> Double-sided printing depends on your printer.

However, here's a brute-force way:  Use gsview "convert" to extract odd pages to a new file odd.pdf and extract even pages to a new file even.pdf.  Print odd.pdf.  Take output papers and put them back into the printer (properly oriented) and print even.pdf on the back sides.

Ubuntu's default PDF viewer--Evince--can manage even-page and odd-page printing, without having to take extra steps you mention here. That is easy to do (In Evince, go to File -> Print->"Page Setup" tab--"only print" odd or even). But my point is that, once you have set up two, three, or four PDF pages per printed page, THEN how can one do double sided printing (on a printer that only does one-sided printing)? There should be a way to instruct the printer to print i.e. in a series of three PDF pages (on one page), then skip the next three pages, then print the next three, skip the next three, etc. Can someone share with us how this can be done?

---

### Post by entropy1 on 2009-12-24
I guess I was a little confused about what you wanted.
How about this:

Step 1) Suppose you start with a pdf file, call it file1.pdf, with 400 pages, where each page has wide margins.  Then you can use the "convert" feature of gsview that I described in my earlier post to create a new file, file2.pdf, with 400 pages.  But now each page has almost no margin.

Step 2) Open file2.pdf with evince and use the "Print to File" option.  Use Page Setup to set the layout to print two pages per side.  Put the output in file3.pdf.  Then file3.pdf has only 200 pages, but each page has twice as much printing.

Step 3) Open file3.pdf with evince.  Use page setup to print only the odd pages.  This time do NOT "Print to File", send the odd pages to a real printer.

Step 4) Take output from printer and put in the paper tray properly oriented.  Open file3.pdf with evince and use page setup to send only the even pages to the printer.

---

### Post by swarup on 2009-12-25
Sounds like a winner! Very good thinking, bro. I haven't installed gsview yet because I was wanting to figure out how to install the Linux version, which I haven't done yet. Often I find that installing an application natively works better, or sometimes has features that the wine version doesn't. Once I get it installed, I'll test what you suggest and report back here. Thanks again for the suggestion. :)

---

### Post by diesch on 2009-12-26
> **swarup said:**
> 
Now, I do have a follow-up question: It seems that both the above applications will allow me to manipulate and configure the PDF files as needed. But once that is done, is there a way for me to tell the printer to print pages 1,2,3, then 7,8,9, then 13,14,15? That way I will be able to manage double-sided printing.

pdfrecycle lets you select individual pages to be included so you can only pages 12,3,7,8,9,...  You can create the input file using a pipe, like


```

 (
   printf 'FILE somefile.pdf\nLAYOUT 1x3\n'; 
   for i in $(seq 0 100); do 
      printf "PAGE $((i*6+1))-$((i*6+3))\n"; 
   done
 ) | pdfrecycle -o the_output

```

But if it's just for printing I'd use *gv* to select even/odd pages, it has some hard to recognize buttons under the "Reload" buttons on the left, the first is "mark odd pages", the second "mark even pages". Use "Print marked pages" to print.

---

### Post by swarup on 2010-01-05
> **entropy1 said:**
> If the original document has wide margins, I have found gsview can be helpful.  Open the document with gsview.  Click on Media and select "User Defined" and choose the page size you want; i.e., the height of the text and the width of the text.

Next, under File choose "Convert".  Click the "Properties" button.  At the bottom of the dialog box you can enter an X and Y offset to move the upper left corner of text toward the upper left corner of the paper.  Click OK, click OK again, enter an output file name.

You will have to experiment to get the offset numbers right.  Eventually, you can make the output pages with almost no margin.

Now when you print multiple pages per sheet, you will have minimum reduction of the print size.

I have been trying the above steps, without success. When one selects "User Defined" and chooses the page size one wants, then should one see an immediate change i.e. in the text size etc? I don't see any change whatsoever in the page when I do this.

Then, when I go to "Convert", and under "Properties" select an X and Y offset and click OK, OK, and output file name, then I get a tiny little 1 cm window on my desktop which will not open, and upon trying to open, instead gives me a text file with the following message:

> GPL Ghostscript 8.64: **** Could not open the file Z:\home\swarup\Desktop\test222.* .

**** Unable to open the initial device, quitting.

I have no idea whether perhaps the settings I am putting for page size or for X and Y are inappropriate, due to which the file cannot be made? I just have no idea what the proper range of numbers is for these settings.

Please guide me how I am to move ahead using this program.

---

### Post by entropy1 on 2010-01-06
I had a similar problem.  I got the error when I specified only a file name but not file type.  For me, the fix was to specify BOTH the output file NAME and TYPE; e.g., outfile.pdf

---

### Post by swarup on 2010-01-06
> **entropy1 said:**
> I had a similar problem.  I got the error when I specified only a file name but not file type.  For me, the fix was to specify BOTH the output file NAME and TYPE; e.g., outfile.pdf

Wow. That made the difference, now at least I get an output file. They should put this instruction in bold letters at the top of their program. :)

Now, I've just made 25 separate versions of the same pdf file, in an attempt to understand how the different parameters you've mentioned-- text height, and offset-- work together. It seems the larger you make the text, the more negative the x and y have to be. My x and y have to be like -30 and -120 respectively in order to keep the print from going off the top of the page. But I have to say, it is a very tricky business trying to get the whole thing properly set on the page. And then in a larger document, say 400 pages, I find that finally getting one page proper does not indicate that the remainder of the pages will also fit properly. I finally settled on 600 by 600 for the page size and height of one document, and got it settled on the screen using -30 x and -120 y. But then several of the other pages of the document did not fit! And obviously, one cannot check each page of a 400-page document.

If you could offer some tips as to how you manage all this?

---

### Post by chewearn on 2010-01-06
I read the posts of this thread, and it seemed to me, it's getting quite complicated just to achieve some paper saving in printing 400 pages.

I like to propose a different solution, one which I used a many of times.

1. Open the file in Evince.
2. Open print dialog.
3. Under "Page Setup" tab, select:
Pages per side: 2
Page ordering: Left to right

4. Under "General" tab, select Range/Pages, and enter the followings into the box next to it.
20,1,18,3,16,5,14,7,12,9

5. Now, click "Print"

After printing is completed (there should be 5 pages), flip the entire stack of papers over for printing on the other side.

Now use the following page sequence:
10,11,8,13,6,15,4,17,2,19

Finally, fold over the papers in half.  Result: you got a mini booklet of 20 pages.

Repeat 20 times for the entire 400-page book; a total of 20 mini booklets.

Here is the printing order for the first 100 pages:
20,1,18,3,16,5,14,7,12,9
10,11,8,13,6,15,4,17,2,19

40,21,38,23,36,25,34,27,32,29
30,31,28,33,26,35,24,37,22,39

60,41,58,43,56,45,54,47,52,49
50,51,48,53,46,55,44,57,42,59

80,61,78,63,76,65,74,67,72,69
70,71,68,73,66,75,64,77,62,79

100,81,98,83,96,85,94,87,92,89
90,91,88,93,86,95,84,97,82,99

I leave it to you to figure out the remaining 300 pages. :)

With additional effort, you could also staple each booklet, tied them together with thread and glue a piece of cardboard on the spine, to create a proper book.

---

### Post by swarup on 2010-01-06
@chewearn: Thank you for the kind suggestion.

It is a nice idea, and quite useful if your print size is otherwise fine. But I am trying to print a Sanskrit text which is several hundred years old, and the print is not so clear and is also small as well. So if I do it your way, it will not be legible. So for me, gsview will be the most practical way to do the task. That way I can expand the size of the text and make it clearer PLUS take up one-fourth the space  it otherwise would have done. Which is important to me, as I will be travelling all over India with it. So I also want to minimize the pages-- while at the same time expanding the size of the text.

---

### Post by entropy1 on 2010-01-06
Swarup,

I was googling around and came across the linux utility pdfcrop.  Use "man pdfcrop" to learn more.  This is great for removing margins.

The extension
[http://code.google.com/p/pdfcrop2/](http://code.google.com/p/pdfcrop2/)

is useful.

You will probably want to put your pdfcrop.pl commands in a script.

---

### Post by swarup on 2010-01-06
Hey, Thanks for the tip! It sounds like a great program. I'm always leery of applications that don't have a GUI, but it looks like it is made for non-computer geeks to be able to use. So I'll have a look and see how it goes.

---

