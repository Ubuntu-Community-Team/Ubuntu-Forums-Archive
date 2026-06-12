---
title: "why does apt-get selects previously deslected packages?"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-22
I just installed Ubuntu onto a flash drive. I'm installing GIMP image editor. I noticed that every package that get installed through apt-get says "selecting previously deselected package".   Is this some sort of logging error?  I've never had any of these packages on my system before.   Why would it select a previously deslected package?

---

### Post by lkjoel on 2010-08-22
> **outleradam said:**
> I just installed Ubuntu onto a flash drive. I'm installing GIMP image editor. I noticed that every package that get installed through apt-get says "selecting previously deselected package".   Is this some sort of logging error?  I've never had any of these packages on my system before.   Why would it select a previously deslected package?
It is normal for it to do that.
I do not really know what it means, but it will install GIMP, and nothing else (unless you wanted it to install more things).

---

### Post by jonnywombat on 2010-08-22
AFIAK

Rather than deselected think of it as unselected...

It does not mean that the package has been installed, removed and is now going to be installed again, it just means the package is not currently installed.

HTH

---

### Post by uRock on 2010-08-22
The packages were previous deselected in Synaptic Package Manager, Apt is marking them for future reference for updates and so that when you open it, you will see that the packages are installed.

---

### Post by outleradam on 2010-08-22
I guess my issue is with the wording.    It dosn't seem to make any sense.  The normal state for an app is deslected.  Selected would be a modifier for that state.   It should just say selecting package gimp.  

The words Previously Deslected seem to just add to confusion.  I have run ubuntu for years and just realized that it does this every time.  I had always assumed I just removed a package and it was deselected, now it is reselecting it.   

Why would they put the words "Previously Deselected" in there when it was never selected in the first place?

---

### Post by HeadHunter00 on 2010-08-22
I am not sure, but I think that means that it is installing the dependencies for the package that is being installed.

---

### Post by lkjoel on 2010-08-22
> **outleradam said:**
> I guess my issue is with the wording.    It dosn't seem to make any sense.  The normal state for an app is deslected.  Selected would be a modifier for that state.   It should just say selecting package gimp.  

The words Previously Deslected seem to just add to confusion.  I have run ubuntu for years and just realized that it does this every time.  I had always assumed I just removed a package and it was deselected, now it is reselecting it.   

Why would they put the words "Previously Deselected" in there when it was never selected in the first place?
Maybe it meant: "Before, this package was deselected".

---

### Post by uRock on 2010-08-22
> **outleradam said:**
> I guess my issue is with the wording.    It dosn't seem to make any sense.  The normal state for an app is deslected.  Selected would be a modifier for that state.   It should just say selecting package gimp.  

The words Previously Deslected seem to just add to confusion.  I have run ubuntu for years and just realized that it does this every time.  I had always assumed I just removed a package and it was deselected, now it is reselecting it.   

Why would they put the words "Previously Deselected" in there when it was never selected in the first place?
Deselected= not installed
Previously deselected= now installed
Selecting previously deselected package means it is installing something that was not installed previously.

When you go into a grocery store, everything is deselected. Once you put stuff in your cart, they become selected or previously deselected.

---

### Post by outleradam on 2010-08-22
The problem with that is that it is not gramatically correct.  It is not previously deselected if it is selecting.   You are saying that selecting and installing are the same when they are not.  Selecting something means to make a choice.   Installing something is a physical action.  

Why would they use the words previously deselected like that?  It shows a discontinuety between the user and machine.  It was "selected" the second I personally selected it.  It needs to be installed.

Installing previously uninstalled does not make sense either.

Here are some better ways of saying it.
Selecting new package 
Installing new package
Selecting package for installation
Selecting package marked not installed
Selecting package for Dpkg
Updating package status to be installed
Selecting package to be installed
.......  You get the point,  I could do this all day.

I understand this comes from the apt installation database directly.  It could be refined before it appears on a users screen with laymen misleading information.

---

### Post by lkjoel on 2010-08-22
I totally agree with you.

---

### Post by uRock on 2010-08-22
A letter to Debian might make them rewrite how the text appears when installing, but I doubt they would care. They could make it like Windows where you have no clue what is going on during installs and updates. I find the terminology easy to understand and there are more important problems that need fixing.

---

### Post by outleradam on 2010-08-22
Where is the source for apt-get?   Google turns up thousands of package names.

---

### Post by lkjoel on 2010-08-25
The source is on /etc/apt/sources.list.
```
cat /etc/apt/sources.list
```

---

### Post by outleradam on 2010-08-25
That's an aptitude sources list.  I need the souce code for apt-get

---

### Post by llamabr on 2010-08-25
It was deselected by you, when you chose to run whatever installation program you ran when you put ubuntu on your computer.  Probably you did not go down the list and deselect things that you didn't want installed.  You let the authors of your installation disk do that for you.

Synaptic keeps a list of all of these packages for updating purposes, and so it knows which ones you didn't install.

A package like gimp, therefore, was previously deselected.  A package that you download from something like getdeb would fall into the category that you are talking about, viz., never before selected.

---

### Post by outleradam on 2010-08-25
It was never selected.  Therefore it's status must be not selected.  Deselected means to reverse the selection... check it out here on english club.  [http://www.englishclub.com/vocabulary/prefixes.htm](http://www.englishclub.com/vocabulary/prefixes.htm)

On top of that, it says it is selecting.  It is not selecting.  It is installing.  I selected the package to be installed.  It is now performing the necessary operations to complete my selection of programs to be installed.

It shows improper grammar and a discontinuity between the machine and the user.  

The words deselected leads one to believe that the package which is now being selected was already selected at one time and it was then unselected.  This is unneeded confusion which can be avoided by changing the line to read:  Selecting package XXX for installation.  Or any of the other suggestions in post #9 on the previous page

There is no reason to cause the confusion of referencing a previous deselected package for which a selection never occurred. Also, there is no reason to select it again after I just got done selecting it by saying "apt-get install gimp".  The minute I hit enter, it was selected. apt-get just needs to install it.

---

### Post by lkjoel on 2010-08-25
> **outleradam said:**
> That's an aptitude sources list.  I need the souce code for apt-get
Aptitude and Apt-Get use the same source list.

---

### Post by llamabr on 2010-08-26
> **outleradam said:**
> It was never selected.  Therefore it's status must be not selected.  Deselected means to reverse the selection... check it out here on english club.  [http://www.englishclub.com/vocabulary/prefixes.htm](http://www.englishclub.com/vocabulary/prefixes.htm)

On top of that, it says it is selecting.  It is not selecting.  It is installing.  I selected the package to be installed.  It is now performing the necessary operations to complete my selection of programs to be installed.

It shows improper grammar and a discontinuity between the machine and the user.  

The words deselected leads one to believe that the package which is now being selected was already selected at one time and it was then unselected.  This is unneeded confusion which can be avoided by changing the line to read:  Selecting package XXX for installation.  Or any of the other suggestions in post #9 on the previous page

There is no reason to cause the confusion of referencing a previous deselected package for which a selection never occurred. Also, there is no reason to select it again after I just got done selecting it by saying "apt-get install gimp".  The minute I hit enter, it was selected. apt-get just needs to install it.

You are correct.  Ubuntu is designed and maintained by people who do not speak English correctly.  What we need is you, and your expertise.  Semantic subtleties confuse and frighten us, and we therefore need your guidance.  You may begin here:

[https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu)

Feel free to contribute as your own expertise allows.

NB, note that "it's" is not the same word as "its".

---

### Post by outleradam on 2010-08-26
^^ Thank you.  I'm sorry for my "it's" problem.  I will follow the directions in that wiki entry.      Unfortunately I believe the problem may be in Debian.  I don't really know about how to speak to them.  I tried to file a standard bug report and it told me that I did not specify a package.  I specified "apt-get" in the bug report e-mail but apparently that is not picked up by their bot-filter.

I'm not trying to step on anyones toes.  My thinking is the best way to take care of problems is to take care of the big and noticeable stuff, then let the little stuff fall in place.  I figure this is easy enough for me as a first contribution to this project which I've been using for 7 years.



> **lkjoel said:**
> Aptitude and Apt-Get use the same source list.
That's a sources list.  That sources list tells the computer where to get .deb files.  I need source code.  Source code is the actual program in C, Java, or whatever the case may be.

---

### Post by lkjoel on 2010-08-27
> **outleradam said:**
> ^^ Thank you.  I'm sorry for my "it's" problem.  I will follow the directions in that wiki entry.      Unfortunately I believe the problem may be in Debian.  I don't really know about how to speak to them.  I tried to file a standard bug report and it told me that I did not specify a package.  I specified "apt-get" in the bug report e-mail but apparently that is not picked up by their bot-filter.

I'm not trying to step on anyones toes.  My thinking is the best way to take care of problems is to take care of the big and noticeable stuff, then let the little stuff fall in place.  I figure this is easy enough for me as a first contribution to this project which I've been using for 7 years.




That's a sources list.  That sources list tells the computer where to get .deb files.  I need source code.  Source code is the actual program in C, Java, or whatever the case may be.

It also tells where to find the source code.
To get the source code, type this in:

```
sudo apt-build source *yourpackage*
```
To get AND build the source code, type this in:
```
sudo apt-build build-source *yourpackage*
```
To get AND build AND install the source code, type this in:
```
sudo apt-build install *yourpackage*
```

To get all the details, type:
```
sudo apt-build --help
```

---

### Post by outleradam on 2010-08-28
Ok, so what is the package name for apt-get?   That's where the problem has been from the get-go.  I contacted Debian and reported a bug, but their bot said the package name was invalid.   I searched for it and cannot find the source or the package name for apt-get because of all the clutter involved with the word apt-get.   

How can I find the source?

---

### Post by lkjoel on 2010-08-28
> **outleradam said:**
> Ok, so what is the package name for apt-get?   That's where the problem has been from the get-go.  I contacted Debian and reported a bug, but their bot said the package name was invalid.   I searched for it and cannot find the source or the package name for apt-get because of all the clutter involved with the word apt-get.   

How can I find the source?
Do you mean the source code?

---

### Post by outleradam on 2010-08-28
yes. That is what I've been asking for 2 pages now.   Do you have an answer or are you just asking arbitrary questions?

---

### Post by TCKevin on 2010-08-28
You wish to know what the apt-get source is well from what I believe (what I read) in 
[http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1](http://www.debian-administration.org/article/An_introduction_to_bash_completion_part_1) 
the apt-get is a bash shell command that should be in your /etc/bash_completed.d/ directory as a file called apt.
The above reference says "When the bash_completion file is sourced (or loaded) everything inside the /etc/bash_completion.d directory is also loaded.  This makes it a simple matter to add your own hooks."

I DO NOT ADVISE YOU TO ALTER THIS FILE!

---

### Post by jtarin on 2010-08-28
> **outleradam said:**
>  Do you have an answer or are you just asking arbitrary questions?Yes!

---

### Post by lkjoel on 2010-08-28
> **outleradam said:**
> yes. That is what I've been asking for 2 pages now.   Do you have an answer or are you just asking arbitrary questions?
[http://ubuntuforums.org/showpost.php?p=9773517&postcount=20](http://ubuntuforums.org/showpost.php?p=9773517&postcount=20)

---

### Post by outleradam on 2010-08-29
[http://git.debian.org/?p=aptitude/aptitude.git;a=tree;h=refs/heads/debian;hb=debian](http://git.debian.org/?p=aptitude/aptitude.git;a=tree;h=refs/heads/debian;hb=debian)

---

### Post by outleradam on 2010-08-29
[https://launchpad.net/apt](https://launchpad.net/apt)

---

### Post by lkjoel on 2010-08-31
> **outleradam said:**
> [https://launchpad.net/apt](https://launchpad.net/apt)
Could you say who you are directing this link to?

---

### Post by jtarin on 2010-08-31
Must be me as I don't have it in my bookmarks yet! :)

---

### Post by outleradam on 2010-08-31
> **lkjoel said:**
> Could you say who you are directing this link to?
It's the link I was looking for with the apt source.

---

