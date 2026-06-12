---
title: "Bash programming frustration"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Diametric on 2010-04-20
Here me out, please.  I am attempting to learn the bash language (for lack of a better phrase) having no previous knowledge of coding of any kind.  So, at this point, I purchased "Learning the bash Shell" and got a bout 100 pages into it before it went beyond my scope.  So, I figured I would back up and and try another book and try to really cover the basics; so I got "Beginning Portable Shell Scripting" which was better that the first, until about page 100....again. 

My problem is this - I'm now two books deep seeing the same results, I get so far and then I feel like the book makes this huge leap and I'm lost.  I've used online tutorials, little classes offered by my work and I still can't seem to get over this steep learning curve.  I consider myself moderately intelligent, computer literate (although I am only a year into Linux) yet I can't seem to find an inexpensive resource to get me through this programming learning curve.  

I get the basics...path name expansion, quoting, variables, etc...but none of the resources I've encountered say "try this real world example".  Am I crazy for thinking there should be a section that says something like "here is a simple script, let's look at each part and understand exactly what the shell is doing"?

Oh well...I feel better now, thanks.  I would feel better, however, if i could write a script other then "hello world"

---

### Post by Iowan on 2010-04-20
Probably not what you were looking for:
[https://help.ubuntu.com/9.04/basic-commands/C/]("https://help.ubuntu.com/9.04/basic-commands/C/")
I could probably find more tutorials - but it sounds like you already have - and found them lacking...

---

### Post by mechro on 2010-04-20
There are loads of script examples with explanatory comments here...

[http://en.tldp.org/LDP/abs/html/index.html](http://en.tldp.org/LDP/abs/html/index.html)

... scroll down to **List of Examples**.

---

### Post by spillin_dylan on 2010-04-20
Personally, I've found the best way to learn scripting is to actually do it.  Figure out what you want your script to do (maybe you already know this), and then just start writing it.  When you're not sure how to make your script do what you need, read up on commands and methods to accomplish your goals.  

_For instance:_

I wrote a Perl script that fetches my computer's IP address and emails it to me, so I can ssh into my computer from wherever I can get my email (and PuTTY on a memory stick).

[INDENT]Step 1:  How can I get my external IP address?
Step 1.5:  Has it changed since the last time we checked?
Step 2:  Parse it into something resembling an email message.
Step 3:  Send that email
Bonus Step 4:  Include command line switches to display IP locally instead of email, silent mode, verbose mode, etc....
Bonus Step 5:  Keep track of all IP addresses in a log file.
[/INDENT]

Some of these steps are way easier to solve than others, but that's all part of learning!  

P.S.  I originally was going to write this in Bash, but ended up switching to Perl because of the simplicity of sending an email from Perl.

---

### Post by Poincare101 on 2010-04-20
bash "programming" always frustrates me.
One thing you can do (if you're at the part with if loops and while loops and stuff), is learn something like perl or python or C (the last one is not a good idea), and then come back. It helps, a lot.

---

### Post by d3v1150m471c on 2010-04-20
So write a script other than hello world. Learn what commands do what and familiarize yourself with characters.

---

### Post by Diametric on 2010-04-20
Spillin_Dylan...thanks.  Pretty good advice.  That's what I've been attempting to work out...how to apply what I've learned...but, I don't really have any data sets.  However, you've given me some good ideas.  Maybe I'll try and actual language like Perl, and see if I'm able to learn that, then see how I translate to bash...?

---

### Post by spillin_dylan on 2010-04-20
I'd definitely suggest (especially if you're used to the linux command line at all) sticking with Bash for a while.  It seems (to me at least) to be a lot simpler, and while Perl has a LOT of power and flexibility, it certainly can be difficult to learn.  Okay, maybe not difficult to learn, but definitely difficult to master.  

Anyhow, I'm still not sure of you purpose for writing a script, but I'd suggest starting with something simple, such as move all "*.jpg" files from your home directory (or better yet, the present working directory!) to your ~/Pictures folder.  This shouldn't be too hard to start with, as it is essentially a bunch of linux commands you (hopefully) already know.

---

### Post by conradin on 2010-04-20
Perhaps this will be up your alley:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

or

[http://www.freeos.com/guides/lsst](http://www.freeos.com/guides/lsst)

---

### Post by gmargo on 2010-04-21
> **Diametric said:**
> Am I crazy for thinking there should be a section that says something like "here is a simple script, let's look at each part and understand exactly what the shell is doing"?

You're not crazy.  But shell script isn't so much about the actual shell.  It's really about driving other tools, like the hundreds of command line utilities included with Unix/Linux.  So once you have a task in mind, which can be solved on the command line, you can automate with the shell.  If the task is more difficult, then move up to a higher level language like Perl or Python.  Many complex things can be done in Bash, but that doesn't make it the best tool for every job.  You don't say what's on page 100 of those books, but I'd guess it's about where Bash becomes the wrong tool.

Anyway, on another subject: If you're looking for something to analyze (for fun!), you have hundreds of examples at your fingertips:```

$ cd /usr/bin
$ file * | grep "shell script"

```Just that one directory turns up 418 shell scripts on my Hardy system.

And I agree with spillin_dylan, the best way to learn shell scripting (or any language) is to do it.  You just need to figure out something to do. I've written many over the years, so here's a list of just a couple to give you some ideas.  Most are very simple.  Many of them amount to just a way to remember options.

[LIST=1]
[*]add_svn_props: adds extra Subversion properties.
[*]backup_mp3_with_rsync.sh: Sync mp3 directories with my backup device.
[*]corehogs: determines disk usage below this point, generates "CoreHogs" file.
[*]days: calculate number of days between now and ?.
[*]diffall: helps to "diff" between two directories.
[*]epoch: translate date to/from epoch time.
[*]header: set xterm title and/or icon text
[*]lame_all_192vbr: run 'lame' on *.wav to create .mp3 with various options.
[*]pop: drives a perl POP3 script
[/LIST]

---

### Post by quadproc on 2010-04-21
> **spillin_dylan said:**
> I'd definitely suggest (especially if you're used to the linux command line at all) sticking with Bash for a while.  It seems (to me at least) to be a lot simpler, and while Perl has a LOT of power and flexibility, it certainly can be difficult to learn.  Okay, maybe not difficult to learn, but definitely difficult to master.  
Agreed.  Perl is a composite of several philosophies all in one wrapping and it is fairly "loose"; that is, Perl doesn't have the tight structural requirements of a language such as bash or C.

I looked for book reviews on Bash a while back and found that most of the reviewers criticized the books that they had read.  I did find one review about Pro Bash Programming by Chris Johnson, which seemed to get a reasonable report but I haven't seen the book myself.

I think that part of the difficulty in learning bash programming is that the language does not "read" well; in other words, you have to stop and think about what each piece of a statement will do.  This contrasts to a language wuch as WFL where a statement might be something like
```
COMPILE (JOHN)TEST/PROGRAM/FOR/IPC/CONCEPTS AS (JOHN)TEST/X; IF COMPILEDOK THEN RUN (JOHN)TEST/X ELSE ABORT "COMPILE FAILED.";
```Code to do the same things in bash would be something like
```
cc /HOME/JOHN/TEST/PROGRAM/FOR/IPC -o /HOME/JOHN/TEST/X
if [ $? -eq 0 ] then . /HOME/JOHN/TEST/X
else
     echo "COMPILE FAILED"
     exit 1;
fi
```The concepts are identical but the readability is very different.

quadproc

---

### Post by Diametric on 2010-04-21
Thanks for the replies. I think I've got some good ideas now about how to move forward and try and manipulate some files.
 
One last question, none of the books so far ever exlains why a script flows in certain way...can anyone explain this?
 
EDIT:  I can't get teh text to display the way I want...so instead
 
first line would be here
this line would be partially indented
the one more so than the one before
 
skip a line but not sure why
indention begins again
 
 
So, I'm trying to figure out why the scripts follow this pattern

---

### Post by quadproc on 2010-04-21
> **Diametric said:**
> ...
One last question, none of the books so far ever exlains why a script flows in certain way...can anyone explain this?
 
EDIT:  I can't get teh text to display the way I want...so instead
 (about indentation)

Most computer languages are free form; that is, the position of the text in a line does not matter.  There are a couple of exceptions but we're not using them here.:)

The purpose of columnizing is to show the reader at a glance which portions of the code are grouped together.  Perhaps a simple example:

```

#!/bin/bash
if [ ! some_condition ] ; then
     echo "The condition is true"
     rm "somefile"
else
     echo "The condition is false so we will create the file"
     ls > "somefile"
fi

```
quadproc

---

