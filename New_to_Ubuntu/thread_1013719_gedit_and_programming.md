---
title: "gedit and programming"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-12-17
i didn't know where to post it, so i just do it over here

i am making some easy 'programs' with gedit, to install madwifi for example
so i won't have to give all the commands in the terminal when i upgrade to a new version of ubuntu

i'm using an eeepc, so there were lost of tweeks
i also want some gedit programs for them, but for some tweeks you have to adjust some other gedit files... and i don't know how i can do that trough another gedit file, if you understand what i mean :P

said in an easier way: i'm trying to make some gedit files to tweek my eeepc automatically (that i just have to open the gedit file in terminal and everything just install itself) but i have some problems with tweeks that you have to open a gedit file and change some lines.

for example:
the eeepc doesn't shutdown completely
you have to open /etc/init.d/halt
and add 'modprobe -r snd-hda-intel' behind the 'do_stop () {'
and i don't know how i should add that line at that exact place using an executable gedit file...

---

### Post by howlingmadhowie on 2008-12-17
this is quite confusing. gedit is a text editor. do you mean shell scripts? if so, have a look at one of the various scripting languages. in this case, a seasoned unix programmer would probably write a short program in a language called awk, but perl or similar could do it just as well.

---

### Post by Pjotrovitz on 2008-12-17
Well, you can use the append shorthand:

sudo print "The text you want here" >> the file to append to

This puts the text you want at the end of the file.

But, for the eee, I would strongly recommend another approach:

Take a look at this: [http://www.array.org/ubuntu/index.html](http://www.array.org/ubuntu/index.html)

Solved all my problems with my eee 901.

---

### Post by Dadsgé on 2008-12-17
if shell scripts are executable and editable with gedit then they probably are...
i found this site 'http://www.freeos.com/guides/lsst/index.html', looks like I'm going to be busy for a while

---

### Post by Dadsgé on 2008-12-17
> **Pjotrovitz said:**
> Well, you can use the append shorthand:

sudo print "The text you want here" >> the file to append to

This puts the text you want at the end of the file.

But, for the eee, I would strongly recommend another approach:

Take a look at this: [http://www.array.org/ubuntu/index.html](http://www.array.org/ubuntu/index.html)

Solved all my problems with my eee 901.

but what to do when i need to add a line in the middle of that file...
and i just tried that command, but it gives me 'warning, the mime type ".." is unknown'

---

### Post by Pjotrovitz on 2008-12-17
Don't know what that means. Tested the command I gave you before I posted it, no problem with it on my end.

If you want to insert text into specific places in a file, you need to do a google search for it. I think the best way would be to use a search replace scheme. Just search for "edit files bash" in google.

---

### Post by Dadsgé on 2008-12-17
hmm, but most sites are rather difficult to understand...
i think i'm just going to wait a week or 2, till the Christmas period is over and then i'll ask my teacher :)
(yes i get lessons of linux on school xD )

---

### Post by ByteJuggler on 2008-12-17
What language are you programming in?  How to go about doing what you want will in large part depend on what language you want to program in.  As an aside: gedit is neither here nor there as far as what you want to do - it is only a text editor that you can use to edit text files, or programs for that matter.  It would not form part of the actual solution of automating your edits/configuring your system.  Also, automating the editing of files like you want to do, can be an error prone/difficult process, so be careful.  That said, you can probably do a lot with regular expressions and Unix shell commands like "sed" or "awk", or otherwise Perl or Python programs.

---

### Post by Dadsgé on 2008-12-17
these adjustments are clear, because my system is still running :)
for the moment, i just used sudo's to install things so i didn't use any language except the command line language...
i think it be best if i learned the language which is used in the system files.

---

### Post by ByteJuggler on 2008-12-17
> **Dadsgé said:**
> these adjustments are clear, because my system is still running :)
for the moment, i just used sudo's to install things so i didn't use any language except the command line language...
i think it be best if i learned the language which is used in the system files.

Well, there are several languages used depending on where you look and what exactly you have installed, including the ones I've mentioned...  Shell scripting seems the obvious choice to suggest, but it does mean that you'll also need to learn (in addition to basic shell scripting) the details of the other commands you'll need to use, like sed, cut, grep, etc.  As a result from a certain point of view something a bit more all-encompassing like Python might therefore be better.

As for the changes being clear/easy - yes I'm sure they are to you, but putting that into code that is clear and unambiguous to the computer is not neccesarily the same thing or as easy to do, particularly if you want the script to keep on working when your system files are updated and things get moved around etc.     Even so, like I say, I'm guessing a simple regular expression based approach can work fairly easily in your case (but by the sounds of things, I think you're possibly underestimating what you need to know/learn in order to tackle this in a robust manner.  Or I'm overestimating what you're trying to achieve.  :))

---

### Post by Dadsgé on 2008-12-17
for the moment, i'm just trying to get all my tweeks in a shell script :)
and therefor i need to know how i can change or add some lines to other scripts
but as you say, i might underestimate it :p

---

### Post by ByteJuggler on 2008-12-18
> **Dadsgé said:**
> for the moment, i'm just trying to get all my tweeks in a shell script :)
and therefor i need to know how i can change or add some lines to other scripts
but as you say, i might underestimate it :p

OK, well do:

```
man sed
```

in a terminal window.  See if you can make sense of that.  You can use "sed" to automate edits/changes to files.  You can thus use sed commands in your shell script to make changes you want.

Also see [here]("http://www.cs.rpi.edu/~hollingd/introunix/lectures/regexp.pdf"), [here ]("http://www.catonmat.net/blog/sed-stream-editor-cheat-sheet/"), [here]("http://www.zytrax.com/tech/web/regex.htm") and [here]("http://www.grymoire.com/Unix/Sed.html").

---

