---
title: "Bash Question"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by Diametric on 2010-01-09
So, my book is going over the bash profile.  Has the file .bash_profile (as is the file mentioned in the book) been replaced by .bashrc?  I can open and view the .bashrc file by typing 

```

```vi ~/.bashrc```

```

But not the .bash_profile.  What am I missing?

Thanks.

---

### Post by rp3 on 2010-01-09
> **Diametric said:**
> So, my book is going over the bash profile.  Has the file .bash_profile (as is the file mentioned in the book) been replaced by .bashrc?  I can open and view the .bashrc file by typing 

```

```vi ~/.bashrc```

```

But not the .bash_profile.  What am I missing?

Thanks.

This Explains it pretty well, click [[COLOR="Red"]HERE[/COLOR]]("http://digg.com/linux_unix/Difference_between_bashrc_and_bash_profile")

---

### Post by J V on 2010-01-09
A .bash_profile file apparently...

Nah, missing here too, how old is the book? usually by the time tech books are published they are already out of date...

---

### Post by Diametric on 2010-01-09
Here is the book: [http://www.amazon.com/Learning-bash-Shell-Nutshell-OReilly/dp/0596009658/ref=pd_bbs_sr_1?ie=UTF8&s=books&sr=1-1](http://www.amazon.com/Learning-bash-Shell-Nutshell-OReilly/dp/0596009658/ref=pd_bbs_sr_1?ie=UTF8&s=books&sr=1-1)

Latest edition is 2005.  So, maybe that has something to do with it. Kinda confusing.

---

### Post by falconindy on 2010-01-09
Bash hasn't changed **that** much since 2005 -- .bash_profile is still valid. If it's missing, just create it and it will run on an interactive login.

---

### Post by John Bean on 2010-01-09
The confusion is caused by the need to satisfy a plethora of possible configurations, but in general .profile is used to control login shells, including bash. But if you want bash login shells to behave differently you can create a .bash_profile which bash will use instead of .profile, but other login shells will continue to run .profile. Normally a bash-aware .profile will also conditionally execute .bashrc if bash is in use, so it's pretty rare to see .bash_profile used these days.

Non-login bash shells execute .bashrc when run; .profile  is used only by login shells.

---

### Post by Diametric on 2010-01-09
Why would I need to create it if it's not there already?  What I'm getting at is, if it's supposed to be there, why isn't it?  I didn't remove anything.  From what I gather .bashrc is for subshells one might open and .bash_profile is run upon opening a terminal.  What confusing is I can find .bashrc and not .bash_profile

Thanks for everyones replies.  Cheers.

---

### Post by falconindy on 2010-01-09
You've misunderstood the point of .bash_profile. It is **not** run when opening a terminal -- that's .bashrc. The only time .bash_profile is used is upon an **interative login**. Terminals launched from a DM such as Gnome create non-interactive logins. Please check a site like tldp.org if you're not familiar with the difference between the two.

It's not that it's **supposed** to be there. It's a file that gets sourced **if its present**. Chances are high that if you don't know about .bash_profile, you don't need it. Particularly in a graphical environment (which Ubuntu focuses on) it doesn't get much use. On the other hand, lack of a .bashrc creates a poor user experience in the terminal.

Simply put, it's not there because Canonical felt it wasn't necessary for new users.

---

### Post by Diametric on 2010-01-09
> **John Bean said:**
> The confusion is caused by the need to satisfy a plethora of possible configurations, but in general .profile is used to control login shells, including bash. But if you want bash login shells to behave differently you can create a .bash_profile which bash will use instead of .profile, but other login shells will continue to run .profile. Normally a bash-aware .profile will also conditionally execute .bashrc if bash is in use, so it's pretty rare to see .bash_profile used these days.

Non-login bash shells execute .bashrc when run; .profile  is used only by login shells.

That makes a bit more sense Mr. Bean.  I guess the book must be a little out of date, as it states that "the most important bash file is the .bash_profile" as "these lines define the basic environment for your login account".  What the book states and what I find whilst exploring /etc have some differences.

Thanks.

---

### Post by John Bean on 2010-01-09
Edit: crossing replies have made my comments (below) largely redundant but I'll leave them in for the record.


> **Diametric said:**
> Why would I need to create it if it's not there already?
That makes no sense. The only way it ever gets there is is someone creates it.
>  What I'm getting at is, if it's supposed to be there, why isn't it?You're jumping to conclusions; who said it's supposed to "be there"?
> From what I gather .bashrc is for subshells one might open and .bash_profile is run upon opening a terminal.No, that isn't correct.
> What confusing is I can find .bashrc and not .bash_profileAs I explained earlier, .profile is generally used in preference to .bash_profile unless there is a good reason to do otherwise.

---

### Post by Captain_tux on 2010-01-09
Hey, nice to talk to someone in the DC area!

Yeah, **John Bean** pretty much nailed. I have that book also... it's a wee bit out of date, as Bash is now up to version 4.0 (that book covers version 2.0), so some things in the book will not be compatible with the current Bash.

---

### Post by Diametric on 2010-01-09
Mr. Bean, perhaps you've misread the tone of my reply.  I was commenting on how your reply made sense where the book did not.  Your line by line dissection of my comments are a bit terse.  Instead of "no. that is not correct" how about adding "because of 'x'"...might help in shedding some light on a subject those of us in the Absolute Beginners section could use and appreciate.

Pleasure meeting you Cap't Tux...keep in touch.

Thanks for all the help.

---

### Post by Mornedhel on 2010-01-09
I suggest reading the INVOCATION section in the bash man page. It describes login shells, interactive shells, and when .profile, .bash_profile, and .bashrc are read (as well as their system-wide counterparts).

---

### Post by Diametric on 2010-01-09
Mornedhel - great suggestion.  That part of the man page described it very well.  Thanks for the reply.

---

### Post by John Bean on 2010-01-10
> **Diametric said:**
> Mr. Bean, perhaps you've misread the tone of my reply.  I was commenting on how your reply made sense where the book did not.

Perhaps you missed my comment in the edit; at the time of posting I hadn't actually seen your reply until after I posted, it had seemed that you were disregarding what had already been written. When I did see your post I immediately added the comment at the top, it was pretty clear that the post I "dissected" had also probably been posted before reading my earlier reply. Forum software can (and often does) make the order of posts appear different from that at the time of posting when several posts are made at much the same time.

> Your line by line dissection of my comments are a bit terse.  Instead of "no. that is not correct" how about adding "because of 'x'"...might help in shedding some light on a subject those of us in the Absolute Beginners section could use and appreciate.

That was exactly why it was terse; I had already explained exactly why this was not true in an earlier reply when I described the correct purpose of the different profile files.

Anyway, I hope your original question has now been answered... several times ;-)

---

