---
title: "Searching for files with ls"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by texpat on 2009-04-21
I'm trying to look for files on my drives. So I use a terminal window and type, for example, *ls *jpg -R* to recursively search for jpeg images. The command only seems to return info from the current directory, though, i.e. it looks like its ignoring the -R switch.

What am I not getting here?

Thanks for any help.

Texpat

---

### Post by Joeb454 on 2009-04-21
You need something along the lines of ```
ls -R / | grep .jpg
``` to find anything with a .jpg extension.

I haven't test the code above, but it should work, there are much better ways of searching though. Using locate may yield better results :)

---

### Post by philinux on 2009-04-21
Yes use locate. but do this first.

```
updatedb

then

locate *.jpg
```

The updatedb does take a short while to execute and does not return any messages.

---

### Post by texpat on 2009-04-21
Thanks Joeb454 and philinux,

The locate solution worked perfectly. I had to 'sudo updatedb' to be able to run it, but that did the trick!

---

### Post by Gen2ly on 2009-04-21
Almost always the options follow the command (e.g. ls -la to list long directories).  I like to use the find command to search-recursively:

```
find . -type f | grep *.jpg
```

The . tells find to start in the current directory, "-type f" is for files ("-type d" could be used for directories), | pipes the command to the grep application, and grep is used to filter the results.

---

### Post by juancarlospaco on 2009-04-21
Beginners search with *ls*, nice...

---

### Post by andrew.46 on 2009-04-21
Hi Dirk,

> ```
find . -type f | grep *.jpg
```

Or to simplify a little you could search home for all jpgs:

```
find $HOME -type f -iname '*.jpg'
```

and to search your entire drive:

```
sudo find / -type f -iname '*.jpg'
```

Mind you if you want to get a little smarter you can also list the size of all of these files as well:

```
find $HOME -type f -iname '*.jpg' -exec du -h '{}' \;
```

Too many possibilities with 'find' :-).

Andrew

---

### Post by Gen2ly on 2009-04-22
Good tip andrew.  I tend torely a little to heavily on grep.

---

### Post by texpat on 2009-04-22
*NOW* we're talking. Thanks a million, guys, I really appreciate all this help.

I've got a bazillion (about 4,5 gigs worth) of files recovered from a damaged hard drive. Recovery didn't rebuild the old directory hierarchy, so I have to manually sort our the important files (mainly photos, music and wordprocessor docs). So I'll end up using the info you provided to locate these and pass the output to a mv command or so to file them away.

As juancarlospaco noted, I'm not a total noob to computers, just to ubuntu.

texpat

---

### Post by Paddy Landau on 2009-04-22
> **texpat said:**
> So I'll end up using the info you provided to locate these and pass the output to a mv command or so to file them away.
You may find *xargs* useful. Type *man xargs* in terminal to find more information.

---

### Post by andrew.46 on 2009-04-22
Hi texpat,

> **texpat said:**
> *NOW*  I'll end up using the info you provided to locate these and pass the output to a mv command or so to file them away.


Perhaps this is a good time to pimp the guide I have just written:

Linux Basics: A gentle introduction to 'find'
[http://ubuntuforums.org/showthread.php?t=1128937](http://ubuntuforums.org/showthread.php?t=1128937)

Down the bottom I very briefly cover xargs which Paddy Landau has mentioned.

Andrew

---

### Post by texpat on 2009-04-22
andrew.46 - just skimmed your tut. This is what I need.

Paddy Landau - cheers for bringing this to my attention.

texpat

---

