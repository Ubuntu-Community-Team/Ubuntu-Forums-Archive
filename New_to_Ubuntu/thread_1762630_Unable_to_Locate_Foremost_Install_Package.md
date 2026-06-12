---
title: "Unable to Locate Foremost Install Package"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by deepeshkris on 2011-05-19
Hello,

I lost all my data on my laptop i am trying to recover that with Photorec and Foremost etc

But the trouble is when i open and do these steps,
Foremost is a command-line utility that allows to simply recover deleted files.



**Foremost Installation **


There are two methods to set up Foremost:


1. Open the terminal (Applications >> Accessories >> Terminal), then run this command:


 **sudo apt-get install foremost**

I get a message saying "Unable to Locate Package Foremost"

I tried the same with Photorec.

Please help me with simple steps. The installation has overwritten the previous version of Ubuntu.

I can boot using Pen Drive but when tried to boot using [LEFT]BootMed it wouldnt boot.

Thanks for all your help
[/LEFT]

---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]Hello there,
you just spelled the name of the package wrong or it's called different.

Why don't you just search for it using the ubuntu software center?


I don't know those programs, but if they are not opensource you've got to add their ppa to your repositories.
To do so open up the software center and go onto preferennces. --> third person software or other software--> add the repository
[/FONT]

---

### Post by Lateralis on 2011-05-19
> **3xp10r3r|X13 said:**
> [FONT=Courier New]Hello there,
you just spelled the name of the package wrong or it's called different.

Why don't you just search for it using the ubuntu software center?


I don't know those programs, but if they are not opensource you've got to add their ppa to your repositories.
To do so open up the software center and go onto preferennces. --> third person software or other software--> add the repository
[/FONT]

Foremost is in the Lucid repository:

```

$ sudo aptitude search foremost
p   foremost           - Forensics application to recover data 

```
          
I can't find photorec though.  

The package is also in [Maverick, Natty and previous versions]("http://packages.ubuntu.com/search?keywords=foremost&searchon=names&suite=all&section=all").

---

### Post by deepeshkris on 2011-05-19
> **3xp10r3r|X13 said:**
> [FONT=Courier New]Hello there,
you just spelled the name of the package wrong or it's called different.

Why don't you just search for it using the ubuntu software center?


I don't know those programs, but if they are not opensource you've got to add their ppa to your repositories.
To do so open up the software center and go onto preferennces. --> third person software or other software--> add the repository
[/FONT]


Thanks for your reply, what options do i have for data recovery?

I found some good options in Foremost and Photorec, but I am unable to install them!

How do i add PPA [FONT=Courier New]to your repositories, i could not locate preferences and thirdperson software option in it.

I am using version 10.10
[/FONT]

---

### Post by deepeshkris on 2011-05-19
> **Lateralis said:**
> Foremost is in the Lucid repository:

```

$ sudo aptitude search foremost
p   foremost           - Forensics application to recover data 

```I can't find photorec though.  

Which version of Ubuntu are you using?

Thanks for your reply, i lost my data and i am trying to recover all of that.

I tried this,

[http://manpages.ubuntu.com/manpages/maverick/man1/photorec.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/photorec.1.html) 

and  this

Foremost is a command-line utility that allows to simply recover deleted files.



**Foremost Installation **


There are two methods to set up Foremost:


1. Open the terminal (Applications >> Accessories >> Terminal), then run this command:


 [B]sudo apt-get install foremost
[/B]

They both are not working i am getting a message:  "Unable to Locate Package Foremost"

Please see if you can help me install some of this software and recover data.

I am using ubuntu 10.10

---

