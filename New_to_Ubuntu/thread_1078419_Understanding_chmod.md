---
title: "Understanding chmod"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-23
[B][SIZE="4"]d = directory

l = link

- = regular file

c = ?

p = ?

s = ?[/SIZE][/B]

---

### Post by taurus on 2009-02-23
```

OPTIONS
       Change the mode of each FILE to MODE.

       -c, --changes
              like verbose but report only when a change is made

       --no-preserve-root
              do not treat ‘/’ specially (the default)

       --preserve-root
              fail to operate recursively on ‘/’

       -f, --silent, --quiet
              suppress most error messages

       -v, --verbose
              output a diagnostic for every file processed

       --reference=RFILE
              use RFILE’s mode instead of MODE values

       -R, --recursive
              change files and directories recursively
       --help display this help and exit

       --version
              output version information and exit

       Each MODE is of the form ‘[ugoa]*([-+=]([rwxXst]*|[ugo]))+’.

```
Or

```
man chmod
```
for more info.

---

### Post by llamabr on 2009-02-23
I'm not sure I understand your question.

One thing you don't want to do is read the man page for chmod.  It's discouraged here.

But if you phrase your problem as a question, I think I can walk you through every detail of a solution.

---

### Post by geirha on 2009-02-23
I assume you are referring to the first letter of each line in the output of "ls -l"? That has nothing to do with chmod, those cannot be changed, they just indicate what type of file it is.

[http://en.wikipedia.org/wiki/Unix_file_types](http://en.wikipedia.org/wiki/Unix_file_types)

---

### Post by mistypotato on 2009-02-23
thanks but I think you've all misunderstood :p

When you do an ls -al, you see a list of all the files in that directory.
in front of many of them is a letter..."l", "d" or "-" usually.
Sometimes there are OTHER letters....like "c" or "p" or "s"


I simply want to LEARN what those other letters mean.  Thats all.

I already know what l, d and - stand for.



How about the other?

---

### Post by glotz on 2009-02-23
[QUOTE=taurus]
```
man chmod
```
for more info.[/QUOTE]
[color=red]You have received an infraction at Ubuntu forums![/color]

It's not allowed to say **rtfm**.

---

### Post by geirha on 2009-02-23
> **mistypotato said:**
> How about the other?

Read the link in my previous post.

---

### Post by llamabr on 2009-02-23
Ah, well, in that case, I revise my previous note discouraging you from reading chmod's man page, and now discourage you from reading the man page for ls.

FWIW, I never, or hardly see those.  Can you post a small sample?

---

### Post by taurus on 2009-02-23
> **glotz said:**
> [color=red]You have received an infraction at Ubuntu forums![/color]

It's not allowed to say **rtfm**.

Too bad this is not an interactive forum or else I could show you what an infraction looks like.

---

### Post by llamabr on 2009-02-23
> **taurus said:**
> Too bad this is not an interactive forum or else I could show you what an infraction looks like.

Seriously, though, we can all agree that Absolute Beginners can not navigate the complicated nomenclature of the technical manual, and so to suggest that they do so is to insult their intelligence.  As I've been warned before, if you can't guide them step by step through the solution, leave off, and let someone else do so.

Reading the manual is not advice we offer here.

---

### Post by tarps87 on 2009-02-23
d = directory
l = symbolic link
s = socket
p = named pipe
- = regular file
c= character (unbuffered) device file special
b=block (buffered) device file special 

From:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)


> **llamabr said:**
> Seriously, though, we can all agree that Absolute Beginners can not navigate the complicated nomenclature of the technical manual, and so to suggest that they do so is to insult their intelligence.  As I've been warned before, if you can't guide them step by step through the solution, leave off, and let someone else do so.

Reading the manual is not advice we offer here.

at no point was it said "rtfm", I can see no harm in telling a user that there are manual page and how to use the, how else will they learn. If the op was told to rtfm then yes there is a problem but to hide a useful source of information is not the way to go

---

### Post by llamabr on 2009-02-23
> **tarps87 said:**
> d = directory
l = symbolic link
s = socket
p = named pipe
- = regular file
c= character (unbuffered) device file special
b=block (buffered) device file special 

From:
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)




at no point was it said "rtfm", I can see no harm in telling a user that there are manual page and how to use the, how else will they learn. If the op was told to rtfm then yes there is a problem but to hide a useful source of information is not the way to go

I thought the same thing, but have been "warned" by administrators not to assume newbies can read man pages, and so not to offer it.

I think it's dumb advice, too.  But I'm just trying to help enforce the guidelines.

---

### Post by mistypotato on 2009-02-23
thanks tarp87

just what I was looking for :D


Seemed like a legit question....not sure why that left others so dazed and confused :confused:

---

### Post by Old *ix Geek on 2009-02-23
> **llamabr said:**
> Seriously, though, we can all agree that Absolute Beginners can not navigate the complicated nomenclature of the technical manual, and so to suggest that they do so is to insult their intelligence.I don't want to start a riot, but I have to say this: That's nonsense!  Twenty-four years ago, when I first started using *nix, ALL I did was RTFM.  That's how I learned everything I needed to know about programming and administering *nix systems.  Later on I started buying books, but it was definitely the manuals that I relied on EVERY DAY at first.  I think it's silly to assume that beginners can't understand man pages. :rolleyes:  In my opinion, that's MUCH more of an insult to their intelligence than the other way around.

---

### Post by mistypotato on 2009-02-23
> **Old *ix Geek said:**
> I don't want to start a riot, but I have to say this: That's nonsense!  Twenty-four years ago, when I first started using *nix, ALL I did was RTFM.  That's how I learned everything I needed to know about programming and administering *nix systems.  Later on I started buying books, but it was definitely the manuals that I relied on EVERY DAY at first.  I think it's silly to assume that beginners can't understand man pages. :rolleyes:  In my opinion, that's MUCH more of an insult to their intelligence than the other way around.

Old ix,

We all have to realize that people come to Linux/Ubuntu and this forum for different reasons.

Some are here because they want to leisurely play with and learn Linux.
Some are here because they have to be...school assignments, job requirements etc
Some are hear for the fun of it.
Some are here out of necessity.
Some are here to help others because they can and they get a sense of satisfaction from it.

Whatever the reason, it's probably not correct to state that the way you may have done it is right for everyone else. (that was figured out far more than 24 years ago :)

In my case, I suddenly needed a server and Windows (IMHO), is no longer the OS of choice.

It is a testament to the great work of others and this community at large that I was able to download, install  and get a Linux server up and running at all.  And, even though I have managed to blow out my server a few times, it is an amazing thing nonetheless and I'm here to stay.

As I don't currently have the luxury of time on my side, I was thrilled to learn that there are many people here willing to give their time to help and save me countless hours of research:D  , much of which research does not always result in the discovery of the answer needed at the moment...nor written to my current level of understanding.

I plan on being a ubuntu'er from now on.  I plan to support the cause financially and I plan to help others who come along and are new to Linux as my knowledge expands.

So, maybe we should let each individual decide what insults their intelligence and let those who give assitance, decide what they think merits their help....or not  :D

Just my 2 cents

---

### Post by Old *ix Geek on 2009-02-23
Oh, I completely see what you're saying, misty, but my point is that not ALL newbies are clueless and unable to comprehend man pages.  That's all. :)

---

### Post by llamabr on 2009-02-23
> **Old *ix Geek said:**
> Oh, I completely see what you're saying, misty, but my point is that not ALL newbies are clueless and unable to comprehend man pages.  That's all. :)

Probably true, and yet the code of conduct on this forum seems to be to assume the opposite.  Users come here to have someone else solve their problems, not to understand how their systems work.  If all you can do is advise a place or a document that teaches the latter, then you should comment elsewhere.

That's how I've been advised, in any case.

---

### Post by Old *ix Geek on 2009-02-23
> **llamabr said:**
> Probably true, and yet the code of conduct on this forum seems to be to assume the opposite.  Users come here to have someone else solve their problems, not to understand how their systems work.  If all you can do is advise a place or a document that teaches the latter, then you should comment elsewhere.

That's how I've been advised, in any case.Until reading this thread I never even KNEW about this 'code of conduct' here. Luckily, I've NEVER told anyone here to RTFM, so I guess that's why I've never been warned! :)

---

### Post by rrashkin on 2009-02-23
I'm a newbie for sure.  I'm not insulted by direction to the MAN pages.

that said, I seemed to have lost lock: was this about "chmod" or "ls"?

---

### Post by tarps87 on 2009-02-24
It is to do with the output from ls -l (I think) usaly you only see the d for directory and l for a link

**d**rwxrwxrwx 	4	george	team1	122	Dec 12 18:02	Projects

---

