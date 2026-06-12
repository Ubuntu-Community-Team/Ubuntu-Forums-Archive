---
title: "Keeping It Clean (Hard Drive Organization)"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by TVTrukChik on 2009-01-05
I've downloaded the new Thunderbird beta.  Figured out that I can just put it in my home directory and it will run from there without installation.  But what if I create more users on this machine?  They should be able to run it also.

So, I moved the new Thunderbird to /usr/lib/thunderbird-3.0, and replaced my existing launchers (panel and AWN) with ones that point to the new location, set up permissions (I'm so proud of my newbie self!) and edited the profile.ini to use my original settings.  It's all working fine.  (Bet you weren't expecting to hear *that*!)

Now the questions.  Was that the best place to put the new files (seeing as the original Thunderbird was in /usr/lib/thunderbird)?  And what do I need to change to be able to type "thunderbird" in the terminal and have it start this new version instead of the original?  What's the difference between putting it in /usr/lib and /usr/share?  And what's with the seemingly duplicate directory in /usr/lib64 that I didn't put there?

I've also downloaded the new version of Kompozer (that's supposed to work OK with Intrepid), but am holding off doing anything with it until I am sure this is the right way to be doing things.  I can just see myself with stuff splattered all across the hard drive.

Thanks for any input!

---

### Post by nemilar on 2009-01-05
> 
Now the questions. Was that the best place to put the new files (seeing as the original Thunderbird was in /usr/lib/thunderbird)? 

Personally, I would have put it in /opt.  Wikipedia [claims /opt is for optional software]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), which is what I have always used it for (in the rare event that I do use it...your example, of testing experimental software, is one of the rare cases in which I use /opt).

> 
And what do I need to change to be able to type "thunderbird" in the terminal and have it start this new version instead of the original? 

From the terminal, type:
```
which tunderbird
```

This is the path of the file that is executed when you issue 'thunderbird'.  On my system, I get:

```

jdeprizi@enterprise:~$ which thunderbird
/usr/bin/thunderbird
jdeprizi@enterprise:~$ file `which thunderbird`
/usr/bin/thunderbird: symbolic link to `../lib/thunderbird/thunderbird'

```

A symlink is basically a shortcut, so you can do this:

```

jdeprizi@enterprise:~$ sudo mv /usr/bin/thunderbird /usr/bin/thunderbird.old 
jdeprizi@enterprise:~$ sudo ln -s /usr/lib/thunderbird/new /usr/bin/thunderbird

```

The first command there moves the thunderbird shortcut to "thunderbird.old"; typing this at the command line will launch the old thunderbird.  The second command creates a new symbolic link ('ln' for link, '-s' for symoblic).  The first argument, /usr/lib/thunderbird/new, is the target of the link; change this to be the thunderbird binary of the new version you are using.  The second argument is the name of the link, which is /usr/bin/thunderbird. 


> What's the difference between putting it in /usr/lib and /usr/share? 

/usr/lib/ is where the libraries for programs in /usr are supposed to go.  The binaries go in /usr/bin/, system binaries go in /usr/sbin/, source code goes in /usr/src/, etc...  Shared files go in /usr/share/  Here you'll find a lot of things like locale information and language packs, manuals, icons, etc.  

> And what's with the seemingly duplicate directory in /usr/lib64 that I didn't put there?

lib64 is where the 64-bit libraries go.

---

### Post by snova on 2009-01-05
I second /opt/thunderbird-3.0.

If you want to be able to run it from a terminal, create a symlink in /usr/local (which is like /usr but for locally installed packages):

```
sudo ln -s /opt/thunderbird-3.0/bin/thunderbird /usr/local/bin/thunderbird
```

Replace the first path as necessary.

---

### Post by nemilar on 2009-01-05
You assume that /usr/local/bin comes before /usr/bin in the PATH ;);) which on Ubuntu, it looks like it does. So yes, this definitely works...  My only qualms with it would be that:

(EDIT: I made the poor assumption here that /usr/local/bin/ *doesn't* always come before /usr/bin/   Please correct me if I am wrong.)


a) it is not a universal solution.  While OP does not require something universal, I think it is most helpful to learn to be portable.
b) it "prevents" you from launching the stable version of thunderbird via the command line ("prevents" in quotes because obviously this is not *really* true)

However, your solution is definitely the easiest to implement, which is always a large advantage.

My question would be, Ubuntu seems to not use /usr/local/ at all.  In fact, my /usr/local/ directory is essentially empty (136K, /usr/local/bin having 0 files in it).  

Perhaps the ideal solution, if you are going to keep thunderbird in opt, would be to create /opt/bin/  and add it to $PATH?

I am not really sure of the most proper solution here... but of course, your solution of /usr/local/bin/ (easiest), the /opt/bin/ solution (hardest), and the /usr/bin/ (somewhere in the middle) all work to solve the problem.

> **snova said:**
> I second /opt/thunderbird-3.0.

If you want to be able to run it from a terminal, create a symlink in /usr/local (which is like /usr but for locally installed packages):

```
sudo ln -s /opt/thunderbird-3.0/bin/thunderbird /usr/local/bin/thunderbird
```

Replace the first path as necessary.

---

### Post by TVTrukChik on 2009-01-05
Thanks to both of you for the info... I'll have to read this over a couple of times to digest and understand it completely.  I really appreciate the explanation of what the terminal commands do... seems that often here in the Beginners' forum, people say "type this" but don't explain how exactly it works.  Symlinks are something I don't quite understand yet, so this helps a lot.

---

### Post by snova on 2009-01-05
> **nemilar said:**
> My question would be, Ubuntu seems to not use /usr/local/ at all.  In fact, my /usr/local/ directory is essentially empty (136K, /usr/local/bin having 0 files in it).

That's the point. ;) It's for **local**ly installed programs, that is, anything the package manager doesn't know/care about.

---

### Post by snova on 2009-01-05
> **TVTrukChik said:**
> Thanks to both of you for the info... I'll have to read this over a couple of times to digest and understand it completely.  I really appreciate the explanation of what the terminal commands do... seems that often here in the Beginners' forum, people say "type this" but don't explain how exactly it works.  Symlinks are something I don't quite understand yet, so this helps a lot.

Then let me explain it.

A symlink is a file that is transparently mapped to another file when a program attempts to read from it. There are two kinds of links: hard and soft.

Hard links are indistinguishable from normal files. In fact, if you create a hard link, it is, for all intents and purposes, **the** file. If you delete the original one, it continues to exist, and you can still access the file through the hard link.

Soft links (symlinks) are more like shortcuts in Windows. If a program tries to read from it, they will get their data from the original file, but other than that, they are different files.

Hard links cannot be made across filesystem boundaries (due to the way they work). Symlinks don't even need a legitimate target (such a link is "dangling", or "broken").

ln is the command to create a link, both hard and soft. -s is the switch that flips it into making a soft link (hard is the default). The first file is the target, the second the name of the link. sudo is necessary because otherwise you cannot create files in /usr/local/.

---

### Post by TVTrukChik on 2009-01-06
Thanks again to both of you... a few minutes of your time has helped my understanding immensely. (I'm one of those people who's not happy with "push this button", I have to understand *why and how* pushing this button makes it work.) I'll save this thread for reference and experiment a bit with the new concepts in the morning.  Again, thanks for your time!

---

