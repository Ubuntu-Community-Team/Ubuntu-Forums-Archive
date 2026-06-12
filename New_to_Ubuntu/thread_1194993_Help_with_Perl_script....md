---
title: "Help with Perl script..."
date: 2009-06-23
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-06-23
This Perl script allows the user to issue command to the computer and control it from the terminal. I'm wondering if it is possible to code keyboard shortcuts for example such as ctrl+S for saving documents or ctrl+O for opening one. 

I've been looking for it online but if someone knows about a good advanced Perl tutorial or would point me to the right direction, I would appreciate it.

Just in case, you didn't understand what I'm trying to do, here it is again: I want to be able to code so the script can execute keyboard shortcuts when the command is typed i.e., if I type 'save documents' the script recognizes it and saves it for me...

Or maybe there's another approach to this...

Thanks!

---

### Post by DGortze380 on 2009-06-23
Looks like you want to look at Term::ReadKey

This may be difficult to script due to threading issues, easier in a compiled language.

---

### Post by Mornedhel on 2009-06-23
The Term::ReadKey module, available through CPAN or the repositories, should provide what you want.

Read the output of "perldoc -q keyboard", assuming you have installed the Perl documentation. You have, right ?

---

### Post by sylvainrb on 2009-06-23
For the Term::ReadKey module and the others listed in the documentation, you said that they are available through CPAN or the repositories, so do I need to install them or are they already integrated in Perl? How do I get them if I need to?

@DGortze380:
I think it would be easier in a compiled language as well, but do you know which one would be more suited for string matching, launching and controlling programs? My knowledge in programming is still limited hehe...

Thanks!

---

### Post by DGortze380 on 2009-06-23
> **sylvainrb said:**
> For the Term::ReadKey module and the others listed in the documentation, you said that they are available through CPAN or the repositories, so do I need to install them or are they already integrated in Perl? How do I get them if I need to?

@DGortze380:
I think it would be easier in a compiled language as well, but do you know which one would be more suited for string matching, launching and controlling programs? My knowledge in programming is still limited hehe...

Thanks!

Most of my experience (not by choice) is in .NET C# ... would be only a few lines there.

I'm partial to the C family, so for use on Ubuntu I personally would try C++. I'd have to go look up the libraries though.

---

### Post by Mornedhel on 2009-06-24
> **sylvainrb said:**
> For the Term::ReadKey module and the others listed in the documentation, you said that they are available through CPAN or the repositories, so do I need to install them or are they already integrated in Perl? How do I get them if I need to?

It's the libterm-readkey-perl package. You can check if it is installed already with a one liner that just requires the module and exits.

> **sylvainrb said:**
> @DGortze380:
I think it would be easier in a compiled language as well, but do you know which one would be more suited for string matching, launching and controlling programs ?

There is no language more suited than Perl to string matching.

---

### Post by sylvainrb on 2009-06-24
@Mornedhel:
Thanks got it. It was already included.

Also you're right string matching with Perl was easy to my surprise. Do you know of any good Perl tutorial that is more advanced than just the beginner ones?

---

### Post by Mornedhel on 2009-06-25
You can try the included documentation. Several pods are designed for beginners. Just type perldoc [podname]. "podname" can be any module name, or one of several from the Perl online manual. perldoc perl gives many pointers :

```
Overview
           perl                Perl overview (this section)
           perlintro           Perl introduction for beginners
           perltoc             Perl documentation table of contents

   Tutorials
           perlreftut          Perl references short introduction
           perldsc             Perl data structures intro
           perllol             Perl data structures: arrays of arrays

           perlrequick         Perl regular expressions quick start
           perlretut           Perl regular expressions tutorial

           perlboot            Perl OO tutorial for beginners
           perltoot            Perl OO tutorial, part 1
           perltooc            Perl OO tutorial, part 2
           perlbot             Perl OO tricks and examples

           perlstyle           Perl style guide

           perlcheat           Perl cheat sheet
           perltrap            Perl traps for the unwary
           perldebtut          Perl debugging tutorial

           perlfaq             Perl frequently asked questions
             perlfaq1          General Questions About Perl
             perlfaq2          Obtaining and Learning about Perl
             perlfaq3          Programming Tools
             perlfaq4          Data Manipulation
             perlfaq5          Files and Formats
             perlfaq6          Regexes
             perlfaq7          Perl Language Issues
             perlfaq8          System Interaction
             perlfaq9          Networking
```

The same documentation is available at [http://perldoc.perl.org](http://perldoc.perl.org). If you need a step by step introduction to Perl, I have found the Llama book to be very good : [http://oreilly.com/catalog/9780596520106/](http://oreilly.com/catalog/9780596520106/)

---

### Post by sylvainrb on 2009-06-25
Thanks! I did find the tutorials in the perldoc last night. That should be enough information to keep me entertained for a while...

---

