---
title: "Newbie - installing software/using GTK and &quot;make&quot;"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Mr. Wolf on 2009-08-20
I'm sure this is a duplicate, so if anyone has a thread or guide to point to, please feel free...

I'm brand new to linux, and the concept of downloading and "installing" software is rather new to me.

I have found a nifty little program I downloaded.  It is asking me to extract it, and make the file, and assumes I have GTK to do so.

I tried the "make" command in a terminal in the proper directory, but it gave tons of errors and appears it couldn't find GTK.  So I went to Synaptic, and can't figure out if I actually have the GTK compiler.


Here is what I know:
I have linux, its Ubuntu, a Debian distribution.
I have 8.x, fully updated (but not upgraded to 9.x.)
GTX is a compiler.
"Make" is a command to compile a program written in C.

Other than that, I'm rather lost I think.  I couldn't even figure out (thanks to their woefully lacking instructions) how to install Google Earth for linux.  The fact is, other than using Synaptic, or hints provided by software such as Virtual Box on how to add software to Synaptic, I don't have the foggiest clue how to install software on linux.

Some basics would be nice, since I'm a complete linux-fool at this point who was, unfortunately, stuck in Windows for all of my life.  It doesn't help that I suffered severe cognitive loss thanks to lead paint fume exposure a few years back so the brain is a little fried.  So, information like "installing software requires recompiling the kernel" if true, and "here's what GTK does" and anything else applicable would be nice.  I'm not a moron, I just don't know anything about Linux and am trying to ask pointed questions so I can slowly learn at my own pace, rather than trying to muddle through a 500 page book of information I'll forget when I need to finally use it.


Thanks for your help, and especially for your patience.

I hate Windows, and want desperately to get away from it.  Installing it on a virtual machine running on Linux is but the first step.

---

### Post by theozzlives on 2009-08-20
Generally they have readme files. The most common way I know is:
```
./configure
make
make install
```
I forget if you need sudo or not.

---

### Post by Delever on 2009-08-20
If this program is packaged the standard way, you will need to:

apt-get install build-essential
[edit: build-essential, not build-essentials]

go to the directory of your program and execute the following:
./configure --prefix ~/here
make
make install

"./configure" is the script which prepares program for compiling. it checks if you have all necessary things to compile. If it gives warnings that something is missing, go to synaptic and install *-dev packages of what is missing.

"./configure --prefix ~/here" will install the program into "here" folder in your home directory. Otherwise program would be installed into system, which is not very good for non-deb programs (compiled from source, as this one).

make will build your program. 

make install will put it into ~/here

and you can execute it by calling ~/here/bin/programname

---

### Post by Delever on 2009-08-20
> **theozzlives said:**
> 
I forget if you need sudo or not.

You need sudo when installing into system. I suggest not to. However, if you must, install into /opt directory.

---

### Post by philcamlin on 2009-08-20
> **theozzlives said:**
> Generally they have readme files. The most common way I know is:
```
./configure
make
make install
```I forget if you need sudo or not.

use this 
```

./configure
make
sudo make install

```

---

### Post by Mr. Wolf on 2009-08-20
I guess my message isn't getting through.

I know the following about linux:

I have Ubuntu, a Debian distribution.
It's running on an x86 processor-based computer.
It has a GUI.
I installed (somehow) a virtual machine to run Windows.
I know how to browse through the linux file system.
I know generally how to browse through Synaptic.

That is really about the extent of my knowledge of Linux, other than maybe it was created as a flavor of Unix by Linus Torvalds of Norway or something like that (thank you Linus!) and that it somehow got associated with a Penguin icon.  I know what a kernel is (operating system at the processor-level) and what a GUI is (I used to write them in LabVIEW before the fire.)  I generally know what an application layer is, but not if Linux has or uses one.  But really, other than these things, please assume near-total ignorance on my part.  I was smart enough to pick Linux, knowledgeable enough to download and install it on my own, and somehow figured out (but subsequently forgot) how to install VirtualBox on my computer so I could transfer my Windows system over and finally give Bill Gates the boot.


I don't know what "installing" a program means in Linux - in Windows, you run an installer which copies an executable and any DLLs it calls, provides links in your registry as necessary, and creates other dependencies based on your system configuration.  I don't know if you do similar in Linux, and what "make"ing a file using the GTK compiler means (is it compiling it as an executable and putting it somewhere on your system so you can run the executable, or is it compiling the program as part of your kernel?)

I am an absolute beginner who most people would assume has no business using Linux.  But I despise Windows and I can no longer deal with its security issues.  I have difficulty learning, but very much WANT to learn how to make my way around Linux.  So, in explaining things to me, please start at the most basic level.  It should start something like:  "Okay, you have downloaded a software package that is labeled by its maker to be compiled using the GTK compiler, to go from raw code in the C programming language, to an executable your system can run (as part of the kernel, or as a standalone executable running on some part of the system; whichever is applicable.)  To do this, you open up a terminal.  You can either navigate to the folder where the make file is for your executable, or (some other option here.)  To make the file using GTK, you first have to (do this) to make sure you have GTK and can access it.  Once you have done this (above mystery procedure) you can now compile the code using the "make" command.  On your terminal command line, type the following:  #/your directory here/make (options you suggest).  This will compile the software (with these parameters and options as you have chosen above - if you want to ____, you can use the _____ option for the "make" command.  Once you have completed the build, all you have to do is (how the heck do I now find the executable, create a shortcut, and place it in the proper place in the "applications" menu???)


I hope this helps resolve the format and level of instruction I require on the subject.  I learn not by following instructions, but by following logic which explains what I am doing and how to do it and what my options are.  Simply telling me "make.../install..../configure...etc." doesn't help me in the slightest.  I apologize for this, and would be grateful for your endearing patience.  Trust me, once I learn something this way, I'll be the one responding to others who need help because I will then have a full and complete understanding.

Thanks again!

---

### Post by Delever on 2009-08-20
Ok then.

I suggest you to [Read About it Here]("http://www.psychocats.net/ubuntu/installingsoftware").

Summary: Look in repositories first. Add remove.

Otherwise, if you can find .deb files for your ubuntu version - great! They are what you should use. They install binary (executable (exe, but not exe)) files right into appropriate folders, and you can uninstall such program using synaptic or apt-get. (for example - [try getting opera browser to see how it works]("http://www.opera.com/")).

As last resort, you can get source code and try to compile it. Sometimes, after installing appropriate -dev libraries, it works. Otherwise it does not and requires more knowledge to do it. In such case it is ok, because such program is probably not suitable for general use yet.

---

### Post by mrbiggbrain on 2009-08-20
ok first GTK is the "Gnome Tool Kit" not a compiler, or even close, next the compilers for linux are most part of GCC (GNU compiler collection) and they come prebuilt in, they are part of the GNU toolchain, and are required when building a linux system so are always included.

Without knowing the exact errors i cant tell you what happening, could you please post those in a code box?

---

### Post by wojox on 2009-08-20
[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

---

### Post by Delever on 2009-08-20
Sorry, we can't really write full tutorial to linux here. This is basically forum full of questions, most of them duplicated. So you can ask.

I am not sure if you REALLY want to learn things at such depth as to fully understand makefiles, GNU automake, and so on. But to show the glimpse of what you are up to, i give you several links:

[http://www.gnu.org/software/make/](http://www.gnu.org/software/make/)
[http://www.gnu.org/software/automake/](http://www.gnu.org/software/automake/)

But really, if someone already did the hard job and made .deb package, use it. Repositories (those are the sources used by add/remove) are basically storage of such prepared .deb packages, tested on your system.

---

### Post by theaaronc on 2009-08-20
> **Mr. Wolf said:**
> I guess my message isn't getting through.

I am an absolute beginner who most people would assume has no business using Linux.  




I think the links in previous posts will probably cover your question from a technical perspective, but I thought I'd put in a note from someone who was a "aboslute beginner" not long ago.

I don't think that you'll find anyone in the Ubuntu community with the opinion that you have "no business" using Linux. I've yet to find a lack of people more than willing to help with any issue. Also, as a beginner, keep in mind that Google and the Ubuntu Forums are your friend. I've found that I can find info on a lot of my questions by prefixing a search with Ubuntu and phrasing the search as a question. An example would be "ubuntu how do I install software". More often than not you'll end up right here in the forums =)

Welcome to Ubuntu and have fun!

---

### Post by Mr. Wolf on 2009-08-20
> **Delever said:**
> Ok then.

I suggest you to [Read About it Here]("http://www.psychocats.net/ubuntu/installingsoftware").

Summary: Look in repositories first. Add remove.

Otherwise, if you can find .deb files for your ubuntu version - great! They are what you should use. They install binary (executable (exe, but not exe)) files right into appropriate folders, and you can uninstall such program using synaptic or apt-get. (for example - [try getting opera browser to see how it works]("http://www.opera.com/")).

As last resort, you can get source code and try to compile it. Sometimes, after installing appropriate -dev libraries, it works. Otherwise it does not and requires more knowledge to do it. In such case it is ok, because such program is probably not suitable for general use yet.

Thank you.  That's definitely useful.  It's exactly the type of explanation I was looking for.  I didn't think Ubuntu would be so difficult as to force me to /make or things of that nature.  Doing a general search is useless if you don't know what to look for.

Maybe we should have a sub-thread for the Absolute Beginner Forum called "Stupid Questions."  But then, I thought that "Absolute Beginner" meant that this forum would be full of what most consider to be "stupid questions."

Thank you for your response.  Again, it is exactly what I was looking for!

---

### Post by Mr. Wolf on 2009-08-20
Okay, I got the necessary information about Add/Remove.

What I'm trying to do is more advanced.  I found a program I like.  It comes in a tarball.gz, which I already unzipped.  The first problem is the package didn't include a configure file.

The install help file suggested that I "make sure GTK+ >=1.0 and it's header files are installed."

And here is where I am lost again.

I ran through Synaptic to make sure I had GTK+.  I thought I had/installed GTK+2.

This is the first lines of the error:

[INDENT][FONT="Fixedsys"]gcc -c -O2 -fno-strength-reduce -Wall -W -g -DLINUX -DUSEGTK `gtk-config --cflags` main.c
/bin/sh: gtk-config: not found[/FONT][/INDENT]

So I went back to Synaptic to make sure I had "gtk-config, which I didn't apparently.  So I installed it and tried again...same result.

I didn't post the rest of the errors because it seems obvious that they are based on the lack of finding the gtk-config.  I think the problem here is that maybe the program I'm trying to install was created long ago, and the file system may have changed, killing the normal dependencies.  But, I'm not sure.


Any ideas?

I think my real danger is that I used to know more than I do, and I'm operating based on incorrect assumptions, and often make what later seem to be blantly obvious errors, such as assuming GTK was a compiler.  I'm a stubborn *******, but please be nice.  Brain damage sucks and I wouldn't wish it on anyone.  The worst of it is this stuff used to be a cakewalk for me.  I was a damn good programmer at one point.  So don't get frustrated or angry with me - I do plenty of that to myself.  Just know that I used to code with the best of them but am damaged goods now.  Gentle nudges in the right direction work best.  THANKS!

---

### Post by oldfred on 2009-08-21
I cannot help with your exact problem. Part of the history of Linux was in the old days you had to do what you want to do but there were many dependencies that had to be installed first. They have just about eliminated that problem with the repositories of programs for Ubuntu by version and .deb files that are precompiled and install easily. 

Some old applications may not be maintained because something new and better has taken its place. What is the program and what does it do? Perhaps someone can recommend an alternative that may be better based on their experience.

---

### Post by Delever on 2009-08-21
> **Mr. Wolf said:**
> Okay, I got the necessary information about Add/Remove.

What I'm trying to do is more advanced.  I found a program I like.  It comes in a tarball.gz, which I already unzipped.  The first problem is the package didn't include a configure file.

The install help file suggested that I "make sure GTK+ >=1.0 and it's header files are installed."

And here is where I am lost again.

I ran through Synaptic to make sure I had GTK+.  I thought I had/installed GTK+2.

This is the first lines of the error:

[INDENT][FONT="Fixedsys"]gcc -c -O2 -fno-strength-reduce -Wall -W -g -DLINUX -DUSEGTK `gtk-config --cflags` main.c
/bin/sh: gtk-config: not found[/FONT][/INDENT]

So I went back to Synaptic to make sure I had "gtk-config, which I didn't apparently.  So I installed it and tried again...same result.

I didn't post the rest of the errors because it seems obvious that they are based on the lack of finding the gtk-config.  I think the problem here is that maybe the program I'm trying to install was created long ago, and the file system may have changed, killing the normal dependencies.  But, I'm not sure.


Any ideas?


Usually you need to look for packages which end with "-dev". And since they are libraries, they also may start with "lib". So I went into synaptic and done a search for "gtk+". The closest I could find in my system (ubuntu jaunty), is "libgtk2.0-dev". I suggest you to follow these steps - your gtk version might differ.

Also realize that no matter how weird message looks, many people get the same weird message doing the same thing as you. So if you go to google and copy paste your error message (gtk-config: not found) into search field, it will return thousands of results. First one is link to this forum, which has answer suggesting to get package "libgtk1.2-dev" - already on the same track.

> **Mr. Wolf said:**
> 
I think my real danger is that I used to know more than I do, and I'm operating based on incorrect assumptions, and often make what later seem to be blantly obvious errors, such as assuming GTK was a compiler.  I'm a stubborn *******, but please be nice.  Brain damage sucks and I wouldn't wish it on anyone.  The worst of it is this stuff used to be a cakewalk for me.  I was a damn good programmer at one point.  So don't get frustrated or angry with me - I do plenty of that to myself.  Just know that I used to code with the best of them but am damaged goods now.  Gentle nudges in the right direction work best.  THANKS!

No one here thinks that beginner is stupid. If one can't fly a plane, that means exactly that - one can't fly a plane. Yet.

---

