---
title: "How do they know that?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Thomas Garman on 2010-02-13
I have been using Ubuntu for almost a year now and I am always running into problems that the forums help me with.

I was just reading another post and I came across the suggestion that the OP should try

sudo apt-get -f install
Well, I wonder:  HOW DOES ANYBODY LEARN THAT?

Where can I find a tutorial that would explain when to use things like "-f" in commands.  I don't even know what to search to find this information.  How could I construct my own terminal commands like the one above just using my own knowledge of what the commands do?

Where does this knowledge come from... and where can I learn it too.  In other words, where is there an explanation of what those commands that people are always suggesting in the forums come from?

---

### Post by HPD2 on 2010-02-13
```
sudo apt-get --help
``` or ```
sudo apt-get -h
```

If you read the man pages or the help files you can get a better understanding of how to use a program.

There is also google.

---

### Post by ankspo71 on 2010-02-13
hi,
I saw that command mentioned too, and I didn't know about that one either. :p Anyways, in most cases we can find info on commands (and programs) by typing any of the three commands in the terminal:

```
man command
info command
command --help
```

90% of what I have learned is from reading these forums.
Hope this helps.

---

### Post by 3rdalbum on 2010-02-13
In some circumstances, apt-get itself will suggest you run that command. But usually I learn things from the man pages.

---

### Post by falconindy on 2010-02-13
I have a small semi-intelligent monkey who dances on my keyboard while I sleep. He writes down a note for any combination of letters that has a positive result.

Also, trial & error, man pages, reading error messages and, to a lesser extent, reading source code.

---

### Post by 2hot6ft2 on 2010-02-14
Learning Linux links are a little old but the basics haven't changed
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

---

### Post by rcayea on 2010-02-14
I have learned the ol' classic way, by having troubles myself and having to fix them. Also, reading a ton of linux-specific books helps. Its true, reading does help. :)

---

### Post by koba101 on 2010-02-14
from all the problems we had to deal with...you sort of get some sort of experience...and there's a lot more to learn

---

### Post by thecliff on 2010-02-14
> **rcayea said:**
> I have learned the ol' classic way, by having troubles myself and having to fix them. Also, reading a ton of linux-specific books helps. Its true, reading does help. :)

Agreed.  When you run into a problem, work to solve it instead of ignoring it or coming up with a work around and be sure to read up as much as you can.  You can check out some books on basic UNIX commands that may prove helpful.

---

### Post by lisati on 2010-02-14
There are a variety of sources of information, some of which have already been mentioned.

When I was first on a computer course many years ago (COBOL! Yuck!), I was doing some reading somewhere and read about the "help" command that's available on some systems. This helped me learn about some commands, and subsequently baffle the tutors with how I knew what to do. One Linux equivalent, "man", has already been mentioned.

Care is needed with this approach so you don't accidentally break something that you can't fix through not knowing what you are doing, particularly if it's not your computer. In other words, *don't blindly run commands unless you're prepared to face the consequences.*

---

