---
title: "RAR password recovery"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by Mariane on 2009-10-19
Hi, 

This is following this thread which is now archive but has not really been answered: 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=388152](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=388152)

Is there such a program for Ubuntu, please? I am using Kubuntu but I would not mind having to open a Gnome session for this, (which is why I tagged "Ubuntu" and not "Kubuntu"). But I would much rather not have to use wine as I don't have it installed and I have no previous experience of it. 

Mariane

---

### Post by Sarmacid on 2009-10-19
The last post on that thread explains how to crack the rar file, and it won't depend on wether you use gnome or KDE.

---

### Post by t0p on 2009-10-19
> **Mariane said:**
> Hi, 

This is following this thread which is now archive but has not really been answered: 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=388152](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=388152)

Is there such a program for Ubuntu, please? I am using Kubuntu but I would not mind having to open a Gnome session for this, (which is why I tagged "Ubuntu" and not "Kubuntu"). But I would much rather not have to use wine as I don't have it installed and I have no previous experience of it. 

Mariane

Read through that thread again.  The last post gives detailed instructions on how to use a .rar-cracking program, using Ubuntu, Kubuntu, Xubuntu, or any Linux distro.

Gotta admit though, I'm surprised cracking a .rar archive is as easy as running a program.  Those things are password-protected for a reason.  Last time I looked into the subject, I was told to forget it.  Use social engineering/knowledge of the archive maker (like if you know his daughter's middle name you may be able to use that inside info) or give it up.

Do us a favour.  If rarcrack works okay, please report back.  The OP of that thread you linked to is a real dick, disappearing like that.

---

### Post by t0p on 2009-10-19
Thought I'd just add: the instructions on how to install rarcrack work fine.  I just copied and pasted them, and now I have rarcrack installed.  I dunno how well the program works though.  If someone wants to post a link to a password-protected .rar archive, I'll tell you how it goes.

---

### Post by hyperAura on 2009-10-19
u can create a rar password protected file urself m8.. that way u dont have to waste bandwidth..:)

---

### Post by t0p on 2009-10-19
> **hyperAura said:**
> u can create a rar password protected file urself m8.. that way u dont have to waste bandwidth..:)


Yes you're quite right.  When I made that post I didn't have any software installed that would create a .rar archive.  But in the meantime I installed rar, and made a password-protected .rar archive to test rarcrack on.

And guess what: rarcrack is a bunch of crap!  To be precise: rarcrack is a brute forcer.  This means that it tries every possible combination of characters, one at a time.  To crack a weak password will take quite a while.  To crack a *strong* password will take forever.  Or until the heat death of the universe at least.  Seriously, you'd be better off searching the internet for an unprotected archive that contains the same files.

**A better idea** would be to use Google or one of its kind to **search the internet for the password**.  You could do this by searching for the name of the archive, or the name of the archive plus the word "password".  See, if the archive was uploaded to a file sharing site like rapidshare, the owner of the archivge may well have advertized its existence by posting its link on a website (there are several sites that exist to carry these kind of links).  If the owner *did* post the link, he will have also posted the password.  Alternatively, someone else may have discovered the password (through social engineering or a similar trick) and *he* may have posted the password.  Either way, a search for the password is most likely a better way to spend your time than using rarcrack or its ilk.

Brute-forcing strong passwords is a waste of time.

---

### Post by t0p on 2009-10-19
Incidentally, I downloaded rarcrack using rickycodie's instructions at the end of [this thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=388152").  So I didn't see any notice about it being an "evaluation copy" that I need to register.  But when I run rarcrack from the command line, it tells me "Evaluation copy. Please register."

So, can someone please tell me where I can find instructions to register it?

**EDIT:** Never mind.  I found a copy of the EULA at /usr/share/doc/rar (where I should have looked in the first place. God I'm a dumbass!) and the dev wants me to buy a license after 40 days!  Ain't gonna happen!

---

### Post by Mark Phelps on 2009-10-19
I can tell you from experience that, unless the password for the rar file is VERY SIMPLE, any password cracking program you run is going to be a waste of time.  And by VERY SIMPLE, I mean something like "ABC".

Why?

Because password-cracking programs work in several different ways.  One approach uses a dictionary of known words and phrases.  If the password is in that dictionary, then you WILL be able to crack the password.

A more frequent approach is known as brute-force and is just that, the password cracking "engine" generates a sample password, tests it against the archive, then changes one character in the password -- and tries again.  It keeps doing this changing a single character through all possible settings, and then does the same thing with the next character.  It doesn't take a very long password for the number of permutations to get into the MILLIONS.

A password such as "AnyTH#NG$123XXX-@b45" could take WEEKS for you to crack! Why? Because it contains lowercase letters, uppercase letters, numbers, and special symbols -- and is 20 characters long.

And, don't believe what you've seen in the movies about password crackers being able to gauge progress by cracking one character at a time and remembering which specific characters worked. That's the movies and that's NOT how password cracking works -- it's an all-or-nothing proposition, either a particular password works or it doesn't.  You don't get partial credit.

---

