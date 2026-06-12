---
title: "running, ps"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by callowschoolboy on 2011-01-04
I have 2 questions:

1) What is used to run executables when I click on the diamond shaped gear icon?  The background, why I ask, is on the command line I gave game.bin +x and ran it no prob, it expanded a folder elsewhere with game2.bin that wouldn't run, I just use
```
chmod +x game2.bin
. game2.bin
```but then when I window to the new folder and just double click the game runs fine!

2) I have programs that hang (often games ;).  I thought I was clever, opened up a terminal and entered ps; just itself and bash came up!  Where is the real command line, that has all the processes I'm running like Firefox for instance?

---

### Post by blind2314 on 2011-01-04
```
ps -ef
```

That will give you an extended process listing, it's what I use at work most often.

---

### Post by A_M_S on 2011-01-04
To find a specific application you can use:

```

ps -ef | grep application_name

``` 


To find firefox:


```

ps -ef | grep fir
ams       4934     1  0 03:27 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.13/firefox
ams       4939  4934  0 03:27 ?        00:00:00 /bin/sh /usr/lib/firefox-3.6.13/run-mozilla.sh /usr/lib/firefox-3.6.13/firefox-bin
ams       4943  4939 16 03:27 ?        00:00:10 /usr/lib/firefox-3.6.13/firefox-bin
ams       4992  4782  0 03:28 pts/1    00:00:00 grep fir

```


for more information about ps type

```

man ps

```

---

### Post by callowschoolboy on 2011-01-05
Thanks guys!  That explains the second question real well.

As for my first question, I forgot to give some background.  I am running Lucid Lynx, and the second file has no extension.  The game is Braid, so what I downloaded was braid.bin, what it created is just 'braid'.  The icon I described seems to correspond to "Autorun Prompt."   is that some program or script at a very low level that is invoked when I double-click in a window on the file 'braid'?  How is it different from my failed attempts to run it on the command line, seen below:
```
keldrew@Lappy:~$ cd braid
keldrew@Lappy:~/braid$ . ./braid
bash: .: ./braid: cannot execute binary file

```
??

---

### Post by blind2314 on 2011-01-05
I didn't know Braid was compatible with Linux/Unix (besides Wine of course). If it's Windows/OS X only like I think it is, you'll need to use Wine to run it under Ubuntu.

---

### Post by yeats on 2011-01-05
```
keldrew@Lappy:~$ cd braid
keldrew@Lappy:~/braid$ . ./braid
bash: .: ./braid: cannot execute binary file

```

The first "." is actually a shortcut for the "source" command  (see [here]("http://ss64.com/bash/period.html") for details).

What you want to do to run an executable from its directory is to do:

```
./*filename*
```

where *filename* is the executable file's name.

Though it sounds like you'll need wine for this particular program, you should still know these basics ;-).

---

### Post by callowschoolboy on 2011-01-06
I think I get it: the source command is for shell scripts, whereas what I have is its own critter, nothing to do with bash?

Also, Braid was released for Linux as part of the Humble Indie Bundle #2.  I didn't see anything specifically on the official Braid site but I'm almost certain Steam would have the Linux version too.

---

