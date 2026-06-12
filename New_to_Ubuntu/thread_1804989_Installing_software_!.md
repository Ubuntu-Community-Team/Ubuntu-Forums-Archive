---
title: "Installing software !"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by margaux on 2011-07-15
Hi all!


I figured out my issue from before, I wasn't copying the proper website location.

So it should have been:
wget [http://www.sph.umich.edu/csg/abecasis/MACH/download/mach.1.0.17.Linux.tgz](http://www.sph.umich.edu/csg/abecasis/MACH/download/mach.1.0.17.Linux.tgz)

Now I'm having another issue, when I use the command:
tar xvzf mach.1.0.17.Linux.tgz

All this happens:
examples/hapmap.haplos
examples/hapmap.snps
examples/sample.dat
examples/sample.ped
executables/mach1
executables/thunder
README

But then what do I do next? How do I actually install and run this software from here?

Thanks!

---

### Post by akand074 on 2011-07-15
Read the readme. It'll tell you. There's a reason that file is called README. It's usually something along the lines of

```
./configure
make
make install
```

but isn't always the case I believe.

---

### Post by dFlyer on 2011-07-15
> **margaux said:**
> Hi all!


I figured out my issue from before, I wasn't copying the proper website location.

So it should have been:
wget [http://www.sph.umich.edu/csg/abecasis/MACH/download/mach.1.0.17.Linux.tgz](http://www.sph.umich.edu/csg/abecasis/MACH/download/mach.1.0.17.Linux.tgz)

Now I'm having another issue, when I use the command:
tar xvzf mach.1.0.17.Linux.tgz

All this happens:
examples/hapmap.haplos
examples/hapmap.snps
examples/sample.dat
examples/sample.ped
executables/mach1
executables/thunder
README

But then what do I do next? How do I actually install and run this software from here?

Thanks!

read the README.

---

### Post by azertyh on 2011-07-15
hello,
there is an application called mach in the repos, with this descrption "mach allows you to set up clean roots from scratch for any distribution or
distribution variation supported".
if it's what you want, install it from synaptic package manager.

---

### Post by Jose Catre-Vandis on 2011-07-15
> **azertyh said:**
> hello,
there is an application called mach in the repos, with this descrption "mach allows you to set up clean roots from scratch for any distribution or
distribution variation supported".
if it's what you want, install it from synaptic package manager.

That's a different program ;)

It's probably best to put the tar file into a separate folder before you untar as it doesn't create one. Inside you will find two folders; examples and executables and the README file. 

For the mach you are looking at, it comes with precompiled binaries (mach1 and thunder) in the executables folder.

Instructions on how to use mach are in the README, hope they make more sense to you than they did to me ;)

---

### Post by Elfy on 2011-07-15
I have just closed your other 2 threads on this - please do not post duplicates.

---

### Post by margaux on 2011-07-15
Sorry for the duplicates -- at the time there were 3 separate issues. 
I did read the README file, thanks. It doesn't help. And I've tried ./configure and it gives me this:

-bash: ./configure: No such file or directory

Any ideas?

---

### Post by Elfy on 2011-07-15
I did post in the one I was posting in :)

---

### Post by margaux on 2011-07-15
Okay so I cd-ed to the 'executables' directory, where there are two additional directories listed, but then when I try to cd to mach1, it gives me this error message:

-bash: mach1: command not found

---

### Post by akand074 on 2011-07-15
> **margaux said:**
> Sorry for the duplicates -- at the time there were 3 separate issues. 
I did read the README file, thanks. It doesn't help. And I've tried ./configure and it gives me this:

-bash: ./configure: No such file or directory

Any ideas?

I just downloaded the tarball. This application doesn't actually install. Just go to the executable folder from the Terminal and run the program.

i.e assuming it's in your home folder

```
cd ~/mach/executables
./mach1
./thunder
```

---

### Post by margaux on 2011-07-15
Ah, I just saw your post in the wget thread.  --->>>

Reading the README is always a good start. 

There's a makefile in the extracted folder.

Running make from a terminal gives this

 	Code:
 	[email]hobgoblin@hobgoblin:~/Desktop/mach2qtl.source[/email].V110$ make
Generic Source Distribution
 
This Makefile will compile and install mach2qtl on your system
 
Type...           To...
make help         Display this help screen
make all          Compile everything 
make install      Install binaries in /usr/local/bin
make install INSTALLDIR=directory_for_binaries
                  Install binaries in directory_for_binaries
make clean        Delete temporary files 
I'm not going any further with it - I don't want to install it :smile:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)



<----

Can you show me the code lines you used to get to the extracted folder (and thus the makefile?) 

I have these when I ls to my MACH directory:

README    executables  index.html.1  mach.1.0.17.Linux.tgz
examples  index.html   index.html.2  mach.1.0.17.Linux.tgz.1

Then I cd to 'executables'

and get 

mach1    thunder

so where does the makefile come in and how do I gain access to it? 

Thanks!

---

### Post by margaux on 2011-07-15
I'm getting these responses a little delayed -- thanks [akand074]("http://ubuntuforums.org/member.php?u=840786")!!

The ./ was what I needed. 

I kept trying just mach1 and nothing was working for me. 

So ./mach1 does the trick

I appreciate it!

---

### Post by akand074 on 2011-07-15
As I posted earlier. There is no make file. That's actually an executable stand-alone application in the executable folders. (i.e it's kind of like a portable application). 

Why to you keep downloading/installing applications in tarballs. Have you checked the Ubuntu repositories (or PPAs) for your software first? Second is there no .deb file for the software you are looking for?

---

### Post by akand074 on 2011-07-15
> **margaux said:**
> I'm getting these responses a little delayed -- thanks [akand074]("http://ubuntuforums.org/member.php?u=840786")!!

The ./ was what I needed. 

I kept trying just mach1 and nothing was working for me. 

So ./mach1 does the trick

I appreciate it!

Cool. Glad it worked!

---

### Post by margaux on 2011-07-15
Hi again,

In response to:

> **akand074 said:**
> As I posted earlier. There is no make file. That's actually an executable stand-alone application in the executable folders. (i.e it's kind of like a portable application). 

Why to you keep downloading/installing applications in tarballs. Have you checked the Ubuntu repositories (or PPAs) for your software first? Second is there no .deb file for the software you are looking for?

I don't know why I'm installing these things as tarballs. What is a tarball? 
What is a .deb file?

---

### Post by PhantmKllr on 2011-07-15
> **margaux said:**
> Hi again,

In response to:



I don't know why I'm installing these things as tarballs. What is a tarball? 
What is a .deb file?
Tarballs are a kinda generic way to distribute software on Linux.

.deb files are Ubuntu's native package format for installing programs. When given the choice, always use the .deb file, it'll do everything for you.

---

### Post by akand074 on 2011-07-15
> **PhantmKllr said:**
> Tarballs are a kinda generic way to distribute software on Linux.

.deb files are Ubuntu's native package format for installing programs. When given the choice, always use the .deb file, it'll do everything for you.

Exactly.

tarball is an archive (like zip and rar), .deb is an executable installer, like .exe. Anything you install from Ubuntu Software Centre (the repositories) is stored as a .deb file.

---

