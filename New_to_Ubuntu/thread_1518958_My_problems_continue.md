---
title: "My problems continue"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-06-27
I would like to think that I am making progress but it's slow  work.

I am running 10'04 which I am dual booting with XP. So I can open Firefox and was looking around for a basic primer on what to do next.

I found a reference to the Synaptic Package manager and that has helped.

Somewhere along the way I have started getting a warning during boot that' I could not update ICEAuthorityf file.

What is ICE Authority file and how does it get updated>

The website that pointed to the Synaptic Package manager also recommended Automatix as a could thing for a beginner to load but when I pursue that I find that it died a couple of years ago and could be replaced witj Ultamatix.

So i download that and try to load it and I get a failure talking about Dependency and Python !!!

So that means there are two problems that  I am stuck on. Please Hrlp

Sandy

---

### Post by cogier on 2010-06-27
To load software go to **Applications>Ubuntu Software Centre** You will find loads there and it will take care of everything for you.

---

### Post by cariboo on 2010-06-27
Open an Applications->Accessories->Termianl and type:

```
sudo chown <user>:<user> /home/<user>/.ICEauthority
```

where <user> is your user name.

As for where to start, I would suggest you have a look at [this]("http:///ubuntuforums.org/showthread.php?t=801404") sticky.

I would suggest you stay away from programs like Ultamatix, it is almost as old as Automatix. Almost everything you need can be installed using Synaptic package manager.

---

### Post by jmszr on 2010-06-27
Sandy.1,

Here are links to some good resources: [http://ubuntu-manual.org/](http://ubuntu-manual.org/) , [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid) ,
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404) , and:[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)  .

This is something you might be interested in: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Also, this comes in handy: the Ubuntu-Google search engine for Firefox: [http://www.ubuntu-search.org/](http://www.ubuntu-search.org/)

Edit: This may be helpful for you: [http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

---

### Post by Sandy.1 on 2010-06-28
> **cariboo907 said:**
> Open an Applications->Accessories->Termianl and type:

```
sudo chown <user>:<user> /home/<user>/.ICEauthority
```where <user> is your user name.

As for where to start, I would suggest you have a look at [this]("http:///ubuntuforums.org/showthread.php?t=801404") sticky.

I would suggest you stay away from programs like Ultamatix, it is almost as old as Automatix. Almost everything you need can be installed using Synaptic package manager.

Happily set out to try your recommendation and collected the following failure message.
chown: missing operand after `sandy1' Do believe that I copied the instruction correctly.

Thanks for all the other suggestions which i shall read.

Please accept that I have no knowledge of Linux at all.

What is ICE Authority?

Sandy

---

### Post by varunendra on 2010-06-28
> **Sandy.1 said:**
> Happily set out to try your recommendation and collected the following failure message.
chown: missing operand after `sandy1' Do believe that I copied the instruction correctly.

<user> has to be replaced by the user id, the one that appears before '@' sign in the terminal prompt (it may differ from the name that appears in the login screen). Let us assume it is 'sandy1' (without quotes of-course), then the command would be:
```
sudo chown sandy1:sandy1 /home/sandy1/.ICEauthority
```
After entering this command, the terminal would ask you to enter your password. Type in your password that you use to log in (it won't show up while typing, just type it correctly & press enter).

If it again returns the same error, copy what you type in the terminal & post here; also, post the output of the commands```
ls /home
```and```
ls -a
``` (just copy-paste the output).

---

### Post by anewguy on 2010-06-28
And since you are a beginner.......

The reason everyone prefers you go through Synaptic Package Manager is so that you don't run into the problems you already hit about dependencies.  Basically, when you install a software package, it relies (depends) on other pieces of software (libraries, etc.) in order to run.  When you tried to install the way you did, these required pieces aren't picked up.  If you go through Synaptic Package Manager, you won't have this problem as it will determine automatically what else needs to be installed.  This is one of the main points about using the package manager, the other being that most of what you would install is supported and would be updated if needed as the system is updated.

Dave ;)

---

### Post by sandyd on 2010-06-28
> **Sandy.1 said:**
> I would like to think that I am making progress but it's slow  work.

I am running 10'04 which I am dual booting with XP. So I can open Firefox and was looking around for a basic primer on what to do next.

I found a reference to the Synaptic Package manager and that has helped.

Somewhere along the way I have started getting a warning during boot that' I could not update ICEAuthorityf file.

What is ICE Authority file and how does it get updated>
**When you run programs using sudo, and not gksudo (yes, there is a difference!, ```
gksudo nautilus
``` is not the same as ```
sudo nautilus
```, some of the programs will screw up the .ICEAuthority file. just remember to use gksudo instead of sudo, and everything should be fine.**
The website that pointed to the Synaptic Package manager also recommended Automatix as a could thing for a beginner to load but when I pursue that I find that it died a couple of years ago and could be replaced witj Ultamatix.

So i download that and try to load it and I get a failure talking about Dependency and Python !!!
**Don't use it, a lot of people end up with screwed up systems after using the automatic installers & such because ubuntu is constantly updated.**
So that means there are two problems that  I am stuck on. Please Hrlp

Sandy.

---

### Post by Sandy.1 on 2010-06-29
<user> has to be replaced by the user id, the one that appears  before '@' sign in the terminal prompt (it may differ from the name that  appears in the login screen). Let us assume it is 'sandy1' (without  quotes of-course), then the command would be:
 	Code:
 	sudo chown sandy1:sandy1 /home/sandy1/.ICEauthority 
After entering this command, the terminal would ask you to enter  your password. Type in your password that you use to log in (it won't  show up while typing, just type it correctly & press enter).

That worked a treat once I fed in the right user name. I'm sandy not sandy1.

So no more error messages during boot but I still don't know what ICEAuthority is???

Many thanks    Sandy

---

### Post by varunendra on 2010-06-29
> **Sandy.1 said:**
> That worked a treat once I fed in the right user name. I'm sandy not sandy1.

So no more error messages during boot but I still don't know what ICEAuthority is???
Many thanks    Sandy

You're welcome Sandy!:)
ICEauthority is explained here:[http://serverfault.com/questions/119580/what-is-iceauthority-file-in-opensuse-11-2](http://serverfault.com/questions/119580/what-is-iceauthority-file-in-opensuse-11-2)
A related explanation is here: [http://manpages.ubuntu.com/manpages/intrepid/man1/iceauth.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/iceauth.1.html)

By the way, here's an additional tip for you:

If you want to quote someone's post, just click on the 'QUOTE' button at the bottom corner of that post. However, you shouldn't quote lengthy posts in their full length.:shock:

Similarly, if you are copy-pasting some text from somewhere, you should consider pasting it as a quote (i.e., placing it in a quotation box). You can do it by selecting the text that you want to put in quotes, then clicking on the 'quote' icon at the top of editing window (one that appears before '#' mark).
If the quote is a command or output of a command, you should use '#' icon instead of 'quote' marks.

You can also do it by writing [ quote ] or [ code ] in the beginning of the text & [ /quote ] or [ /code ] in the last (without spaces inside the bracket!).

:cool:

---

### Post by Segofam on 2010-06-29
Hi,
I am very new to Linux also, here is one of the courses that has  helped me get into the flow of things. There is no real need to download  or install Debian (Ubuntu is based on Debian - Lucid Lynx is the far updated version) to do  this course [http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html) 
Today I  have managed to view AVI's through the command line using mplayer, and I  have also figured out how to change folders and view text using Nano,  gedit, vi and a couple of other text editors. I can now also edit grub  so i can change which OS I want to boot into, Ubuntu or XP,that was really kewl -  well it was to me anyway :)
Ubuntu has been a fun experience for me - a bear to learn though - and has been quite rewarding as I can now - after two months - do everything that I do on XP, including the things that we are not supposed to do :-/
Good luck.
Scott

Here's the table of contents: [http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)

---

### Post by Sandy.1 on 2010-06-29
Thanks to all. let's consider this problem closed

Sandy

---

