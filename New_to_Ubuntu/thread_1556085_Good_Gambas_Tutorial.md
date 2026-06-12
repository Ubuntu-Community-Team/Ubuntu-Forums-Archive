---
title: "Good Gambas Tutorial"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by DaGeek247 on 2010-08-18
I have Ubuntu 10.04 and I am wondering, how do I set up Gambas from beginning to end?

I have used Visual BASIC 6 (I use it, telling me how bad it is won't change a thing.) And I have absolutely no idea where to start to get gambas working. period. I have not ever compiled source code from anything to get it to work.

All I am asking for is a simple easy to use full tutorial on install gambas. Any help would be great!

---

### Post by kalaharix on 2010-08-19
Hi 

Installing Gambas is not difficult. 

You don't have to compile Gambas on UB10.04. The repository version is 2.19 which is not far enough behind the current 2.21 to worry about. There is also an Alpha version of Gambas3 which is compile-only svn sourced.

Do not use the Ubuntu software centre. The installation from there is annoyingly incomplete (if I was paranoid I would suspect sabotage by the Python Mafia :icon_frown:)

Go Applications, Accessories, Terminal and type into the terminal (without apostrophes):

'sudo apt-get install gambas2'

When that has finished installing, you should be able to run Gambas by typing 'gambas2' at the prompt. You can also create a shortcut on the desktop.

The learning curve on Gambas is steep because the documentation is not written for beginners. I think Gambas is superb but I am leveraging my experience of VB. I find it stunningly reliable as a commercial mySQL frontend. I have never worked with application software which is easier to come back to 6 months down the line.

I would say that if I were a new programmer, I would probably choose Python over Gambas for a number of reasons (none of which have anything to do with the quality of the product). The Python documentation is better and the community is wider. There is also the problem that Gambas is, to all intents, a product of a one-man band with less guarantee of continuity.

That does not apply to me: I wrote my first BASIC programmes on an HP9830 and a home-built z80 computer I hand-soldered myself in about 1977. There is no way I am changing now!

Don't believe the guff you read on this forum about 'nobody use basic any more'. There is still more corporate use of BASIC related languages (admittedly mostly legacy) in businesses of all sizes all over the world than Python will ever have.

---

### Post by KIAaze on 2010-08-19
Gambas comes with a lot of examples and I found it easy to get started with (but I had previous programming experience).
However, to use the examples you have to copy them into a directory where you have write permissions.

The documentation is pretty good: [http://gambasdoc.org/help/](http://gambasdoc.org/help/)
Tutorials: [http://gambasdoc.org/help/tutorial](http://gambasdoc.org/help/tutorial)

I created a search plugin for it here: [http://mycroft.mozdev.org/search-engines.html?name=gambas&opensearch=yes](http://mycroft.mozdev.org/search-engines.html?name=gambas&opensearch=yes)

The mailing-list can also be useful.

Here's a program I created with Gambas:
[https://launchpad.net/webcontentcontrol](https://launchpad.net/webcontentcontrol)

It's not 100% gambas (calls various scripts to do its work) and had it not been based on an existing gambas program, I would probably have used something like GTK,Qt or wxWidgets in C++ or their Python bindings.
But using Gambas definitely did help speed up GUI development!

---

### Post by DaGeek247 on 2010-08-19
Yes that answers my question on how to install gambas properly thank you for the help.

---

