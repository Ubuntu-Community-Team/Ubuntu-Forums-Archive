---
title: "&quot;cannot execute binary file&quot;"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by flylehe on 2009-03-06
Hi,
Lately I am trying to install a higher version of emacs under my $
{HOME} on my office server. I add the new emacs path "${HOME}/emacs/bin" into PATH. The new emacs can be invoked quite well when I ssh to the server, but encounters this "${HOME}/emacs/bin/emacs: cannot execute binary file" error when I am working on my office computer that loads my ${HOME} as part of its disk. How can I make it work? Really appreciate your help! 

My laptop that I use to ssh to my server is 32bit ubuntu, and the
server is x86-64 and what I see from my office computer is CentOS that uses gnome.

Besides emacs, I also installed higher versions of bash and gnuplot
under my HOME than the ones under bin, and they all work whether I am
working on my office computer or ssh to my office server from my
laptop.

Thanks!

---

### Post by taurus on 2009-03-06
What's the output of this command from a terminal?

```
file ~/emacs/bin/emacs
```

---

### Post by flylehe on 2009-03-06
It's
./emacs: sticky ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), not stripped

---

### Post by taurus on 2009-03-06
```
ls -la ~/emacs/bin
ldd ~/emacs/bin/emacs
```

---

### Post by flylehe on 2009-03-06
Output to ls -la:
> 
drwxr-xr-x   2 lehe lehe     4096 Mar  4 22:49 .
drwxr-xr-x  23 lehe lehe     4096 Mar  4 22:49 ..
-rwxr-xr-x   1 lehe lehe    18865 Mar  4 22:49 b2m
-rwxr-xr-x   1 lehe lehe   276326 Mar  4 22:49 ctags
-rwxr-xr-x   1 lehe lehe   103507 Mar  4 22:49 ebrowse
-rwxr-xr-t   2 lehe lehe 13700263 Mar  4 22:49 emacs
-rwxr-xr-t   2 lehe lehe 13700263 Mar  4 22:49 emacs-22.3
-rwxr-xr-x   1 lehe lehe    36418 Mar  4 22:49 emacsclient
-rwxr-xr-x   1 lehe lehe   273774 Mar  4 22:49 etags
-rwxr-xr-x   1 lehe lehe     7365 Mar  4 22:49 grep-changelog
-rwxr-xr-x   1 lehe lehe     4067 Mar  4 22:49 rcs-checkin

output to ldd ./emacs:
> 
	libXaw3d.so.7 => /usr/X11R6/lib64/libXaw3d.so.7 (0x0000003092c00000)
	libXmu.so.6 => /usr/X11R6/lib64/libXmu.so.6 (0x0000003092800000)
	libXt.so.6 => /usr/X11R6/lib64/libXt.so.6 (0x0000003095200000)
	libSM.so.6 => /usr/X11R6/lib64/libSM.so.6 (0x0000003090200000)
	libICE.so.6 => /usr/X11R6/lib64/libICE.so.6 (0x0000003090000000)
	libXext.so.6 => /usr/X11R6/lib64/libXext.so.6 (0x000000308fe00000)
	libtiff.so.3 => /usr/lib64/libtiff.so.3 (0x0000003097700000)
	libjpeg.so.62 => /usr/lib64/libjpeg.so.62 (0x0000003091800000)
	libpng12.so.0 => /usr/lib64/libpng12.so.0 (0x0000003093300000)
	libz.so.1 => /usr/lib64/libz.so.1 (0x000000308f800000)
	libm.so.6 => /lib64/tls/libm.so.6 (0x000000308f400000)
	libungif.so.4 => /usr/lib64/libungif.so.4 (0x0000003091600000)
	libXpm.so.4 => /usr/X11R6/lib64/libXpm.so.4 (0x0000003094c00000)
	libX11.so.6 => /usr/X11R6/lib64/libX11.so.6 (0x000000308fa00000)
	libasound.so.2 => /lib64/libasound.so.2 (0x0000003095e00000)
	libdl.so.2 => /lib64/libdl.so.2 (0x000000308f600000)
	libpthread.so.0 => /lib64/tls/libpthread.so.0 (0x000000308fc00000)
	libncurses.so.5 => /usr/lib64/libncurses.so.5 (0x0000002a9558f000)
	libc.so.6 => /lib64/tls/libc.so.6 (0x000000308f100000)
	/lib64/ld-linux-x86-64.so.2 (0x000000308ef00000)


---

### Post by geirha on 2009-03-06
I wonder why it has the sticky bit ... it has no effect on linux. Try removing it.
```
chmod -t ~/emacs/bin/emacs
```

---

### Post by flylehe on 2009-03-06
Did what you suggested. Now it has no sticky bits, and still doesn't work...
Is it harmful to remove sticky bits from my new emacs?

---

### Post by Bölvaður on 2009-03-06
I would suspect that the emacs version is made for 64 bit operating systems, which you said you did not have.


this is me trying to open 64 and 32 bit version on a 32 bit os
```

$ file warsow.**x86_64 **
warsow.x86_64: ELF **64-bit** LSB executable,** x86-64**, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), not stripped

$ file warsow.**i386 **
warsow.i386: ELF** 32-bit** LSB executable, **Intel 80386**, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), not stripped
```

Your output looks more like the 64 than 32 in my opinion. So perhaps you should go hunt down 32 bit version

---

### Post by flylehe on 2009-03-06
Actually I did intend to install a higher version of emacs on my office server which is x86-64 than its own emacs. So 64bit emacs is the correct choice for my office server. Or am I understanding your post wrong?

BTW: I have no root access to my server, so I can only install it under my $HOME.

---

### Post by taurus on 2009-03-06
> **Bölvaður said:**
> I would suspect that the emacs version is made for 64 bit operating systems, which you said you did not have.


this is me trying to open 64 and 32 bit version on a 32 bit os
```

$ file warsow.**x86_64 **
warsow.x86_64: ELF **64-bit** LSB executable,** x86-64**, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), not stripped

$ file warsow.**i386 **
warsow.i386: ELF** 32-bit** LSB executable, **Intel 80386**, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), not stripped
```

Your output looks more like the 64 than 32 in my opinion. So perhaps you should go hunt down 32 bit version

I thought he said that his laptop is running Ubuntu is 32bit but his server in his office that runs CentOS is 64bit.  He installed emacs on his server/CentOS.

---

### Post by geirha on 2009-03-06
> **flylehe said:**
> Did what you suggested. Now it has no sticky bits, and still doesn't work...
Is it harmful to remove sticky bits from my new emacs?

The sticky bit on files is simply ignored in linux, so whether it's on or off doesn't matter. It was just a long shot that maybe it had something to do with you not beeing able to execute it. On other *nix systems the sticky bit may have an effect.

Does the file command on other executables produce similar output to that of your emacs?
```
file /bin/bash
```

---

### Post by flylehe on 2009-03-06
Looks quite same except not stripped

/bin/bash: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), stripped

./emacs: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), not stripped

BTW:
I am talking about my server which is X86-64, which I think is Unix not linux. So the sticky bytes might have effect...?

---

### Post by Bölvaður on 2009-03-06
> **taurus said:**
> I thought he said that his laptop is running Ubuntu is 32bit but his server in his office that runs CentOS is 64bit.  He installed emacs on his server/CentOS.

yes this is a great fail :( I began to think about him accessing emacs on the laptop so it translated into me thinking he's trying to use emacs on x86 :-\"

---

### Post by geirha on 2009-03-06
> **flylehe said:**
> Looks quite same except not stripped

/bin/bash: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), stripped

./emacs: ELF 64-bit LSB executable, AMD x86-64, version 1 (SYSV), for GNU/Linux 2.4.0, dynamically linked (uses shared libs), not stripped

BTW:
I am talking about my server which is X86-64, which I think is Unix not linux. So the sticky bytes might have effect...?

Ah, I obviously haven't read the posts here properly. Your home folder is on a 64-bit linux system, and it is mounted on your office computer (via NFS probably), which is running CentOS? ... I'm guessing your office computer is not 64-bit then. What does ```
uname -a
``` say on both the server and your office computer?

CentOS is linux too btw.

---

### Post by flylehe on 2009-03-06
Thanks! I think you are right! 
My laptop:
> Linux 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
My office computer is:
> Linux 2.6.9-78.0.13.ELsmp #1 SMP Wed Jan 14 16:12:46 EST 2009 i686 i686 i386 GNU/Linux
My office server is:
> Linux 2.6.9-78.0.8.ELsmp #1 SMP Wed Nov 19 19:42:38 EST 2008 x86_64 x86_64 x86_64 GNU/Linux
An off-topic question: does "i686 i686 i386" mean my office computer has three linux kernels?

I built my new emacs by ssh from my laptop to my server which has a 64-bit OS, then my new emacs must be 64-bit specific; now I am trying to use my new emacs on my office computer with 32-bit OS and a 64-bit application is unlikely to run on a 32-bit OS, which cause my original problem. So I think I have to build my new emacs on my office computer? Is that 32-bit specific emacs executable usable on my 64-bit-OS office server? Are 32-bit executables always able to run on 64-bit OS? If no, then I have to install two versions of emacs on my server and on my office computer?

Another related question:

I was also wondering if it is possible to build my own soure code on my laptop (32-bit OS), and copy the executable to my office computer (32-bit OS) and my office server to run? Note that the OS's of the three machines are different, my laptop is Ubuntu 32-bit 8.10, my office computer is 32-bit CentOS, and my office server is 64-bit (? I don't know the OS). Maybe this is not correct. Instead should I only exchange SOURCE code between my laptop, my office computer and my office server, and only run the EXECUTABLE that is built from the source on the same machine?

---

### Post by geirha on 2009-03-06
```
lshw -class cpu
# or
cat /proc/cpuinfo
``` should show whether you have 64-bit or 32-bit cpu. uname prints what the OS treats the cpu as. On the computer I'm on now, I have a 64-bit CPU with a 32-bit OS, and uname -m shows 
```
$ uname -m
i686
```
If I had 64-bit OS on this computer, it would've shown x86-64. 

It's perfectly fine for you to put executables built on 32-bit CentOS on the 64-bit server. It will run when you run it from your CentOS computer, but not on the server. As long as you manage to keep track on which executables execute on which computer, you'll be fine. Maybe name the executables emacs64 and emacs32?

---

### Post by flylehe on 2009-03-06
Thanks! 

Did you mean generally it is incorrect to run on a 64-bit linux an executable built on a 32-bit linux? The reverse is obviously impossible I know.

How about between Centos and Ubuntu or between Ubuntu different versions? Between linux and Unix? 

Does this portability have something to do with if CPU is 64-bit or 32-bit , or only depends on if OS is 64-bit or 32-bit (only considering linux and Unix of course)? 

These questions are some basics that I have been uncleared about for quite a while.
Thanks!

Update:
I just install my new emacs on my office computer, and it can be run both on my office computer and by ssh to my office server. I realized all the previous packages I installed on my office computer could all be run on my office server by ssh to it. Does that mean executable generated on 32-bit OS can always run on 64-bit OS?

---

### Post by geirha on 2009-03-06
> **flylehe said:**
> Thanks! Did you mean generally it is incorrect to run on a 64-bit linux an executable built on a 32-bit linux? How about between Centos and Ubuntu or between Ubuntu different versions? Between linux and Unix? Does this portability have something to do with if CPU is 64-bit or 32-bit , or only depends on if OS is 64-bit or 32-bit?
Thanks!

You can run a 32-bit executable on a 64-bit OS, but the shared libraries (that the 32-bit executable needs) must also be 32-bit, so it's quite a hassle as you'll need to install a second set of libraries.

Executing binaries between CentOS and Ubuntu and other Ubuntu releases of the same bitness, is also possible, as long as the needed libraries are available. It may be the libraries are too old on one system, in which case you'll need to install newer versions of the libraries on that system in order to be able to run it.

So, in general, it's best to compile the binary on the system its supposed to run on. Will give you less problems.

When it comes to different OSes, like between linux and BSD, they use a different binary format. BSD has added support for running linux binaries, but you can't run BSD binaries in linux afaik.

---

### Post by flylehe on 2009-03-06
Your post is quite helpful!

I think if built with static linking, the executable will be portable from 32-bit to 64-bit or between different computers without the hassle caused by dynamic-linking libraries?

Amazingly the packages I installed from source on my office computer, like emacs, bash, bashdb and gnuplot,  could all be run on my office server by ssh to it. Since my office computer loads my $HOME on my office server as its hard disk, the portability is probably because my server already has two versions of those dynamic-link libraries: one for 32-bit and one for 64-bit?

---

### Post by geirha on 2009-03-06
Yes, staticly linking the 32-bit libraries should make it run without problems.

And, yes, your server probably has 32-bit libraries as well then. You can see what shared libraries a binary uses with the ldd command.
```
ldd filename
```

---

### Post by flylehe on 2009-03-06
Yes, I did dig into that on both my office computer and the server.
For example, for the newly-installed emacs, there is one more .so file for the server than for my computer, which is linux-gate.so.1, the rest 20 .so files are the same but with different addresses for server and my computer (I assume those numbers at the end of each line for each .so file are addresses), e.g.on the server:
> 
libSM.so.6 => /usr/X11R6/lib/libSM.so.6 (0x00d26000)

and on my computer:
> 
libSM.so.6 => /usr/X11R6/lib/libSM.so.6 (0x00a46000)

Looks like these .so files each have two parts: one for 32-bit and one for 64-bit. 
It seems I almost couldn't stop querying these things, probably still in the over-enthusiastic phase of starting using linux.

---

