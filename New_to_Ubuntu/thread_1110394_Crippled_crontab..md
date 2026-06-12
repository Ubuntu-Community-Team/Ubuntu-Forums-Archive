---
title: "Crippled crontab."
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Langstracht on 2009-03-29
I'm really not at all sure that this is a ubuntu problem.  But perhaps someone can pitch in anyway.

I have long used an alias rather than a relatively complicated file copy command to do periodic specific file type back ups.  

I decided to smarten up and added it to my crontab file which contains a bunch of commands that, to my knowledge, all perform as they should - some daily, some every number of days, some dates of the month, whatever.

But not this new command.  It's set to run daily.  But often does not.  Manually entering the command after noticing a "non-execute", always works.

Anyone have idea what would cause the erratic behaviour?

Oh ... and how to fix it.

---

### Post by MrWES on 2009-03-29
> **Langstracht said:**
> I'm really not at all sure that this is a ubuntu problem.  But perhaps someone can pitch in anyway.

I have long used an alias rather than a relatively complicated file copy command to do periodic specific file type back ups.  

I decided to smarten up and added it to my crontab file which contains a bunch of commands that, to my knowledge, all perform as they should - some daily, some every number of days, some dates of the month, whatever.

But not this new command.  It's set to run daily.  But often does not.  Manually entering the command after noticing a "non-execute", always works.


Anyone have idea what would cause the erratic behaviour?

Oh ... and how to fix it.

post the output of 

```
crontab -l
``` (lower case L)

Bill

---

### Post by llamabr on 2009-03-29
it looks like crontab is running some script you wrote?  If so, also post the script.

---

### Post by asmoore82 on 2009-03-29
You should also note that there is system-wide root-owned crontab at "/etc/crontab"
but also each user has their own personal crontab accessed through the `crontab` command.
this 2nd one is probably the one you should be using to back up personal data.

---

### Post by Langstracht on 2009-03-30
There are 36 lines in the crontab file (all of which, to repeat, work with the exception of one) so I am not about to bore you with all list of all of them.

However sample lines are:

   10 7 *              *  *     export DISPLAY=:0 && amarok
   30 7 *              *  1,3,5 export DISPLAY=:0 && pan
   52  7 *              *  *    xfer

where xfer is alias for:

find -ctime 0 -name "*.mp3" -exec cp {} Desktop/Xfer \;

---

### Post by JohnLM_the_Ghost on 2009-03-30
Do you have extra blank line below the command?
It is a known bug that last command is not run if there's not a blank line below.

Besides I do not know how cron deals with aliases, try putting full command in it!

---

### Post by MrWES on 2009-03-30
> **Langstracht said:**
> There are 36 lines in the crontab file (all of which, to repeat, work with the exception of one) so I am not about to bore you with all list of all of them.

However sample lines are:

   10 7 *              *  *     export DISPLAY=:0 && amarok
   30 7 *              *  1,3,5 export DISPLAY=:0 && pan
   52  7 *              *  *    xfer

where xfer is alias for:

find -ctime 0 -name "*.mp3" -exec cp {} Desktop/Xfer \;

Who's crontab is this from? You as the user, or root's crontab? Because I was wondering what user's .bashrc or .bash_aliases the alias is called from.

Bill

P.S. Second thought; why not just make it an executable script and call to that?

```
#! /bin/bash
find -ctime 0 -name "*.mp3" -exec cp {} Desktop/Xfer \;
```

Then chmod u+x script.sh

---

### Post by Langstracht on 2009-03-30
The problem command isn't the last one in the file (I hadn't known about the "known bug" otherwise I would have sent a differently configured snippet - sorry).

As for replacing the alias with the command.  I've previously done that.  With the same perplexing result - sometimes it works, other times it does not.

---

### Post by kevmitch on 2009-03-30
I know it seems a little silly for a "one liner" like that, but you might try putting it in a file as a script and calling the script from cron. Also do you have a mail set up on your system (e.g., exim4) and a ~/.forward file with your email address? Cron mails the owner of the crontab whenever the command has output.

You could also try redirecting BOTH stderr and stdout to a log file and check it after a failure.

```

find -ctime 0 -name "*.mp3" -exec cp {} Desktop/Xfer \ >> /path/to/logfile 2>&1

```

---

### Post by Langstracht on 2009-03-30
In reply to MrWES, I understood that crontab was always "root".  But perhaps I was wrong.

Since, to repeat, sometimes it works and sometimes it doesn't, do you think in any event that might/could that be the issue?

My thinking was that must mean the "permanent stuff" - where the crontab runs and the command itself - aren't the problem.  But something "outside".  But what?

As for the script idea, sorry but I don't know about them.  And I'm not sure how that would work and/or what your suggestion means.

---

### Post by Langstracht on 2009-03-30
O.k. I just tried your suggested command verbatim (i.e. cut and paste) and, as far as I can tell it did not run.  Nor can I find a logfile.

Perhaps I'm not looking for the right thing.  Or in the right place.

---

### Post by MrWES on 2009-03-30
> **Langstracht said:**
> In reply to MrWES, I understood that crontab was always "root".  But perhaps I was wrong.

Since, to repeat, sometimes it works and sometimes it doesn't, do you think in any event that might/could that be the issue?

My thinking was that must mean the "permanent stuff" - where the crontab runs and the command itself - aren't the problem.  But something "outside".  But what?

As for the script idea, sorry but I don't know about them.  And I'm not sure how that would work and/or what your suggestion means.

Hrmm..well no; if you are logged in as a user and type crontab -e, you are editing that particular users crontab. If you type sudo crontab -e, you are editing the root users crontab. 

Bill

---

### Post by JohnLM_the_Ghost on 2009-03-30
> **Langstracht said:**
> In reply to MrWES, I understood that crontab was always "root".  But perhaps I was wrong.

There are crontab for every user.

Check with:

```
crontab -l
```

and

```
sudo crontab -l
```

and you will probably see different results

---

### Post by Langstracht on 2009-03-30
That's true.

One lists the file.  The other lists nothing.

---

### Post by MrWES on 2009-03-30
> **Langstracht said:**
> That's true.

One lists the file.  The other lists nothing.

Whatever one lists the alias xfer, make sure that user has the alias in their .bachrc or .bash_aliases file.

Bill

---

### Post by Langstracht on 2009-03-30
Actually it is in both .bashrc and .bash_aliases.

But surely that is not the issue.  Sometimes it runs.  So it must be there.  No?  

Then sometimes it does not ...

---

### Post by Barriehie on 2009-03-30
I feel your pain on this one.  I too had an on/off crontab.  I generated this bug report,  [311756]("https://bugs.launchpad.net/ubuntu/+source/cron/+bug/311756") and couldn't find a solution.  It started working again so the bug was closed.  I'ld edit and then check the log and see that the crontab file was loaded and still nothing.  I'ld logout, reboot, change editors, and nothing.  At one point it started working so now I tread lightly.  I didn't notice what version you're running but I know it worked fine under 7.10 and after upgrading to 8.04 was when the issue started.

Barrie

---

### Post by Langstracht on 2009-03-30
Interesting.  I just upgraded to 8.04 too ...

I've tried editing the command (e.g. changing the time), rekeying it, moving up and down in the pecking order ... and the aberrant behaviour continues.  Although apparently only with this one command.

If you do happen to uncover anything I would be delighted to hear.  Otherwise I guess I'm stuck.

Thanks.

---

### Post by kevmitch on 2009-03-30
Sorry, I didn't realise the importance of the final semicolon in your command.

Scripts are just bash commands that you put in files. If you edit a file 

```
gedit xfer
```

and put this in it

```

#!/bin/sh
find -ctime 0 -name "*.mp3" -exec cp {} Desktop/Xfer \; >> /home/<your username>/xfer.log2>&1

```

then save the file and make it executable with

```

chmod +x xfer

```

You can then run the commands in the file by typing that file's name. 

```
xfer
```

The result is very similar to an alias, except that a script can be much more managable when you want to do more complex things or you have strange characters in your commands.

I would also say that a script is more reliable for something like cron because you KNOW a script is there, but it can be difficult to know if cron sees a particular alias depending on where it gets defined. 

It also provides a clear separation between the crontab specification and the commands themselves. The command you're using has some unusual characters that might be messing things up if they are getting interpreted in the wrong context. 

You do however want to quote the full path of the script in the crontab. For example, if the script is in /home/<username>/bin/, you want your crontab entry to look like

```
52 7 * * * /home/<username>/bin/xfer
```

I do recognize the intermittent component to the problem and it may not seem like any of this addresses that. However, making a script and having it output to a log file will make tracking down the problem a whole lot easier. This is because there will be less ambiguity as to how you might expect things to behave.

---

### Post by Langstracht on 2009-03-30
Thanks for taking the time to lead me through this.  I'll try to digest it all and give it a try.

That said, I'm thinking I should NOT be calling this new file xfer however since that name is already aliased.  Or is that the whole point?

---

### Post by JohnLM_the_Ghost on 2009-03-30
> **Langstracht said:**
> I'm thinking I should NOT be calling this new file xfer however since that name is already aliased.  Or is that the whole point?

Hmm... if you provide full pathname, I think it shouldn't be a problem.

And really you could remove the alias at all so you'd only have one copy of the command (script).

If you feel like you're going to use this particular command in terminal (not with crontab) as well, you could put script in /usr/bin folder OR put your script folder's name in $PATH variable. So you'd be able to type only the name instead of full path.

---

### Post by Langstracht on 2009-03-30
O.k. I'll give it a try.  My podcasts download (regularly thanks to crontab!) early in the morning so I'll set this up to run afterward.

If it doesn't work I'll "let you know".  Course, if it does, I will be happy.  But unconvinced. And want it to work daily for a while.

Thanks again for your assistance.

---

