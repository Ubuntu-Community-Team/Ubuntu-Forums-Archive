---
title: "request suggestions on writting software applications"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by Old Jimma on 2009-07-07
Hi Ubuntu Community:

I've gotten to the point of wanting to write software for some applications that I need. O:)

For example, I need to make name tags for parents of my son's lacrosse team. It would be nice so that parents could begin to know who each other are.

The name tag needs to include:
[LIST]
[*]the parent's name
[*]their son's name,
[*]the number on their son's jersey,
[*]the position that their son plays,
[*]a jpeg photo of their son, and
[*]the "club name" their son belongs to (the team has several "club" levels).
[/LIST]

:p

I've been programming since 1969... but my experience has been entirely in scientific programming. I've programmed in IBM assembler, FORTRAN, COBOL, PL1, APL, SAS, and R. So, I've got a little experience under my belt.

However, I have no idea what language I should use to program this application.

Here are my questions:

[LIST=1]
[*]How should I begin? What language should I use? WILL THAT LANGUAGE BE AVAILABLE IN UBUNTU?:-k
[*]What book should I use to learn that language?
[*]The name tags will need to be printed in color! Will that language allow this?
[/LIST]

Thank you Ubuntu Community!):P

Best regards,
Phil Smith

---

### Post by 3rdalbum on 2009-07-07
For this sort of program (making and printing name tags), you have two options:

1. Openoffice.org Basic. Create a template in OOo for what you want the tags to look like, and then use a bit of Ooo's built-in Basic (it's like Visual Basic For Applications) to generate the names. For added points, put all the names and details in an Ooo Base database, and use Ooo Basic to pull them out and populate the document.

2. Scribus/Python. Create a template in Scribus, and use the inbuilt Python interpreter to populate the template with the details.

Both programs are multiplatform, and can handle colour. There are a number of books around dealing with Openoffice.org, and I imagine at least some of them would deal with Ooo Basic. If you would prefer to use Scribus, you can bring yourself up to speed with the Python programming language by installing the "diveintopython" package from Synaptic and taking a read; it's targetted toward programmers and gives you an introduction into how stuff is done in Python.

The Python Library Reference is invaluable too, download it from [www.python.org](www.python.org).

---

### Post by Mornedhel on 2009-07-07
> **Phil Smith said:**
> Hi Ubuntu Community:

I've gotten to the point of wanting to write software for some applications that I need. O:)

Happens even to the best of us. :)

> **Phil Smith said:**
> For example, I need to make name tags for parents of my son's lacrosse team. It would be nice so that parents could begin to know who each other are.

The name tag needs to include:
[LIST]
[*]the parent's name
[*]their son's name,
[*]the number on their son's jersey,
[*]the position that their son plays,
[*]a jpeg photo of their son, and
[*]the "club name" their son belongs to (the team has several "club" levels).
[/LIST]

:p

Do you have the database somewhere, or will you need to fill it from hand ?

> **Phil Smith said:**
> I've been programming since 1969... but my experience has been entirely in scientific programming. I've programmed in IBM assembler, FORTRAN, COBOL, PL1, APL, SAS, and R. So, I've got a little experience under my belt.

However, I have no idea what language I should use to program this application.

Here are my questions:

[LIST=1]
[*]How should I begin? What language should I use? WILL THAT LANGUAGE BE AVAILABLE IN UBUNTU?:-k
[*]What book should I use to learn that language?
[*]The name tags will need to be printed in color! Will that language allow this?
[/LIST]


About every language is available in Ubuntu. Ubuntu is still Linux, and at its core Linux still appeals to advanced users and programmers. No worries there.

Your general idea sounds like

database/flat text => application => spits out formatted text

About any language would do to write the application, including COBOL. However, I'd recommend a simple scripting language (Python/Perl) over C/C++/any compiled language, since you're not going to use it a lot and it doesn't need to be fast.

There are many books available for any language. Also a lot of resources online, including the official documentation for each language. Results may vary depending the language community.

If it were me, I'd fill a simple flat text file with something like

```
<parent name> <child name> <jersey number> <position> <path to jpeg photo> <club name>
```

This can be made much simpler if you have a convention to associate a number to a club name, and a convention to be able to deduce easily the path to the jpeg from the child name for instance.

Then I'd write a really simple Perl script to translate directly each line into a few lines of LaTeX or HTML, to produce a formatted table of name tags, and finally I'd generate a PDF from LaTeX or print the HTML to a PDF printer.

Edit: 3rdalbum has some interesting ideas. I never used Scribus before and I absolutely dislike OO.o Basic (or Visual Basic for that matter), but it's worth exploring.

---

### Post by Old Jimma on 2009-07-07
My thanks to 3rdalbum and Morndelhel for their really excellent advice!!!!

Many thanks!

Phil Smith
Duluth, GA

---

