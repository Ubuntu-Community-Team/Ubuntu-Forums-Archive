---
title: "text to speech - how to?"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-16
I have laringitis and have been emailing my wife in the house to communicate with her blackberry.  She is trying to help me by not talking to me which makes me want to talk back (even if it's not a question).

Let's say she's sitting on couch and I'm 15 or 20 feet away.  Is there any way for me to type something and have something on Ubuntu speak it aloud.

Perhaps openoffice word then click something or a specialized program i could download?

thanks so much for taking your time to read this

---

### Post by sandyd on 2009-10-16
> **mjp29 said:**
> I have laringitis and have been emailing my wife in the house to communicate with her blackberry.  She is trying to help me by not talking to me which makes me want to talk back (even if it's not a question).

Let's say she's sitting on couch and I'm 15 or 20 feet away.  Is there any way for me to type something and have something on Ubuntu speak it aloud.

Perhaps openoffice word then click something or a specialized program i could download?

thanks so much for taking your time to read this
[http://linuxhelp.blogspot.com/2006/01/festival-text-to-speech-synthesis.html](http://linuxhelp.blogspot.com/2006/01/festival-text-to-speech-synthesis.html)

hope you feel better!

---

### Post by kwacka on 2009-10-16
check out 'festival' - it's in the multimedia repositories

---

### Post by vambo on 2009-10-16
Try espeak. It's in the repos. You just use it from the command line, eg

```
espeak "hello world"
```

---

### Post by mjp29 on 2009-10-16
I am trying "Festival" by following directions and did the sudo command in terminal.  After a while I typed festival and typed hello in terminal and got errors.  I thought maybe it had not completely downloaded, so i waited around an hour and went back and still can't get festival to work.  Also, if I try to exit terminal it tells me a process is already going on and if I exit the process will quit.  So I still have terminal running now.

But should I quit terminal, reboot, and reinstall (to do this do i just type the sudo command again to reinstall over what is there or partially there)?

That's all I have to say and ask.  You can stop reading here and reply.  Everything below here is just a copy/paste of what is going on in terminal right *now*.

________________________________________________________________________
michael@michael-laptop:~$ sudo apt-get install festival
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 kdebase-runtime-data-common
  linux-headers-2.6.28-11 libxine1-misc-plugins libxcb-xv0 kde-icons-oxygen
  libxine1-bin libexiv2-5 librasqal1 redland-utils kdelibs5-data
  linux-headers-2.6.28-11-generic libxcb-shape0 libstreamanalyzer0 libpq5
  libstreams0 exiv2 libaudio2 libxcb-shm0 kdebase-runtime-data
  libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  festlex-cmu festlex-poslex festvox-kallpc16k libestools1.2
Suggested packages:
  festival-freebsoft-utils festival-gaim pidgin-festival
The following NEW packages will be installed:
  festival festlex-cmu festlex-poslex festvox-kallpc16k libestools1.2
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7475kB of archives.
After this operation, 20.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe libestools1.2 1:1.2.96~beta-2 [1348kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe festival 1.96~beta-7ubuntu1 [917kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe festlex-cmu 1.4.0-6 [881kB] 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe festlex-poslex 1.4.0-5 [235kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe festvox-kallpc16k 1.4.0-5 [4094kB]
Fetched 7475kB in 50s (149kB/s)                                                
Selecting previously deselected package libestools1.2.
(Reading database ... 131365 files and directories currently installed.)
Unpacking libestools1.2 (from .../libestools1.2_1%3a1.2.96~beta-2_i386.deb) ...
Selecting previously deselected package festival.
Unpacking festival (from .../festival_1.96~beta-7ubuntu1_i386.deb) ...
Selecting previously deselected package festlex-cmu.
Unpacking festlex-cmu (from .../festlex-cmu_1.4.0-6_all.deb) ...
Selecting previously deselected package festlex-poslex.
Unpacking festlex-poslex (from .../festlex-poslex_1.4.0-5_all.deb) ...
Selecting previously deselected package festvox-kallpc16k.
Unpacking festvox-kallpc16k (from .../festvox-kallpc16k_1.4.0-5_all.deb) ...
Processing triggers for man-db ...
Setting up libestools1.2 (1:1.2.96~beta-2) ...

Setting up festival (1.96~beta-7ubuntu1) ...

Setting up festlex-cmu (1.4.0-6) ...
Setting up festlex-poslex (1.4.0-5) ...
Setting up festvox-kallpc16k (1.4.0-5) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
michael@michael-laptop:~$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> hello
SIOD ERROR: unbound variable : hello
festival> hello
SIOD ERROR: unbound variable : hello
festival> hello
SIOD ERROR: unbound variable : hello
festival> hi
SIOD ERROR: unbound variable : hi
festival> 
festival> hi
SIOD ERROR: unbound variable : hi
festival>

---

### Post by mjp29 on 2009-10-16
> **vambo said:**
> Try espeak. It's in the repos. You just use it from the command line, eg

```
espeak "hello world"
```

I installed ksmile and couldn't get it to work.

I'm now trying to get festival to work and am still trying to get it to work via awaiting users replies on what i should do next [see my reply in this thread asking for more help]

if i can't get festival to work, i'll definitely seak out and install espeak.

So thank you for your reply and giving me another option if i can't get festival to work.

---

### Post by mjp29 on 2009-10-20
> **vambo said:**
> Try espeak. It's in the repos. You just use it from the command line, eg

```
espeak "hello world"
```

ok, espeak will be my third try.

I'll install espeak.

Please, someone, tell me how to uninstall "festival" - probably will have to use a terminal command as festival isn't showing up in any menu.

---

### Post by zer0x on 2009-10-20
Hi,

Festival:

```
festival> (SayText "Hello Dave")
```

Quickstart Guide:

[http://festvox.org/docs/manual-1.4.3/festival_7.html]("http://festvox.org/docs/manual-1.4.3/festival_7.html")

HTH

zer0x

---

### Post by mjp29 on 2009-10-20
I can't get any of the 3 speak programs to work.  Ksmile just wouldn't work.  Espeak would only "click."  And festival, I installed again, won't do anything.  I pasted my terminal into below, perhaps you can tell me what I'm doing wrong

michael@michael-laptop:~$ espeak "hello world"
michael@michael-laptop:~$ espeak hello world
michael@michael-laptop:~$ festival "hello world"
The program 'festival' is currently not installed.  You can install it by typing:
sudo apt-get install festival
bash: festival: command not found
michael@michael-laptop:~$ sudo apt-get install festival
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libxine1-x librdf0 kdebase-runtime-data-common
  linux-headers-2.6.28-11 libxine1-misc-plugins libxcb-xv0 kde-icons-oxygen
  libxine1-bin libexiv2-5 librasqal1 redland-utils kdelibs5-data
  linux-headers-2.6.28-11-generic libxcb-shape0 libstreamanalyzer0 libpq5
  libstreams0 exiv2 libxcb-shm0 kdebase-runtime-data libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  festlex-cmu festlex-poslex festvox-kallpc16k
Suggested packages:
  festival-freebsoft-utils festival-gaim pidgin-festival
The following NEW packages will be installed:
  festival festlex-cmu festlex-poslex festvox-kallpc16k
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/6127kB of archives.
After this operation, 16.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package festival.
(Reading database ... 131604 files and directories currently installed.)
Unpacking festival (from .../festival_1.96~beta-7ubuntu1_i386.deb) ...
Selecting previously deselected package festlex-cmu.
Unpacking festlex-cmu (from .../festlex-cmu_1.4.0-6_all.deb) ...
Selecting previously deselected package festlex-poslex.
Unpacking festlex-poslex (from .../festlex-poslex_1.4.0-5_all.deb) ...
Selecting previously deselected package festvox-kallpc16k.
Unpacking festvox-kallpc16k (from .../festvox-kallpc16k_1.4.0-5_all.deb) ...
Processing triggers for man-db ...
Setting up festival (1.96~beta-7ubuntu1) ...

Setting up festlex-cmu (1.4.0-6) ...
Setting up festlex-poslex (1.4.0-5) ...
Setting up festvox-kallpc16k (1.4.0-5) ...
michael@michael-laptop:~$ festival> (SayText "Hello Dave")
bash: syntax error near unexpected token `('
michael@michael-laptop:~$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> saytext "hello dave"
SIOD ERROR: unbound variable : saytext
festival> festival> (SayText "Hello Dave")
SIOD ERROR: unbound variable : festival>
festival> saytext hello world
SIOD ERROR: unbound variable : saytext
festival> saytext hello
SIOD ERROR: unbound variable : saytext
festival> speak hello
SIOD ERROR: unbound variable : speak

---

### Post by zer0x on 2009-10-21
Hi,

I just checked your output, looks like the first time you did not include the brackets, and the second time you also typed 'festival>' at the start of the command.

At the 'festival>' prompt you just need to type:

```
(SayText "Hello Dave")
```

It is case sensitive, so you will have to use 'SayText' not 'saytext' :D

Here is my output:

```
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (SayText "Hello Dave")
#<Utterance 0xb6ac7718>
festival> 
```

HTH

zer0x

---

### Post by mjp29 on 2009-10-23
> **zer0x said:**
> Hi,

I just checked your output, looks like the first time you did not include the brackets, and the second time you also typed 'festival>' at the start of the command.

At the 'festival>' prompt you just need to type:

```
(SayText "Hello Dave")
```

It is case sensitive, so you will have to use 'SayText' not 'saytext' :D

Here is my output:

```
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (SayText "Hello Dave")
#<Utterance 0xb6ac7718>
festival> 
```

HTH

zer0x

Thanks so much and that actually works and made the computer speak for the first time.

However, the parenthesis one must type and the _"_ then _"_ again and then type end parenthesis -> for example one must type exactly (SayText "Hello Dave")

well having to type _"_ twice and _(_ once and _)_ once makes it fairly [very] un-user friendly, don't you think?

I mean, I could not speak due to losing my voice, but typing all those _(_ & _)_ and _"_ & _"_ simply makes the command line a pain in the buttox to use over and over again when typing many things for the cpu to say over and over again

I wish I could just type SayText Hello Dave        
I could live with that and feel that is not difficult to do

---

### Post by jmszr on 2009-10-23
mjp29,

There is a GUI for espeak called gespeaker in Synaptic that works as you wish.

---

### Post by undecim on 2009-10-23
I don't recall installed epseak, but it's on all my ubuntu laptops (9.04), so I think it may be a default package. espeak is as easy as typing "espeak Hello World" in a terminal.

This simple bash line will also let you type lines non-stop and get speech output without typing any syntax or commands (just type what you want to say, press enter, type some more, press enter...)
```
while read SPEAK; do espeak $SPEAK; done
```

---

