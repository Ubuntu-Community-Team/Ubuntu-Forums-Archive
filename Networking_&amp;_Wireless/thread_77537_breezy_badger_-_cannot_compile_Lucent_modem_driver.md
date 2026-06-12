---
title: "breezy badger - cannot compile Lucent modem drivers"
date: 2005-10-17
forum: Networking &amp; Wireless
---

### Post by blastus on 2005-10-17
My guide [Ubuntu 5.04 (Hoary) Lucent WinModem Setup](https://wiki.ubuntu.com/forum/hardware/lucent) doesn't work on Breezy. I can compile the Lucent drivers under Hoary but not under Breezy:

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/neo/data/ltmodem-2.6-alk-7 modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/neo/data/ltmodem-2.6-alk-7/lt_modem.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/neo/data/ltmodem-2.6-alk-7/lt_modem.o] Error 127
make[1]: *** [_module_/home/neo/data/ltmodem-2.6-alk-7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [module] Error 2
```

I have build-essential and linux-headers-2.6.12-9-386 installed. build-essential installed gcc 4.0 or something. Does anyone know how to fix this?

---

### Post by heimo on 2005-10-17
This should set gcc 3.4 as your compiler:
```
sudo apt-get install gcc-3.4
export CC=gcc-3.4

```

---

### Post by blastus on 2005-10-17
[QUOTE=heimo]This should set gcc 3.4 as your compiler:
```
sudo apt-get install gcc-3.4
export CC=gcc-3.4

```[/QUOTE]

I can't do that--no Internet connection. 

Kubuntu appears to have gcc-4.02 20050808 installed. I can't find any references anywhere in the Lucent driver Makefile or anywhere in the Lucent driver code that references gcc-3.4. Why would it expect gcc-3.4?

The Lucent drivers have also been tested up to 2.6.10 according to the documentation. But the issue I'm having is that somewhere Kubuntu Breezy is setup look for a non-existent compiler. I am beginning to think this is a bug in Kubuntu Breezy as the error is related to /usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh. I haven't tried it yet with Ubuntu Breezy.

---

### Post by breakthestate on 2005-10-17
gcc 3.4 might be on the CD.  try adding it to your /etc/apt/sources.list and then apt-get update and then above.

---

### Post by blastus on 2005-10-17
According to [this thread](http://www.ubuntuforums.org/showthread.php?t=56835&page=17), gcc 3.4 is not on the CD. They also say that the Breezy kernel will not compile with gcc 4.0 so I can't even recompile the kernel even if I knew how. According to that thread I tried to install gcc 3.4 by downloading...

```
gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
gcc-3.4_3.4.4-6ubuntu8_i386.deb
```

...and running "dpkg -i" but then it says that cpp 3.4 is missing. I don't know how to fix it or what packages I need to download or how to even verify that gcc 3.4 is installed or even if gcc 3.4 is going to be able to compile my Lucent drivers anyway.

I don't really understand the issues but from what I've read, they should have either compiled the Breezy kernel with the same version (4.0.2) of gcc that the distribution ships with, or at least made the version (3.4.5) of gcc that was used to compile the kernel available on the CD installable via apt-get. 

It seems like Breezy has left everyone who needs to compile kernel modules to get their hardware working (which are typically networking devices) out in the cold.

---

### Post by breakthestate on 2005-10-17
doesn't the cd come with an earlier version of gcc-3.x ?  does that work for you?

---

### Post by blastus on 2005-10-17
gcc 3.3 is on the CD and I have installed it. I don't know if it is the "active" or "default" compiler but I got the same compile error message. From what I've read, I need the exact same version of the gcc compiler that was used to compile the kernel to be able to compile kernel modules. That version is gcc 3.4.5. And I can't think about using gcc 4.0.2 to recompile the kernel (even if I knew how) because people are saying you need gcc 3.4 to compile the Breezy kernel.

Edit: This thread [Compiling kernel modules (GCC3.4 / 4.0) problem](http://ubuntuforums.org/showthread.php?t=77851) explains the issue with Breezy.

---

### Post by breakthestate on 2005-10-17
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/)

I suggest downloading on your computer with internet access all of the files at this site that are relevant to your architecture.  Then move them to your ubunutu box, and then install them using dpkg -i filename.deb.  If you come across one that calls for another one, install the other one first.  This might work.  Be sure, as said above to make gcc-3.4 your default compiler.

---

### Post by freedom on 2005-10-18
And this the solution on distro that is "for human beings" :confused: 
This is ridiculous...
To put GCC version 4.0 with kernel compiled with 3.4 and not include 3.4 with distro...

No comment really.

---

### Post by nobby_trussin on 2005-10-18
i totally agree how stupid to send out a distro with the kernel compiled with a different version of gcc than the one that ships with it - its just asking for trouble. what a pain in the arse. 

you need to get cpp in order to get gcc-3.4 to install and then possibly relink /usr/bin/gcc to /usr/bin/gcc-3.4 and possibly do the same for the cc command

as of yet i've had no joy and no one really seems to have a solution other than recompiling the kernel with gcc-4.0 which, as mentioned in this thread isn't going to work (hence why they didn't compile the kernel in breezy with it).

its frustrating as the module i am trying to compile worked straight away in ubuntu 5.04.

---

### Post by blastus on 2005-10-18
OK, so I downloaded 14 .deb packages. I could not install two packages because one is dependent on the other and, one of them is dependent on a package that does not exist, and at least one package was downgraded! And where is libstdc++6_3.4.4-6ubuntu...deb? I don't even know if I downloaded the right packages or what each one is for. :???: :???: :???: 

I can compile the modem drivers and I can get online, but now Breezy is screwed. OpenOffice.org no longer opens AT ALL and I get startup errors in gedit. But now that I have an Internet connection maybe there is a way I can fix this mess and have gcc 3.4 and 4.0 installed properly?

I must say this is disappointing. It is SIGNIFICANTLY HARDER now to get a Lucent modem to work in Ubuntu. I really don't know how much harder this can get but I imagine I may have to figure out the internals of the Linux kernel and the source code for my Lucent modem driver in the future.

Edit: Yep Breezy is now busted. I can't even run apt-get!

```
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.4' not found (required by apt-get)
apt-get: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.4' not found (required by /usr/lib/libapt-pkg-libc6.3-6.so.3.10)
```

Synaptic doesn't work, OpenOffice.org doesn't work, gedit doesn't work etc...

```
** (gedit:9111): WARNING **: Error, unable to open module file '/usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.4' not found (required by /usr/lib/libaspell.so.15)'


** (gedit:9111): WARNING **: Error, impossible to activate plugin 'Spell checker'
```

---

### Post by preater on 2005-10-18
This is a real shame, and a bit embarrassing that you can't compile the Breezy kernel using the tools Breezy ships with.

[QUOTE=heimo]This should set gcc 3.4 as your compiler:
```
sudo apt-get install gcc-3.4
export CC=gcc-3.4

```[/QUOTE]

If it's any help, this does work.  I installed gcc-3.4, then followed the [Ubuntu 5.04 (Hoary) Lucent WinModem Setup](https://wiki.ubuntu.com/forum/hardware/lucent) guide mentioned earlier.  Set $CC to gcc-3.4 before you compile, and it's fine.

Andrew

---

### Post by blastus on 2005-10-18
[QUOTE=preater]This is a real shame, and a bit embarrassing that you can't compile the Breezy kernel using the tools Breezy ships with.

sudo apt-get install gcc-3.4
export CC=gcc-3.4

If it's any help, this does work.  I installed gcc-3.4, then followed the [Ubuntu 5.04 (Hoary) Lucent WinModem Setup](https://wiki.ubuntu.com/forum/hardware/lucent) guide mentioned earlier.  Set $CC to gcc-3.4 before you compile, and it's fine.

Andrew[/QUOTE]

But to connect to the Internet I have to compile the Lucent modem drivers, but to compile them I need to install gcc-3.4, but to install gcc-3.4 I need a connection to the Internet!!! :( 

```
sudo apt-get install gcc-3.4

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gcc-3.4
```

Anyway I had a brainstorm. Even though the process of compiling the drivers **DESTROYED MY BREEZY INSTALLATION!!! :mad: **, I salvaged the ltmodem.ko and ltserial.ko files from it. I just finished re-installing Breezy from stratch and followed my guide from Step 4 of 6 onwards using the *.ko files and it works. ;) 

Now since I have an Internet connection I believe I can do a "sudo apt-get install gcc-3.4." But the point is, is that, people who use a Lucent modem to connect to the Internet CANNOT install gcc-3.4 with apt-get!!! :( 

If someone would be so kind to make a guide with explicit instructions on how to install gcc-3.4 WITHOUT an Internet connection, it would really help out. I just might be able to do that now, maybe with "sudo apt-get install gcc-3.4" I can tell what packages are actually needed, then I can do a scan-packages (or whatever the command is) to create a local repository, and install gcc-3.4 on a fresh Breezy installation by adding that repository to apt.

---

### Post by breakthestate on 2005-10-19
what about after you compile the drivers.....

export CC=gcc-4.0 
And then  symlink /usr/bin/gcc (and possibly cc and cpp) back to 4.0?  

Then try apt-get and openoffice.org and see if they are broken.  If you set CC to 4.0 right after you compile the drivers for your lucent, I think your system might turn out to be just fine.

Also, I know I've run across a guide for how to keep your system up and running on Debian with two different compilers.  I think this may apply.  

Also, it seems that you could write a guide if a combo of the above things worked.  I think it would go like this:

- Download Breezy
- Get the .deb files for gcc-3.4 and cpp-3.4 from a computer with an internet connection.
- Install those debs (in the order in which you succeeded) 
- Set the CC variable and symlink /usr/bin/gcc to 3.4
- Compile the drivers as you have succeeded
- Reset the CC variable and symlinks (there may be other things to do here, such as cc and cpp symlinks, but I'm not sure)

I think that maybe you could be successful in writing a bullet-proof guide if you worked out some kinks for the above.  It seems your main problems are simply knowing exactly what to do once you get gcc 3.4 and how to not break the system with it.  

I'm not a developer and I would consider myself a linux noob, and I know it was probably a bad decision to not include 3.4 with breezy, but remember that you and I and everyone here is part of what makes Ubuntu work, and if you could make this guide, I think you could help hundreds and hundreds of people stick with Ubuntu.  So I suggest doing a fresh Breezy install and try out your techniques until you don't break your system.  Then...write a guide and help a bunch of people.  I believe you can do this.  It would be awesome.

---

### Post by heimo on 2005-10-19
[quote=blastus]I can't do that--no Internet connection. 
[/quote]

:oops: Sorry blastus, I was thoughtless there. It should be obvious to assume that you wouldn't be compiling modem drivers if you already had internet connection up and running. If I'm not mistaken, linmodem drivers are not included in Ubuntu, but also if I'm not (once again) mistaken, I believe the goal is to be able to compile everything that ships with Ubuntu using just the tools that ship with Ubuntu. Of course it would be nice to have out of the box support for these devices - I don't know the backgrounds, but is there some license issue? Anyway, I hope you guys get this solved. Best of luck.

Sincerely, blastus, sorry I couldn't help.

---

### Post by elfgoh on 2005-10-19
Hihi, would be fantastic if there's a guide on this. I'm experiencing similar problems, and the forums have popped up others in the same predicament.

I apologise for being unable to contribute much cos I'm a real noob. Juz one mth into linux =)

Btw, I'm wondering if a bug report has been filed? May I know where do I do that?  Do the developers know that this is a BIG porblem for many of us?

Tks

---

### Post by elfgoh on 2005-10-19
Hey can some1 wif net connection raise this issue at Technical Board meeting? I wun have a net connection to do that....

[https://wiki.ubuntu.com//TechnicalBoardAgenda](https://wiki.ubuntu.com//TechnicalBoardAgenda)

---

### Post by robertobech on 2005-10-19
Couldn't you share your compiled modules, so I can try them here too? I'm about to upgrade to Breezy, but I'm afraid all this talk of installing gcc and seeting things around will get me confused... If you could send the modules through e-mail, it's [email]robertobech@gmail.com[/email]. Thanks in advance...

---

### Post by blastus on 2005-10-19
Thank you breakthestate, heimo, and elfgoh for your kind and informative comments! 

I will try to put a guide together here for installing gcc-3.4 (if I can figure this out.) I've only been using Linux now for two months so my knowledge is extremely limited, but I guess I have to push learning this stuff sometime or another. I just have to get into the right mood and have a lot of time on my hands and put the pieces of the puzzle together.

Based on what I've learned, you don't need to export CC to install gcc-3.4 (but maybe if you don't you'll trash your system like I did I'm not sure.) Somehow the system knows to look for gcc-3.4 even though gcc-4.0 is installed and is the "default" compiler. Also, since Breezy was compiled with gcc-3.4.5 and I apparently installed gcc-3.4.4...this tells me that to compile kernel modules you perhaps only need to have a compiler that has the same MAJOR.MINOR version as the compiler that was used to compile the kernel.

We should also file a bug report about this gcc-3.4/gcc-4.0 issue and take a look at the Technical Board Agenda as elfgoh points out.

---

### Post by blastus on 2005-10-19
[QUOTE=robertobech]Couldn't you share your compiled modules, so I can try them here too? I'm about to upgrade to Breezy, but I'm afraid all this talk of installing gcc and seeting things around will get me confused... If you could send the modules through e-mail, it's [email]robertobech@gmail.com[/email]. Thanks in advance...[/QUOTE]

Edit: Here you go, I've attached them to this post.

---

### Post by odrop on 2005-10-20
Just to throw in my own experience with this, I had to basically go through the same thing as the original poster did to get my  slmodem drivers working with breezy.  The only thing that saved my eternal frustration and switching back to mandrake(well mandriva now) was these forums.  It's a shame this had to happen to such a good distro, maybe this is forgiveable in the long run.

But this isnt just a pain for modem drivers, anyone trying to compile custom kernel modules and maybe some other things are going to run into this fun little 'bug.'

---

### Post by elfgoh on 2005-10-20
Actually there's one temporary solution I've thot of: I juz dwnloaded an ubuntu Hoary livecd. Since I cld use my modem in Hoary, I'll probly be doing that till there's a proper solution in breezy. (Hopefully!) 

robertotech: I honestly think u shouldn't switch to Breezy yet, at least not until u r sure that a Breezy live cd can load ur modem... my 5c. 

Anyway, let's juz hope that the developers will fix this soon, and dun make the same mistake twice....

Btw, mine is a smartusb56 modem, juz in case any1 needs help wif that in Hoary.

---

### Post by robertobech on 2005-10-20
[QUOTE=elfgoh]robertotech: I honestly think u shouldn't switch to Breezy yet, at least not until u r sure that a Breezy live cd can load ur modem... my 5c. 
.[/QUOTE]
Thanks for your advice. Anyway, I've updated to breezy because my wife has a windows2000 installation, and I can access the internet through our home network...

---

### Post by robertobech on 2005-10-20
[QUOTE=blastus]Edit: Here you go, I've attached them to this post.[/QUOTE]

Thanks! I'm gonna try it tonight!

---

### Post by blastus on 2005-10-21
OK, here it is as promised. ;) 

[HOWTO: Install gcc-3.4 via apt-get without an Internet connection](http://www.ubuntuforums.org/showthread.php?t=79896)

---

### Post by lreyes6 on 2005-10-22
Just like a suggestion... if u have acces to an internet cafe or something u can download the packages from here [http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/) and then install them on your ubuntu...

saludos:cool:

---

### Post by breakthestate on 2005-10-22
blastus, 

awesome.

---

### Post by blastus on 2005-10-22
[QUOTE=breakthestate]blastus, 

awesome.[/QUOTE]

Thanks breakthestate! I hope this works for you. Seems like one doesn't need to export CC...when you compile kernel modules, the system seems to know that it needs gcc-3.4 and will use it if it is installed. gcc -dumpversion returns 4.0.2 but yet I was able to compile my kernel modules. I'm not sure this will work for everyone though but it worked for my Lucent modem.

---

### Post by StefanoCole on 2005-10-25
Hello, I also had the problem of compiling the Lucent modem drivers.
So I took the compiled modules that have been posted by Blastus in this thread (file breezy-lucent-modem.tar.bz2). Then, I followed the Howto present on the Wiki about Lucent win modems for the other steps and I managed to connect to internet! 

Thank Blastus so much for posting the compiled modules :KS 

Bye, Stefano

---

### Post by blastus on 2005-10-26
I'm glad these modules are working. ;) You might want to recompile them on your machine though. Once connected, if you "sudo apt-get install gcc-3.4", you should be able to compile them. Alternatively, you can [install gcc-3.4 via apt-get without an Internet connection](http://www.ubuntuforums.org/showthread.php?t=79896) and compile them.

---

### Post by nevelis on 2006-05-08
Have you seen [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/Ubuntu/]("http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/Ubuntu/") ?  There's a .deb file there for the default Breezy kernel.

If you're using a different kernel, let me know and I'll build you a .deb

Cheers,
Aaron

---

