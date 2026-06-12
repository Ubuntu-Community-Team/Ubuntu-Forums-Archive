---
title: "I need math work, is Ubuntu good for me?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by M. Amin on 2010-05-23
Hello everyone,

I'm considering switching to Ubuntu.  But I'm not sure if it suits my work needs.  I will summarize my questions in points:
[LIST]
[*]I use MS Word for my writings, I need full equation editor, does Open Office provide that?
[*]I use some table method in MS Word to number my equations there, can I do that in Open Office? (The method is described [[COLOR="Blue"]here[/COLOR]]("http://blogs.msdn.com/microsoft_office_word/archive/2006/10/20/equation-numbering.aspx"))
[*]I'm using Excel for curve fitting, and also (which is very important) find an equation for the curve generated, Excel can offer linear, logarithmic, polynomial up to the 6th degree and other kinds of regression.  Is that available in Open Office or any other program that works on Ubuntu?
[*]I'm also going to need Matlab, Mathematica or similar programs.  Is there a version of such programs that works on Ubuntu?  But free of course!
[/LIST]
Those are my concerns about switching to Ubuntu, I actually want to but I need to know if it fits my work or not, so I hope someone would help me answer these questions.

Thank you in advance.

---

### Post by ron999 on 2010-05-23
Hi
You can test OpenOffice for yourself by installing it on your Windows PC.

---

### Post by ranch hand on 2010-05-23
You can try Open Office on your current OS.  Many people do.  It is a free download.

[http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

---

### Post by jetsam on 2010-05-23
Here's your tools.

LyX.  Look up tex on wikipedia.  Then do the LyX tutuorial.

Extra credi, Sage.

Go to the Sage website ([www.sagemath.opg](www.sagemath.opg))  Read that, and decide if it is right for you.

Then learn Python.  Start with the... i forgot.  There's a matrix package called numpy, I think. 

That is the stuff you are looking for.

When you get your PHD, you can thank me later.

---

### Post by unmole on 2010-05-23
AFIK, open office can do most, if not all of what you need. Like suggested above, you can try out open office on windows itself. As far as mathematical software is concerned, There is a Linux version of MATLAB. I personally use Qt Octave for my number crunching though.

---

### Post by tom.swartz07 on 2010-05-23
I have Matlab and Maple 13 on my laptop. Dunno how I would be able to crunch some of the Wave Functions that I use for my Quantum Mechanics research without it!

---

### Post by M. Amin on 2010-05-25
Thank you so much guys.  I actually tried OpenOffice and I don't think it suits me at all though.. but I will try other programs that you suggested.
I'm not actually using MATLAB yet, but I know I'm gonna need it soon that's why I asked.
Thank you again people.

---

### Post by meho_r on 2010-05-25
> **M. Amin said:**
> Hello everyone,

I'm considering switching to Ubuntu.  But I'm not sure if it suits my work needs.  I will summarize my questions in points:
[LIST]
[*]I use MS Word for my writings, I need full equation editor, does Open Office provide that?
[*]I use some table method in MS Word to number my equations there, can I do that in Open Office? (The method is described [[COLOR="Blue"]here[/COLOR]]("http://blogs.msdn.com/microsoft_office_word/archive/2006/10/20/equation-numbering.aspx"))
[*]I'm using Excel for curve fitting, and also (which is very important) find an equation for the curve generated, Excel can offer linear, logarithmic, polynomial up to the 6th degree and other kinds of regression.  Is that available in Open Office or any other program that works on Ubuntu?
[*]I'm also going to need Matlab, Mathematica or similar programs.  Is there a version of such programs that works on Ubuntu?  But free of course!
[/LIST]
Those are my concerns about switching to Ubuntu, I actually want to but I need to know if it fits my work or not, so I hope someone would help me answer these questions.

Thank you in advance.
I can only say that you're doing it wrong from the start: using an Office suite for serious mathematical work is plain wrong. The ideal application for high quality typesetting (especially for mathematics), de facto standard in academic milieu and unbeaten champion typography-side for over 20 years is LaTeX. BTW, [LyX](http://www.lyx.org/), suggested by jetsam, is a simple frontend for LaTeX, so you may start with it.

---

### Post by rhm on 2010-06-25
> **M. Amin said:**
> Hello everyone,

I'm considering switching to Ubuntu.  But I'm not sure if it suits my work needs.  I will summarize my questions in points:
[LIST]
[*]I use MS Word for my writings, I need full equation editor, does Open Office provide that?[/LIST]

Open Office provides an excellent Formula Editor that you may use anywhere within the OOo environment. It is similar to MathType, but much lighter and less prone to messing the symbol sizes and other formats. It allows for the equations to be written using the Math language, which is very much like saying the expression out loud. It also gives the option of saving the equations as a different file, which comes in handy when there are equations that are used frequently. Equations don't bog down your document or inflate the size as much as the MS Word equations do, so having a document with many formulas won't slow you down (and make you want to throttle your computer) or crash.

This is what initially sold me onto Open Office, though later I found even greater control using LaTeX. If you will be writing a lot of technical documents with many mathematical expressions, it would be worth your while to learn LaTeX, regardless of the operating system you end up using.

> 
[LIST]
[*]I use some table method in MS Word to number my equations there, can I do that in Open Office? (The method is described [[COLOR="Blue"]here[/COLOR]]("http://blogs.msdn.com/microsoft_office_word/archive/2006/10/20/equation-numbering.aspx"))[/LIST]


Open Office has stronger, saner and far less frustrating cross-referencing capabilities than anything in the MS Office suite. I can't come up with a reasonable argument to sell this to you other than "try it for yourself". When I still used it to write math stuff, I managed to get similar results to those shown in the table method, without going through the same hassle; equation numbering using the table method should be perfectly doable.


> 
[LIST]
[*]I'm using Excel for curve fitting, and also (which is very important) find an equation for the curve generated, Excel can offer linear, logarithmic, polynomial up to the 6th degree and other kinds of regression.  Is that available in Open Office or any other program that works on Ubuntu? [/LIST]


There's a wide array of options to choose from here. If you are an Excel guy, Open Office Spreadsheet will seem slower, but friendlier. Spreadsheet took me the longest to get used to, but then again, I used Excel intensively. That being said, Spreadsheet will fit curves just as well as Excel, with the same options.

Gnuplot is also great for plotting and fitting data. The learning curve is about a weekend long and produces extremely good quality plots.

You may also use Sage, Octave, Scilab or R to do curve fitting and number crunching of different sorts. As someone else posted, check them out and see which one fits you the best. There are also versions of Mathematica, Maple and Matlab for Linux, which might suit you better.


> 
[LIST]
[*]I'm also going to need Matlab, Mathematica or similar programs.  Is there a version of such programs that works on Ubuntu?  But free of course!
[/LIST]


Sage, Octave and Scilab should have you covered. R could be useful, depending on the sort of number crunching you would need to do. Those are the ones you can get for free. 

> 
Those are my concerns about switching to Ubuntu, I actually want to but I need to know if it fits my work or not, so I hope someone would help me answer these questions.

Thank you in advance.

Switching to Ubuntu seems daunting at first but it's a rewarding decision once you get your work tools working for you. If the tools you mentioned are the only ones holding you back, by all means, take the leap. You will be happy you did.

---

