---
title: "make command / how to unpack files"
date: 2011-07-13
forum: New to Ubuntu
---

### Post by margaux on 2011-07-13
Hi,

I'm trying to download a program called MACH 1.0

The README files says: 
INPUT FILES
===========

Mach 1.0 needs a Merlin format data and pedigree files as input.
[FONT=Georgia]
[FONT=Trebuchet MS]I have several questions. 

When I go to the Merlin website, these are the instructions:
[/FONT][/FONT]This version is recommended for Unix users with access to the GNU C++ compiler. To install Merlin, unpack the archive below,  type make and follow instructions. Have fun! 
      [B][merlin-1.1.2.tar.gz]("http://www.sph.umich.edu/csg/abecasis/Merlin/download/merlin-1.1.2.tar.gz")
[/B]
First of all, what is C++? Second, what does "type make" mean? I assume this means in the terminal, but when I type "make" (after downloading the program files) I get this error message:
[FONT=Courier New]
make: *** No targets specified and no makefile found. Stop[/FONT].

There is also this option on the Merlin website:

[FONT=Courier New]If you do not have access to a C++ compiler, one of the  following precompiled versions may work on your system:[/FONT]
      [Linux-merlin.tar.gz]("http://www.sph.umich.edu/csg/abecasis/Merlin/download/Linux-merlin.tar.gz")      For GNU/LINUX systems
[FONT=Tahoma]
My question is, what do I do AFTER I have these files on my system? How do I run them?[/FONT] 
Any help would be greatly appreciated!

---

### Post by seawolf167 on 2011-07-13
C++ is a programming language, the default compiler on Ubuntu is GCC

First, get the packages so you can compile from source

```
sudo apt-get install build-essential
```

then download the tar.gz file, by default it will go to ~/Downloads, so cd to that directory

```
cd ~/Downloads
```

extract the file and its contents

```
tar xvzf merlin-1.1.2.tar.gz
```

cd to the newly made directory

```
cd merlin-1.1.2
```

configure the package (if needed)

```
./configure
```

then make it

```
make
```

and finally, install it

```
sudo make install
```

you can then remove the source and tar.gz

```
cd ..
rm merlin-1.1.2.tar.gz
rm -rf merlin-1.1.2
```

and run the program (assuming the program name is *merlin*)

```
merlin&
```

---

### Post by margaux on 2011-07-13
Hi again,

So I only got as far 
cd ~/Downloads

once I entered 
tar xvzf merlin-1.1.2.tar.gz

I got these error messages:
tar: merlin-1.1.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

I also tried cd-ing to Documents and trying that command again, because this is where the merlin-1.1.2 file is showing up on my system. 

Just for kicks, I tried cd-ing to merlin-1.1.2, and that worked, but once I typed:
./ configure

I got the error message:
bash: ./ configure: No such file or directory

Ah, I hope this is fixable. 
Thanks for your help.

---

### Post by seawolf167 on 2011-07-13
Are you sure you are in the correct directory? If you type

```
ls
```can you see the filename?

You can also use tab completion to ensure you have the correct name and the file exists there

```
cd ~/Download
tar xvzf mer[TAB]
```Edit: just re-read your post, instead of cd-ing to ~/Downloads, cd to ~/Documents

There is not a space anywhere in the command 

```
./configure
```

Edit again:

If there isn't a configure file in the directory merlin-1.1.2, then just proceed with the *make* command, you may not have to do a make install either, it'll probably just leave the binary there for you to use, see if there is a README file contained in the tarball with more information

---

### Post by margaux on 2011-07-13
Okay! Slight progress.

Thanks for the tip on tab completion. 

When I ls in my Documents directory, merlin-1.1.2/ is listed as a directory. 
When I enter the command: 
tar xvzf merlin-1.1.2/

I get these error messages:
tar: merlin-1.1.2/: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

gzip: stdin: unexpected end of file
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

Just for kicks, I cd-ed to the merlin-1.1.2/ directory and tried 
./configure

but got the error message:
bash: ./configure: No such file or directory. 

From here, I also tried:
make

but got the same thing as before:
make: *** No targets specified and no makefile found. Stop.

Any ideas?

---

### Post by seawolf167 on 2011-07-13
You already have extracted the tarball to the directory merlin-1.1.2, so cd to that directory and run the *make* command

```
cd ~/Documents/merlin-1.1.2
make
```

---

### Post by skatinjj on 2011-07-13
I am not home so I can not try to install this program.

Is there a README or anything of the sort in ~/Documents/merlin-1.1.2?

---

### Post by seawolf167 on 2011-07-13
I just grabbed the tarball myself to take a look at it (didn't install it though - not sure if the *make* command will throw any errors since there isn't a configure script, this would be a programming problem if any exist)

step-by-step:

```
cd ~/Downloads
mkdir merlin
cd merlin
wget http://www.sph.umich.edu/csg/abecasis/Merlin/download/merlin-1.1.2.tar.gz
tar xvzf merlin-1.1.2.tar.gz
cd merlin-1.1.2
make all
sudo make install
cd ~/Downloads
rm -rf merlin
```the binaries are now installed to /usr/local/bin

---

### Post by margaux on 2011-07-13
After 
cd ~/Documents/merlin-1.1.2

I type
make

And get the same error message as always:
make: *** No targets specified and no makefile found. Stop. 

The README associated with this stuff says:

COMPILING AND INSTALLING MERLIN
Type make and follow instructions. 

START OF BRIEF INSTRUCTIONS
A more detailed tutorial is available on the web at:
[http://www.sph.umich.edu/csg/abecasis/Merlin/tour](http://www.sph.umich.edu/csg/abecasis/Merlin/tour)
A summary reference for all Merlin options is available at:
[http://www.sph.umich.edu/csg/abecasis/Merlin/reference.html](http://www.sph.umich.edu/csg/abecasis/Merlin/reference.html)

So, no help there.

---

### Post by margaux on 2011-07-13
Dear Seawolf,  You are a superstar.   I could cry.   Okay so it looks like everything went through! After sudo make install went through, I  typed: cd ~/Downloads  and then  rm -rf Merlin  This didn't do anything (and I don't think it was supposed to), but in any event that's better than an error message.   So now, can I just type merlin from here? (I'm still in the Downloads directory).  I'm almost there!!! THANK YOU!!!  :]

---

### Post by margaux on 2011-07-13
Oh jeez.

That message went through without any formatting! I'm sorry. 

In any event, everything went through. Now I'm in the Downloads directory and wondering if I can access merlin from here or if I should go back via cd ..  

Thanks again!

---

### Post by seawolf167 on 2011-07-13
> **margaux said:**
> Dear Seawolf,  You are a superstar.   I could cry.   Okay so it looks like everything went through! After sudo make install went through, I  typed: cd ~/Downloads  and then  rm -rf Merlin  This didn't do anything (and I don't think it was supposed to), but in any event that's better than an error message.   So now, can I just type merlin from here? (I'm still in the Downloads directory).  I'm almost there!!! THANK YOU!!!  :]

the folder name is case-sensitive; merlin is not the same as Merlin

the binary(s) installed to /usr/local/bin which in your $PATH variable, so simply typing the name of the binary in a terminal should make it do whatever its supposed to do (you may have to pass it arguments and stuff, I have no clue what the program is supposed to do or how it is supposed to work)

---

### Post by FormatSeize on 2011-07-13
> **margaux said:**
> 
 
I type
make
 
And get the same error message as always:
make: *** No targets specified and no makefile found. Stop. 

All they are telling you to do is type make? I'm not sure exactly what Merlin is, but I've compiled hundreds of packages manually, and they usually begin with some sort of configure script running. That's done with either ``./configure'' or ``perl [configfile]'', and then type make.
 
When you go to the directory that is created when after untarring the tarball, is there a file in there that is called ``Configure'' or ``config.guess''? From my experience, you are getting this error because there is no makefile (as you can see). But there is no makefile until after you run some sort of configuration script, which will create an appropriate makefile for the system targeted for installation. 
 
I'm not at home right now, so I can't untar anything, but either there's a configuration script missing, or there's something else that's wrong with this particular download. 
 
Does the README specify a target for make?

---

### Post by margaux on 2011-07-13
Well yeah, that was the confusing part for me too! 

After following the code lines Seawolf provided, I got Merlin to open up in my terminal. Now my ultimate goal was to run a program called MACH 1.0, which you can see from its read me file: 
**README File**

INPUT FILES
===========

Mach 1.0 needs a Merlin format data and pedigree files as input.
[FONT=Trebuchet MS]
[/FONT][FONT=Verdana]required Merlin to run. So I'm still working on that. Once I open Merlin in my system, I'm getting a few "FATAL ERROR" messages, but this is certainly related to the datafiles I'm running and not to the installation.


[/FONT]

---

### Post by seawolf167 on 2011-07-13
So the "merlin" issue is solved then?

---

### Post by margaux on 2011-07-13
For now. It's multi-faceted. 

Seawolf, you're very helpful. 

I wonder if you could explain one more thing to me. 
I just tried to install another tar.gz package, and followed the instructions you'd listed before with merlin. 

I created a directory (mkdir MACH) , moved there (cd MACH), and then used wget to "get" the program:

wget [http://www.sph.umich.edu/csg/abecasis/MACH/download/Linux-mach.tar.gz](http://www.sph.umich.edu/csg/abecasis/MACH/download/Linux-mach.tar.gz)

Which worked (!)

I then used:
tar xvzf Linux-mach.tar.gz

to unpack it (? -- I think that's what this command does)

which gave me the directory name of:
mach-1.0.16/

I cd-ed to this directory, and like before tried the command
make all 

(in theory to be followed by sudo make install)

HOWEVER, this time I got a slightly different error message than what I'd been getting before: 

make: ***No rule to make target 'install'. Stop

Any clue what's going on here?

---

### Post by margaux on 2011-07-13
just for clarification,

after I unpacked the file and tried to "make all" in the directory mach-1.0.16 and it didn't work, I also tried the command "make all" in 

cd Linux-mach

which gave me the bash: error I've seen a million times before (no such file or directory)

---

### Post by seawolf167 on 2011-07-13
I haven't downloaded and looked at this tarball yet, but try

```
./configure
make
sudo make install
```

after you cd to the directory, i.e.

```
cd mach-1.0.16/
```

---

### Post by margaux on 2011-07-13
From inside the directory

~/Downloads/MACH/mach-1.0.16$ 

I type:
./configure

and I get:
bash: ./configure: No such file or directory. 

So no luck! 

(I also tried ./configure make) <-- silly?  (It didn't work either)

---

### Post by seawolf167 on 2011-07-13
Ok so I downloaded the file you listed earlier, inside are two binaries (this is not a source compile) called "mach1" and "thunder" both of which are 64-bit executable binaries

```
file mach1
```gives

```
mach1: **ELF 64-bit LSB executable**, **x86-64**, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.0, not stripped

```and

```
file thunder
```gives

```
thunder: **ELF 64-bit LSB executable**,** x86-64**, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.0, not stripped

```so it looks like the same problem in your previous thread - executing a 64-bit binary on a 32-bit system.

---

### Post by margaux on 2011-07-13
Aw that's too bad. 

I'm just running this 32-bit system (i686) on an old Dell PC. I'm not dual booting, I wiped Windows off. It's a dual-core processor, would you recommend reinstalling xubuntu lucid linix with the x86_64 bit platform?

I supposed that would mean I'd have to reinstall everything else...but if I keep coming up against this problem it might be worth it.

---

### Post by seawolf167 on 2011-07-13
With the problems you are having running the software you want to run, it may be worth it.

If you decide to reinstall, there are a couple things I suggest:

[LIST=1]
[*]Make a backup with [Clonezilla ]("http://www.clonezilla.org")in case something goes wrong or you want to revert back
[*]Move your /home partition it its own dedicated partition, a guide is [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving")
[*]Move anything you want to keep (files/documents/etc) that are not in your new /home partition to it before you reinstall
[*]When reinstalling, choose to manually partition the disks, then don't change the partition table, just mount /home as /home, and swap as swap (since they already exist). Your installation will just be the new / (root), when you boot, all your settings and files/folders will already be there on your other partition
[/LIST]

---

