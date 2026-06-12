---
title: "lilypond refuses to execute"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by moose3642 on 2009-05-13
I can't seem to delete this thread entirely, so please ignore it until it dies.

---

### Post by pro003 on 2009-05-13
you need option to run the app, try this little example:


Create a text file called ‘test.ly’ and enter:

    {
      c' e' g' e'
    }


To process ‘test.ly’, proceed as follows:

    lilypond test.ly


You will see something resembling:

    lilypond test.ly
    GNU LilyPond 2.12.2
    Processing `test.ly'
    Parsing...
    Interpreting music...
    Preprocessing graphical objects...
    Finding the ideal number of pages...
    Fitting music on 1 page...
    Drawing systems...
    Layout output to `test.ps'...
    Converting to `test.pdf'...

---

