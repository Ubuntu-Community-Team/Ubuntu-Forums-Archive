---
title: "command line"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by mekanik7777 on 2010-01-30
holy crap nuggets. why is it that even in the beginners threads i feel like a pre-beginner. the hardest thing for me is understanding basic basic command line line stuff like what a space does and why is it called an arguement and i cant even install java like how the website explains "step by step". i dont know what /, " ", ~ and how they are relative to getting java to install. i tried reading the pocket guide but that is still to complicated.

is there a better version of terminal that has some kind of gui so i dont have to type my life away


HELP! HELP!, i am so new im beggining to hate linux.

---

### Post by tubasoldier on 2010-01-30
why are you trying to install java in the command line? it should be available for install in add/remove programs. or in synaptic, which should be under administration.

and for a specific step by step here are a few options:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
[http://www.javalobby.org/java/forums/t72809.html](http://www.javalobby.org/java/forums/t72809.html)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by steveneddy on 2010-01-30
> **mekanik7777 said:**
> holy crap nuggets. why is it that even in the beginners threads i feel like a pre-beginner. the hardest thing for me is understanding basic basic command line line stuff like what a space does and why is it called an arguement and i cant even install java like how the website explains "step by step". i dont know what /, " ", ~ and how they are relative to getting java to install. i tried reading the pocket guide but that is still to complicated.

is there a better version of terminal that has some kind of gui so i dont have to type my life away


HELP! HELP!, i am so new im beggining to hate linux.

Don't type it - copy and paste - <snip>

In Linux there is a short cut to copy and paste...

Simply **highlight** whatever you want to copy, then go to the terminal and push your middle mouse button, or if on a laptop, hit the pad with two fingers - this will past whatever you just highlighted into the terminal.

Welcome to Linux - the command line, or terminal, will become your friend. don't be scared of it.

Please explain what you are trying to accomplish, because most of the stuff you want/need to install are merely small clicks away.

The GUI way of installing is Synaptic Package Manager.

System --> Administration --> Synaptic Package Manager

search for the application you need and install it from there.

---

### Post by mekanik7777 on 2010-01-30
i was trying to get my neihgbor to use ubuntu on his computer, got it installed and he goes to a website pogo.com to play games, when he tries to play the game it asks if i want to installl java, i say yes, it takes me to download page then saves a .bin file, i try to open the file and i get a messgae saying i need to pick a program to open it. on the java website it has a walk thru of what to do to install it and its not helping

---

### Post by tubasoldier on 2010-01-30
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

There. that will help you get java installed more directly than the java website.

---

### Post by Primefalcon on 2010-01-30
really just go to applciations -> ubuntu software center

a new window will open

in the search bar in the top right type java

and install both sun java 6.0 plugin, this will allow your browser to run java aps in your browser, for general use you should also install sun java 6 runtime

that's it **no command line codes needed**

---

### Post by Diametric on 2010-01-30
> **mekanik7777 said:**
> i was trying to get my neihgbor to use ubuntu on his computer, got it installed and he goes to a website pogo.com to play games, when he tries to play the game it asks if i want to installl java, i say yes, it takes me to download page then saves a .bin file, i try to open the file and i get a messgae saying i need to pick a program to open it. on the java website it has a walk thru of what to do to install it and its not helping

First, go here:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and read on how to get all things multimedia that you need.  It's super easy and can be completed in about 10 minutes.  This will get the machine to play most if not all multimedia apps you need.....flash, java etc.

Next, if you're serious about Linux, read up on the command line.  I've just started myself and I recommend "Learning the bash shell' by Cameron Newham and Bill Rosenblatt - published by O'Reilly.  By the way...the command line is the shell, terminal...all the same thing.  At first it can be a bit intimidating, but for real...once you "get" what it does and why Linux is so command line dependent (as opposed to Windows and all things GUI)..it will make SO much more sense and is SO much more powerful.

Welcome...hang in there and use this forum.  There are some straight OG Linux hustlers on this forum and most are ready to help as soon as you post a question.  

Enjoy!

---

### Post by mekanik7777 on 2010-01-30
i did find it in the software center, not sure why i could not get working on his, got it on mine, ill check tomorrow, thanks

---

### Post by Primefalcon on 2010-01-30
Command line is powerful and I use it myself a lot.... but I just want to stress that a lot of people don't use it, with Ubuntu there is a GUI for nearly everything there is to do.....

for a new user it'd be easier to show them the GUI way to do things so they can learn how to do this quicker, they learn the CLI if and when they're ready, but the CLI is not necessary to using Ubuntu

And your welcome

---

### Post by mekanik7777 on 2010-01-30
> **Diametric said:**
> First, go here:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) and read on how to get all things multimedia that you need.  It's super easy and can be completed in about 10 minutes.  This will get the machine to play most if not all multimedia apps you need.....flash, java etc.

Next, if you're serious about Linux, read up on the command line.  I've just started myself and I recommend "Learning the bash shell' by Cameron Newham and Bill Rosenblatt - published by O'Reilly.  By the way...the command line is the shell, terminal...all the same thing.  At first it can be a bit intimidating, but for real...once you "get" what it does and why Linux is so command line dependent (as opposed to Windows and all things GUI)..it will make SO much more sense and is SO much more powerful.

Welcome...hang in there and use this forum.  There are some straight OG Linux hustlers on this forum and most are ready to help as soon as you post a question.  

Enjoy!

when i try the first step in the link to get the repository the terminal wont let me enter my pass word, the cursor flashes but my password wont display when i hit the keys

glenn@glenn-desktop:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for glenn:

---

### Post by Primefalcon on 2010-01-30
> **mekanik7777 said:**
> when i try the first step in the link to get the repository the terminal wont let me enter my pass word, the cursor flashes but my password wont display when i hit the keys

glenn@glenn-desktop:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for glenn:
just type your password and hit enter, your password wont show, it's a security thing system is still reading it though

---

### Post by mekanik7777 on 2010-01-30
worked great, thanks

---

### Post by Primefalcon on 2010-01-30
> **mekanik7777 said:**
> worked great, thanks
YW feel free to come back anytime ;-)

---

### Post by ubername on 2010-01-30
> **steveneddy said:**
> Don't type it - copy and paste - <snip>

In Linux there is a short cut to copy and paste...

Simply **highlight** whatever you want to copy, then go to the terminal and push your middle mouse button, or if on a laptop, hit the pad with two fingers - this will past whatever you just highlighted into the terminal.

....snip...

Many thanks steveneddy - Ive been using ctl-c (shift)-ctl-v for years! I wish I had known this earlier!

---

### Post by Diametric on 2010-01-30
> **mekanik7777 said:**
> when i try the first step in the link to get the repository the terminal wont let me enter my pass word, the cursor flashes but my password wont display when i hit the keys

glenn@glenn-desktop:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for glenn:

Good question!   When in the terminal (or shell...same thing) and you type your password, it does not display the characters...or anything at all.  So if your password is "1234"...just type in 1234 and press enter (return) and if it is the correct key pattern then it will continue to run.  Let me know how it goes.

Ooops.  Didn't see the other posts.

---

