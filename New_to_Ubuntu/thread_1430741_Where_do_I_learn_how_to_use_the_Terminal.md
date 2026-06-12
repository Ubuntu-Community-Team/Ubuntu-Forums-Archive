---
title: "Where do I learn how to use the Terminal?"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by WubiNoob on 2010-03-15
I was trying to install a driver the other day for a wireless card on my laptop, and when I tried to seek help, the only answers I got were long, complex terminal commands that were pages long. I later decided I will eventually need to learn these types of scripts and bash things, so I was wondering where to start.

Is there a reliable source for getting to know the terminal better? I would really like feedback from all the experts, please help a beginner out. Thanks.

---

### Post by Bachstelze on 2010-03-15
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Search for "command line", "terminal", etc..

---

### Post by blur xc on 2010-03-15
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

bm

---

### Post by cerealtx on 2010-03-15
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

restateing whats said, if you want to learn terminal/shell id suggest doing everything even the duh stuff, with terminal, for me it just helps reinforce the ideas and the how to's, and with linux your not always going to have a fancy gui :P

---

### Post by bpalone on 2010-03-15
If you are the book type, you might find a copy of "Linux In A Nutshell", by Siever, Weber, Figgins, Love & Robbins, published by O'Reilly, ISBN-10 0-596-00930-5 useful.

It lists most of the commands, what they do and their syntax.  Pretty dry reading, but a wealth of reference information.  You get to thinking, what was that command, was it abcde, you can look it up before you commit a big mistake or minor one for that matter.

The CLI is very powerful and useful and well worth the time to learn.  I still have a long way to go.  So, with that power one must be careful, or it can be a oops minute and the system is hosed.  So one suggestion would be to either set up a virtual machine with Linux on it, or set up a spare computer just for learning the CLI.  That way if you do make a big oops, nothing really damaged, just some lost time to reinstall.  Which makes a virtual machine the better choice, because you can just make copy of virtual machines disk file as a backup.  Then all you have to do is copy it back and presto, back where you were before.

So, do, by all means take the time to learn the command line.  Just be patient, Rome wasn't built in a day.  You will know when you are getting it...You will sit down at a Windows machine in the command line and type ls -l rather than dir.  Enjoy the journey.

---

### Post by J V on 2010-03-15
Pages long? I doubt it... besides you don't need to memories them, just paste them into the terminal...

---

### Post by blur xc on 2010-03-15
> **J V said:**
> Pages long? I doubt it... besides you don't need to memories them, just paste them into the terminal...

And FYI (to the op) ctrl-shift-v to paste into the terminal.  Ctrl-shift-c to copy.  Ctrl-c and ctrl-v have long had other meanings in the terminal, way before copy and paste even existed.

BM

---

### Post by pastalavista on 2010-03-15
You can find out a lot about commands in the terminal itself with ```
man 'command'
#--and
'command' --help
```

---

### Post by grysbal on 2010-03-15
I started with computers in college a looooong time ago and we learned DOS, it's nice now to relearn CLI with Ubuntu, it's perhaps old fashioned but it gives you absolute control which can be a double edged sword but having that absolute control is, for me, reassuring.

I shall be searching and reading for a long time to learn all I need to know but it's good to have the appetite for learning about computers reignited after MS dampened that in me such a long time ago.

@bpalone Thanks for the advice, I'll look up that book :)

---

### Post by Iowan on 2010-03-15
Sure wish I could remember the (similar) thread that had a link to wallpaper with commands... :(

---

### Post by blur xc on 2010-03-15
> **grysbal said:**
> I started with computers in college a looooong time ago and we learned DOS, it's nice now to relearn CLI with Ubuntu, it's perhaps old fashioned but it gives you absolute control which can be a double edged sword but having that absolute control is, for me, reassuring.

I shall be searching and reading for a long time to learn all I need to know but it's good to have the appetite for learning about computers reignited after MS dampened that in me such a long time ago.

@bpalone Thanks for the advice, I'll look up that book :)

You sound exactly like what I went through.  Back in my dos days I really enjoyed using my computer.  Then I took a short break from computers, and when I got back, Windows took everything over and I was very annoyed and miserable.  I used it because I had to, and I hated it.  I got by, but my normal catch phrase at work was "I hate computers"...  But, Ubuntu has changed that for me.  Using the computer became fun again...  I've been reading command line books and have been working on shell scripting.  It's quite fun, and rewarding...

Although I do recall back in my dos days a batch file that I was working on, going horribly wrong, and before I realized what was happening, I had deleted half my hard drive...  I reinstalled often back then...

Now, VBox is my testbed.  I play, screw up, and don't care!

Good luck, and have fun learning.

BM

---

### Post by jmszr on 2010-03-15
WubiNoob,

I believe this is the wallpaper to which Iowan (post #10) was referring: [http://www.tux-planet.fr/a-linux-wallpaper-for-beginners-un-fond-decran-linux-pour-les-debutants/](http://www.tux-planet.fr/a-linux-wallpaper-for-beginners-un-fond-decran-linux-pour-les-debutants/)

Also: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners) , and this: [http://www.stat.tamu.edu/~dahl/teaching/605/1.20/shell-tutorial/html/](http://www.stat.tamu.edu/~dahl/teaching/605/1.20/shell-tutorial/html/) .

These are good to have: [http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/8/unixlinux-command-cheat-sheet/) and: [http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

---

### Post by lyall on 2010-03-15
> **WubiNoob said:**
> I was trying to install a driver the other day for a wireless card on my laptop, and when I tried to seek help, the only answers I got were long, complex terminal commands that were pages long. I later decided I will eventually need to learn these types of scripts and bash things, so I was wondering where to start.

Is there a reliable source for getting to know the terminal better? I would really like feedback from all the experts, please help a beginner out. Thanks.

for help **UsingTheTerminal**
see the follow link
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

for install a **WifiDocsWirelessCardsSupported**
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

also for other info look at the following link **TitleIndex**
[https://help.ubuntu.com/community/TitleIndex]("https://help.ubuntu.com/community/TitleIndex")


the world is at your fingers if you know how to ask and look

good luck and have fun learning

---

### Post by Barriehie on 2010-03-16
> **Iowan said:**
> Sure wish I could remember the (similar) thread that had a link to wallpaper with commands... :(

I've seen it too and found it [here]("http://tuxtraining.com/2008/10/02/handy-wallpaper-for-basic-linux-commands").

---

