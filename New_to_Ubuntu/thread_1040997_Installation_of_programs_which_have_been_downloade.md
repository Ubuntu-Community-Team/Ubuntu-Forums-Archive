---
title: "Installation of programs which have been downloaded"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Ambushed on 2009-01-16
Hey guys & gals, I am new to Ubuntu.

I'm just wondering how to install a program once I downloaded it.

I go into terminal & go to the DIR of the location of the program then what do I type to install the program.

Trying running through some of the tutorials but they didn't seem to help.

Running 8.10.

---

### Post by nothingspecial on 2009-01-16
What are you trying to install?

---

### Post by SunnyRabbiera on 2009-01-16
Indeed, as you dont do the windows way of installing things here...
Give us the name of the app

---

### Post by bailbath on 2009-01-16
It depends on what you have downloaded!
Have you checked your package manager for the program first?
go to System-admin-synaptic it will ask for your password. Then use the search for finding the program that you want. If it is there highlight it and mark it for install, it will download and install it for you then you will find it in your menu ready for launching.
If it is a program that is not available from synaptic I go back to my first sentence!
Ian

---

### Post by redseventyseven on 2009-01-16
Hello,

Welcome aboard! Hope you find Ubuntu useful!

As you may have guessed, there are differences in the way that Ubuntu and Windows work. Whereas in Windows you go and download setup.exe from some random website for just about every program, in Ubuntu the usual way of downloading a program is to fetch it from a repository - a pre-made library of software packages which have been scrutinised for use with Ubuntu.

It would help if you could let us know what program you're trying to install, then we can tell you if it's in the repositories (in which case installation is a piece of cake) or if it's a Windows-only program then someone might know of a Linux equivalent which does the same job.

---

### Post by zvacet on 2009-01-16
If you downloaded something like **package.deb** then just double click on it.But other posters arre right,there is difference between Windows and linux in way how to install downloaded files.And yes,what are you trying to install?Package name,file exension,link...

---

### Post by Michael.Godawski on 2009-01-16
hi and welcome,

have a look at 

[LIST]
[*][http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)
[/LIST]

It really depends what type of file you have downloaded.

---

### Post by Ambushed on 2009-01-16
Ohok, thanks for the reply guys.

I am trying to install aircrack-ng-1.0-rcl.tar.gz

Can you please give me a step-by-step guide as to how to install.


Cheers.:guitar:

---

### Post by Ambushed on 2009-01-16
> **Michael.Godawski said:**
> hi and welcome,

have a look at 

[LIST]
[*][http://godawski.oxyhost.com/howtoinstall.html](http://godawski.oxyhost.com/howtoinstall.html)
[/LIST]

It really depends what type of file you have downloaded.

So I'm up to the part where it says to type in ./configure once you cd'd into the DIR of the files which I have done.

The problem is once I type ./configure into the terminal once in the dir it says bash: ./configure: No such file or directory

How can I fix this? Was I surpose to do ./configure *file name* or something?

---

### Post by stchman on 2009-01-16
> **Ambushed said:**
> Ohok, thanks for the reply guys.

I am trying to install aircrack-ng-1.0-rcl.tar.gz

Can you please give me a step-by-step guide as to how to install.


Cheers.:guitar:

The package aircrack is in the Ubuntu repositories.

To install use apt.

```
sudo apt-get install aircrack-ng
```

Easy.

Pretty much anything you need is in the repos.

---

### Post by Ambushed on 2009-01-16
> **stchman said:**
> The package aircrack is in the Ubuntu repositories.

To install use apt.

```
sudo apt-get install aircrack-ng
```

Easy.

Pretty much anything you need is in the repos.

Once in the DIR of amb@amb-laptop:~/Desktop$ I type in sudo apt-get install aircrack (for the file which is called aircrack.tar.gz) & it says 

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package aircrack


Note that I have to files on my Desktop aircrack.tar.gz & aircrackn - (Which I have extracted & renamed)

---

### Post by 73ckn797 on 2009-01-16
The easiest method for a beginner will be to go to System/Administration/Synaptic Package Manager. From there scroll down and you will find the "aircrack" program. Right click and designate "Mark for Installation". Then click on "apply" and everything will be installed for you.

---

### Post by atngplusultra on 2009-01-16
the ways to enable repositories are multiple.
the best would probably to open Synaptic.
System -> Adminstration -> Synaptic Package Manager
On the top menu, select Settings -> Repositories
and carefully enable some other repos (not sure which you'll need)
and then, once you've got all those repos installed, you should be able to use Synaptic to install aircrack.

edit: see post above, too.

---

### Post by Ambushed on 2009-01-16
When I go to System/Administration/Synaptic Package Manager & I scroll down I don't see aircrack under All

Is there anything in terminal I have to type to enable aircrack to show in Synaptic Package Manager

---

### Post by 73ckn797 on 2009-01-16
> **atngplusultra said:**
> the ways to enable repositories are multiple.
the best would probably to open Synaptic.
System -> Adminstration -> Synaptic Package Manager
On the top menu, select Settings -> Repositories
and carefully enable some other repos (not sure which you'll need)
and then, once you've got all those repos installed, you should be able to use Synaptic to install aircrack.

edit: see post above, too.

There are posts dealing with adding repos. 

Look here also: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by stchman on 2009-01-16
> **Ambushed said:**
> Once in the DIR of amb@amb-laptop:~/Desktop$ I type in sudo apt-get install aircrack (for the file which is called aircrack.tar.gz) & it says 

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package aircrack


Note that I have to files on my Desktop aircrack.tar.gz & aircrackn - (Which I have extracted & renamed)

You do not need that .tar.gz file you downloaded the repositories have the .deb package.

Also make sure all your repositories are enabled (Universe, Multiverse, Main, and Restricted) in System--->Administration--->Software Sources

You forgot the -ng.  The name of the package is aircrack-ng NOT aircrack.

Type in:
```

sudo apt-get update

```
Then:
```

sudo apt-get install aircrack-ng

```

---

### Post by Ambushed on 2009-01-16
Type in:
```

sudo apt-get update

```
Then:
```

sudo apt-get install aircrack-ng

```[/QUOTE]

Done and done, now what? Sorry for the continuous same questions almost got it!

---

### Post by Ambushed on 2009-01-16
I can now see aircrack-ng in the Repositories & it looks as if it is installed.


Now how to do I run it.:P

---

### Post by Ambushed on 2009-01-16
Having a look in Add/Remove Programs, is the aircrack application supposed to be located somewhere in there?

---

### Post by Ambushed on 2009-01-16
Beeeeeeeeeummmp:(

---

### Post by 73ckn797 on 2009-01-16
> **Ambushed said:**
> Having a look in Add/Remove Programs, is the aircrack application supposed to be located somewhere in there?


I did not find it in Add/Remove but in Synaptic Package Manager.

If it is installed you need to look through Applications. If it is not listed there then you may need to look under System/Preferences/Main Menu, and see whether it is enabled to be listed under the appropriate sub-menu.

You may need to logout and back in.

---

### Post by Sef on 2009-01-16
Please wait at least 24 hours with no responses before bumping your thread.  Thank you.

---

### Post by Ambushed on 2009-01-16
> **73ckn797 said:**
> I did not find it in Add/Remove but in Synaptic Package Manager.

If it is installed you need to look through Applications. If it is not listed there then you may need to look under System/Preferences/Main Menu, and see whether it is enabled to be listed under the appropriate sub-menu.

You may need to logout and back in.

Still unable to locate, should be called aircrack am I right?

> **Sef said:**
> Please wait at least 24 hours with no responses before bumping your thread.  Thank you.

Sorry about that.

---

### Post by handydan918 on 2009-01-16
> **Ambushed said:**
> I can now see aircrack-ng in the Repositories & it looks as if it is installed.


Now how to do I run it.:P

Usually, you can just type the name of the app in a terminal and it will launch. 

If you need to find the actual executable, do```
which aircrack-ng
```

---

### Post by Ambushed on 2009-01-16
> **handydan918 said:**
> Usually, you can just type the name of the app in a terminal and it will launch. 

If you need to find the actual executable, do```
which aircrack-ng
```

I see, cheers for that.
[I][B]
I'll be back[/B][/I]:guitar:

---

### Post by stchman on 2009-01-17
> **Ambushed said:**
> I can now see aircrack-ng in the Repositories & it looks as if it is installed.


Now how to do I run it.:P

I do not know aircrack usage just how to install it.

---

### Post by Ambushed on 2009-01-17
> **stchman said:**
> I do not know aircrack usage just how to install it.

Oh ok, thats fine.

I have got another question

- Say that I download a tar.gz file from the net, would you be able to gives me the steps (or redirect me) of how to install & run the program.

---

### Post by handydan918 on 2009-01-17
No one can tell you that, because there is not one particular way. 

tar is from TapeARchive, and gz is gzip. It's just a compressed archive. It could contain anything. Just uncompress it
```
tar -zxvf stupid_filename_here
```
 and look for a readme file.

---

### Post by Ambushed on 2009-01-19
> **handydan918 said:**
> No one can tell you that, because there is not one particular way. 

tar is from TapeARchive, and gz is gzip. It's just a compressed archive. It could contain anything. Just uncompress it
```
tar -zxvf stupid_filename_here
```
 and look for a readme file.

Ok, so can you tell me what the -zxvf is, is it related to the permissions?

So once I extract a file, how can I run it from a terminal.

---

