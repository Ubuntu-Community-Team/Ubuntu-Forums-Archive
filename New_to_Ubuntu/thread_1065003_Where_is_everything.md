---
title: "Where is everything?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Jerriy on 2009-02-09
I recently discovered where (which file) newly installed programmes were put by installers "add/remove" & synaptic (home\usr\bin etc)

My question is where is everything else? I want to install a new font in the notepad thing for example. There I notice that there are only four fonts (Classic, Kate, Oblivion & Tango). So I press "add" and guess what? Instead of a file with the four fonts I get "thrown outside" into the main/home location with all of it's "hundreds" of files. I've noticed that this happenes quite a lot (more or less whenever I press the "+Add..." button. 

And since ubuntu files often tend to consist of shorthands and abbreviations, it means that file search is not much of an option.

So my question is what are the names and locations of all those default files for fonts, screensavers and what not? I'm sure it isn't the intention that everytime one presses the add button one is expected to scan all of the files/folders in the home directory just to find default locations

---

### Post by LowSky on 2009-02-09
Why would you press the add button, What are you expecting it to do?

Iff you need new fonts go to add/remove or synaptic and look for ubuntu-resrticted-extras

it will install fonts from windows, java, and flash

---

### Post by Jerriy on 2009-02-09
Thanks for you reply I'll get back to you later (I'm having difficulty reading and posting here (I can't use the quick reply, moreover on-and-off I get this message that the ubuntu apache server is "temporarily unable to service" my request due to maintenance downtime or capacity problems" 

But then I presss the reload button and suddenly I'm in... then I'm out again. Is this also happening at your end?

---

### Post by llamabr on 2009-02-09
Hi.  Yes, there's some weirdness with the forum's web server.  What you need is to type:

sudo apt-get install ubuntu-resrticted-extras

From the terminal, which will install a bunch of extra fonts, and some other goodies.  I'm not exactly sure what you mean by "notepad thingy".  Notepad only works under wine, and you shouldn't be using it -- it's not going to work very well.  If you want a text editor, there are many better ones to install under ubuntu, such as nano, or kile.  Give them a try.

---

