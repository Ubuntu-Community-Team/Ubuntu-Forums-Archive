---
title: "Can't install...anything?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by RevStHuck on 2010-02-14
Okay, complete and total noob here.  I've been trying to figure this out to the best of my ability but I'm simple I suppose 'cause it just ain't happening.

I'm trying to install a new version of Firefox and/or Opera on Ubuntu and it isn't working.  I download Opera and click "Open with GDebi package installer" and get an error message: "Dependency is not satisfiable: libqt3-mt"  

So what am I doing wrong and what do I need to do to fix it?  And please, explain in simple terms I'm afraid I really am terribly new to this OS.  We all got to start sometime, right?  Thank you.

---

### Post by Satoru-san on 2010-02-14
This tends to happen when you try to install something that is not in the repository. 

Here is how to fix that. Look at the name of the missing dependancy, and either search for it in synaptic, or even easier, open up a terminal it is in your applications menu. and type this

```
sudo apt-get install libqt3-mt
```
It will prompt you to enter your user password, and will install the program, then try to install opera agian.

---

### Post by phillw on 2010-02-14
> **RevStHuck said:**
> Okay, complete and total noob here.  I've been trying to figure this out to the best of my ability but I'm simple I suppose 'cause it just ain't happening.

I'm trying to install a new version of Firefox and/or Opera on Ubuntu and it isn't working.  I download Opera and click "Open with GDebi package installer" and get an error message: "Dependency is not satisfiable: libqt3-mt"  

So what am I doing wrong and what do I need to do to fix it?  And please, explain in simple terms I'm afraid I really am terribly new to this OS.  We all got to start sometime, right?  Thank you.


Hi and welcome,

Indeed we do !!  When you say 'new' version of FireFox, how new ? There is Namoroka (the code name for FireFox 3.6) I'm not 100% sure if it is a final release yet. 

If you want the most upto date information on Ubuntu & FireFox, then I strongly recommend popping over to LovingLinux's thread at [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

He keeps it fully upto date with what is going on in the world of Ubuntu and FireFox.

\edit -- yikes, there's a 3.7 out !!! (I'm still on 3.6 pre)

Regards,

Phill.

---

### Post by Satoru-san on 2010-02-14
> **phillw said:**
> \edit -- yikes, there's a 3.7 out !!! (I'm still on 3.6 pre)

D: I am way behind the Times, I am trying to keep my system stable, Besides 3.6 is masked by ~x86

```
Mozilla/5.0 (X11; U; Linux i686; ja-JP; rv:1.9.1.6) Gecko/20100214 Gentoo **Firefox/3.5.6**
```

---

### Post by RevStHuck on 2010-02-14
Okay...tried the terminal and I got this: 

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt3-mt

...now what?

---

### Post by nick_goodfate on 2010-02-14
> **RevStHuck said:**
> Okay, complete and total noob here.  I've been trying to figure this out to the best of my ability but I'm simple I suppose 'cause it just ain't happening.

I'm trying to install a new version of Firefox and/or Opera on Ubuntu and it isn't working.  I download Opera and click "Open with GDebi package installer" and get an error message: "Dependency is not satisfiable: libqt3-mt"  

So what am I doing wrong and what do I need to do to fix it?  And please, explain in simple terms I'm afraid I really am terribly new to this OS.  We all got to start sometime, right?  Thank you.

the best way to install somthing in ubuntu is synaptic manager , in your sustem menu . forget the: download a file and doble click it , from windows . exept its necessary . if you want to install something and cant find it in synaptic , google "how to install .... " and you ll surely find instractions .

---

### Post by RevStHuck on 2010-02-14
In regard to Firefox, its 3.6 and I download it and I really just don't know what to do with that one.  It's sitting there and I just don't know how to install that one.

---

### Post by nick_goodfate on 2010-02-14
> **RevStHuck said:**
> Okay...tried the terminal and I got this: 

 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt3-mt

...now what?

first you have to add repositories . repositories are the places it look for the programs/packages you try to download . check here how to do this : [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Repositories_using_Synaptic_Package_Manager](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Repositories_using_Synaptic_Package_Manager)
this is a guide for ubuntu 9.10 . if you have an other distribution , search in google " how to add repositories your_distribution" . when you do this try again to find libqt3-mt in terminal .

---

### Post by phillw on 2010-02-14
> **RevStHuck said:**
> In regard to Firefox, its 3.6 and I download it and I really just don't know what to do with that one.  It's sitting there and I just don't know how to install that one.


For FireFox 3.6 ...
> For** ubuntu karmic/Lucid users**
 Open the command prompt and run the following commands
 [INDENT]sudo add-apt-repository ppa:mozillateam/firefox-stable
 sudo apt-get update
 sudo apt-get install firefox-3.6
[/INDENT]

Should go get it for you.

I'm sure it's in the repositry .. but maybe only in the Lucid area. Anyways, that will get it for 9.10

Regards,

Phill.

---

### Post by lovinglinux on 2010-02-14
> **phillw said:**
> Hi and welcome,

Indeed we do !!  When you say 'new' version of FireFox, how new ? There is Namoroka (the code name for FireFox 3.6) I'm not 100% sure if it is a final release yet. 

If you want the most upto date information on Ubuntu & FireFox, then I strongly recommend popping over to LovingLinux's thread at [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

He keeps it fully upto date with what is going on in the world of Ubuntu and FireFox.

\edit -- yikes, there's a 3.7 out !!! (I'm still on 3.6 pre)

Regards,

Phill.

Thanks for your comment regarding my tutorial.

Firefox 3.6 is already final version, but depending on how you install it (see [installation methods](http://lovinglinux.megabyet.net/?page_id=220#Installation-Methods-2) and [method comparison](http://lovinglinux.megabyet.net/?page_id=220#Method-Comparison-2)) it could be some version after 3.6. Last time I checked, the 3.6pre was in fact 3.6.1 and not some version before 3.6 as the name might suggest.

If you are running 32bit Ubuntu, then I recommend using the Ubuntuzilla method. If you are running 64bit, then I recommend the *mozillateam/firefox-stable* ppa.

Firefox 3.7 has been available from some time now. The current version is 3.7alpha1. I don't recommend if you are a extension junkie like me. I have [50 installed](http://lovinglinux.megabyet.net/?p=36) :) Most extensions won't be compatible with version 3.7 at this stage. Although you can [override compatibility](http://lovinglinux.megabyet.net/?page_id=220#Extension-Compatibility-2), you can expect that some extensions will not work at all or will exhibit strange behaviors.

BTW, Lucid already has Firefox 3.6 final, so there is no need to add a ppa.

---

### Post by tekkidd on 2010-02-14
if it gives you an dependency not satisfiable error go to synaptic (ALT F2 Synaptic) and type in the dependency and install it. Note if you have a really old version of ubuntu the dependency might not be in the repos

---

### Post by mathfreak123 on 2010-02-14
Hi! Linux installs things a bit differently than Windows does. Several distributions of Linux use a package manager program to install programs for you.

Ubuntu uses Synaptic Package Manager, and what it does is it basically gives you a very long list of all the programs you have available to install to your system. You can narrow the list down to programs you just want to look at with the search function. When you find a program you want, you simply mark its tick box and click "Apply" to install.

The package manager lists all the programs from repositories, which are just huge pools of programs. Firefox 3.6 isn't out in the repositories that come with the Ubuntu install yet, but you can add the repository from the Firefox team by following phillw's instructions 3 posts above this post.

To use Synaptic, click System -> Administration -> Synaptic Package Manager in the upper left-hand corner.

Hope this helps! Please post questions if you have any!:D

---

### Post by tekkidd on 2010-02-14
> **RevStHuck said:**
> Okay, complete and total noob here.  I've been trying to figure this out to the best of my ability but I'm simple I suppose 'cause it just ain't happening.

I'm trying to install a new version of Firefox and/or Opera on Ubuntu and it isn't working.  I download Opera and click "Open with GDebi package installer" and get an error message: "Dependency is not satisfiable: libqt3-mt"  

So what am I doing wrong and what do I need to do to fix it?  And please, explain in simple terms I'm afraid I really am terribly new to this OS.  We all got to start sometime, right?  Thank you.

go to synaptic and type in the dependency and install it

---

### Post by k3lt01 on 2010-02-14
> **RevStHuck said:**
> Okay, complete and total noob here.  I've been trying to figure this out to the best of my ability but I'm simple I suppose 'cause it just ain't happening.Best piece of advice I could give you is if your are a noob I would stick with what's in the Ubuntu repositories for a while. Then you could add Backports and/or Proposed (both official Ubuntu repositories). Once you are comfortable with using official repositories then branch out and add "unofficial" repositories like Medibuntu and maybe a ppa. When you are comfortable with how it all works then go searching the web for other applications but be aware you may not be able to get an easy fix to any problems that crop up.

---

