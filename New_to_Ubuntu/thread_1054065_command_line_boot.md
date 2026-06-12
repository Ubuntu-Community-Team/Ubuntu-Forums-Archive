---
title: "command line boot"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by luis956 on 2009-01-29
Hey guys im new here and I have a problem. I just installed studio ubuntu but when I turn on my computer it goes to a command line log in. I type my user name and password then it shows luis@ubuntu:~$      what do i do now? I tried to use the search bar but that didnt help.

---

### Post by mrbiggbrain on 2009-01-29
at the shell prompt

```
startx 
```

that command will start the xserver, and bring up your default window manager.

---

### Post by luis956 on 2009-01-29
It tells me that it is not installed

---

### Post by luis956 on 2009-01-29
Tried to install it with the command then its says that the package is missing, has been obsoleted, or is only available from another source. However the following packages replace it:
x11-common?

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> It tells me that it is not installed

ok then you do not have xserver installed. did you get the server version of ubuntu? it ships with no window managers

have you tryed

```
sudo apt-get x11-common
```

or maybe ubuntu-desktop will install it as a dependency

```
sudo apt-get ubuntu-desktop
```

---

### Post by abhilashm86 on 2009-01-29
i couldn't understand your problem,but is default command line when logged on?
do the following,

ctlt+ alt + F7

this will get back your system from commandline,do and reply,in my system it had happened,i did same way:)

---

### Post by luis956 on 2009-01-29
Tells me invalid operation x11-common

---

### Post by abhilashm86 on 2009-01-29
don't type anything login name or password,just type control alt and f7 key,it will directly take you to GUI desktop,right?

---

### Post by luis956 on 2009-01-29
Nothing happens when i press those keys at the same time

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> Tells me invalid operation x11-common

what are the exact commands you are running?

---

### Post by luis956 on 2009-01-29
mrbiggbrain it tells me that its an invalid operation ubuntu-desktop

---

### Post by luis956 on 2009-01-29
Exactly what u told me to type

---

### Post by abhilashm86 on 2009-01-29
is the whole background commandline??what happens after u enter login name and password?

try this- press ctrl+alt+f1
this takes to u to command option line,from there press 
ctrl+alt+f7

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> Exactly what u told me to type


oops,

try

 ```
sudo apt-get install ubuntu-desktop
```


forgot install ... im verry sorry

---

### Post by luis956 on 2009-01-29
abhilashm86 nothing happens when I try those keys, and the whole background is command line.

---

### Post by luis956 on 2009-01-29
Damn it says that it couldnt find the package :( Damn am I screwed

---

### Post by abhilashm86 on 2009-01-29
> **luis956 said:**
> abhilashm86 nothing happens when I try those keys, and the whole background is command line.

oh now i get your point,
hey anyways when you get GUI desktop,you can well use either commandline or GUI,by changing those keys.

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> Damn it says that it couldnt find the package :( Damn am I screwed

can you try

```
ping www.google.com
```

does it time out, or does it give you numbers in milseconds

this will tell us if your online.

---

### Post by luis956 on 2009-01-29
I am offline i know that much hehe, I downloaded the cd, and i even checked it for errors but it was clean.I did this at home i am at school right now

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> I am offline i know that much hehe, I downloaded the cd, and i even checked it for errors but it was clean.I did this at home i am at school right now

thats why you cant get the files, you dont have access to the repos.  you would have to be online to sue the apt-get command... well or set a cd/dvd with the files on it as a repo, but youd have to have all the files you needed, a whole lot of them.

---

### Post by luis956 on 2009-01-29
Ok so when I get home I just plug in my ethernet cord and try all the steps you gave me before to see which one works?

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> Ok so when I get home I just plug in my ethernet cord and try all the steps you gave me before to see which one works?

haha only the right steps, the first few was me haveing a brain freaze and forgetting part of the command.

but yes try

```
sudo apt-get install ubuntu-desktop
```

if it dosnt have x in it

```
sudo apt-get install x11-common

```

---

### Post by luis956 on 2009-01-29
Ok do I have to configure anything if all i do is plug in my ethernet cord?

---

### Post by mrbiggbrain on 2009-01-29
> **luis956 said:**
> Ok do I have to configure anything if all i do is plug in my ethernet cord?

everything SHOULD configure correctly as long as you have everything else setup correctly. if another os can do it linux should.

---

### Post by luis956 on 2009-01-29
Ok, hey thanks allot for your help much appreciated. I will give it a try in like 3 hours because I have flash class in a bit.

---

### Post by ashwin.kj on 2009-01-29
You could also try /etc/init.d/gdm start 
i.e if ur are using gnome.

---

### Post by TomErwin on 2009-01-29
Hey Luis, I wish your Flash class went good. I had same problem today..
"mrbiggbrain" : thank you so much for the solution (installing the desktop) it has worked with me and I am writing these lines now from my Ubuntu desktop... the download was much bigger than what I thought. but it is wonderful that it worked. thank you again you made my day :)

---

### Post by mrbiggbrain on 2009-01-29
> **TomErwin said:**
> Hey Luis, I wish your Flash class went good. I had same problem today..
"mrbiggbrain" : thank you so much for the solution (installing the desktop) it has worked with me and I am writing these lines now from my Ubuntu desktop... the download was much bigger than what I thought. but it is wonderful that it worked. thank you again you made my day :)

Not a problem, i hope it works for luis too, i dont claim to know alot about linux, i was quite excited i might know the answer haha :-)

---

### Post by TomErwin on 2009-01-30
I am sorry if I ask this question here, I have a problem with my Camera. How can I start a post? I am sorry it is the first time for me to be in a forum :)

---

### Post by ratmandall on 2009-01-30
Start a new thread in beginner talk.
[http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)

---

### Post by TomErwin on 2009-01-30
> **ratmandall said:**
> Start a new thread in beginner talk.
[http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)

Thank you very much. I just did it :)

---

