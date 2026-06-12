---
title: "Installing earlier version of gcc"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by newport_j on 2009-08-26
I want to install gcc version 3.2 onto my Linux desktop. It has now gcc 4.2 which I do not want to interfere with. What is the command to install gcc version 3.2 onto my desktop computer. If I just use apt-get install gcc that will only put the latest version on my computer. I already have that so please give me one to install gcc version 3.2 on my desktop.


newport_j

---

### Post by Bachstelze on 2009-08-26
Do you really need 3.2, not just any version of gcc from the 3.x series? You can install gcc 3.4 with

```
sudo apt-get install gcc-3.4
```

If you really need 3.2, you'll have to compile it from source.

---

### Post by newport_j on 2009-08-26
I think that I can get by with gcc 3.4 ,that would work. But I must tell my application where to find 3.4.I am using 4.2 now and that will not work with ccured/cil else why would I go back to a previous application. So if I use 3.4 I must tell my application during ./configure where to find gcc 3.4. How do I do that.

./configure CC=foo

will the above command do it?

newport_j

---

### Post by Bachstelze on 2009-08-26
Yes, though of course you would need to replace foo with the command for gcc 3.4:

./configure CC=gcc-3.4

---

### Post by newport_j on 2009-08-26
Do we not need a path here? it is not enough to just tell it what compiler to use (I assume it would use the latest compiler on the system if no compiler was specifically cited to use).

But if I install gcc 3.4 where does it go? I already have 4.2 installed (it came with Ubuntu 8.04 LTS). So if I install 3.4 or for that matter any other gcc version where does it go?.

My latest and greatest compiler (gcc 4.2) is in /usr/bin/. I cannot put gcc 3.4 in the same place  without damaging both. In addition I must know this path for 3.4 in order to get the command CC=foo correct. CC=foo must tell you where the compiler as well as telling you the compiler to use.

Newport_j

---

### Post by Bachstelze on 2009-08-26
> **newport_j said:**
> But if I install gcc 3.4 where does it go? I already have 4.2 installed (it came with Ubuntu 8.04 LTS). So if I install 3.4 or for that matter any other gcc version where does it go?

GCC 4.2 is at /usr/bin/gcc-4.2 and /usr/bin/gcc is a symlink to it. GCC 3.4 is at /usr/bin/gcc-3.4. Since /usr/bin is in your PATH, you don't need to specify the absolute path to it.

---

### Post by newport_j on 2009-08-26
I have at /usr/bin/ gcc only and it is a executable - not a directory. So I want to install say gcc 2.95.3 on the same PC, but not interfere with gcc 4.2 which is there already. Then I want to tell my application where to find the gcc 2.95.3. I will do this usually during the configure stage with CC=foo. So I must do two things:

1. install gcc-2.95.3 and not interfere with .the current gcc 4.2.
2 tell the application during ./configure where to find the older compiler.  The application will not work with gcc 4.2 which is why I started this in the first place. Do you think I would go through this if I did not have to?

The question is how do I do it? Where does the second compoiler go? It must not interfere with the first compiler but it must be known to the application that requires it for that app to work..


newport_j

---

### Post by Bachstelze on 2009-08-26
> **newport_j said:**
> I have at /usr/bin/ gcc only and it is a executable - not a directory.

Who said it was a directory? And if you have only /usr/bin/gcc, that's not normal. Which version of Ubuntu are you running?

---

### Post by mc4man on 2009-08-26
> I cannot put gcc 3.4 in the same place without damaging both.
Out of curiosity do you have some info to back that up. I have several gcc (& g++, cpp) versions installed and never have had an issue.

There are gcc, g++ and cpp links that point to the default system versions, the rest just sit there doing nothing unless specified by a CC, CXX or CPP flag.

(even installed your 2.95 which I'll never use and plan to dump now

> $ CC=gcc-2.95 ./configure
...............
checking for gcc... gcc-2.95
checking if gcc-2.95 static flag  works... yes
checking if gcc-2.95 supports -fno-rtti -fno-exceptions... yes
checking for gcc-2.95 option to produce PIC... -fPIC
checking if gcc-2.95 PIC flag -fPIC works... yes
checking if gcc-2.95 supports -c -o file.o... yes


---

### Post by newport_j on 2009-08-26
I do not know if /usr/bin/gcc is abnormal. I do know that gcc is a executable file - it is green. It is not a directory. Of course, /usr/bin/ is a directory. 
 
I just want to have gcc 4.2 already installed and then add gcc 2.95.3 which I want to install. I would not do this unless the install instructions for ccured and CIL said to. The software cannot be reliable if using gcc 4.2. The two software program will not compile with gcc 4.2. The include files are too current. the gcc 2.95.3 with its older include files will compile ccured and CIL.
 
I just want gcc 2.95.3 installed and used for those two programs (ccured and CIL). I am new to Linux. It seems they have a certain place for the gcc compiler. Add a second gcc compiler and that becomes your current and only compiler (if it is not destroyed during install). It seems there is only one place the compiler goes.
 
Where can I put this second compiler and not destroy my first and latest gcc compiler. As I said, I only have a special use for it. They are research progams so it seems the are not kept up to date. Graduate students do not have that kind of time.
 
If I want to use them (and I do). Then I must install and older version of gcc and I do not want to destroy the current version.
 
 
respectfully,
 
newport_j

---

### Post by mc4man on 2009-08-27
You can just install an **earlie**r gcc version from synaptic, it will not 'replace' your system default.
Package wise 2.95 will not be available, though still available from the dapper repo (2 packages required

From the cil 1.37 hmtl
> we have tested CIL on the following compilers:

    * On Windows, cl compiler version 12.00.8168 (MSVC 6), 13.00.9466 (MSVC .Net), and 13.10.3077 (MSVC .Net 2003). Run cl with no arguments to get the compiler version.
    * On Windows, using cygwin and gcc version 2.95.3, 3.0, 3.2, 3.3, and 3.4.
    * On Linux, using gcc version 2.95.3, 3.0, 3.2, 3.3, 4.0, and 4.1. 

I'll attach a build log from compiling on gcc-4.2, maybe you'll find it useful to compare or spot issues (on another 8.04 -i386 install, will edit in

glancing thru reminded me I had multilib support enabled, whether an issue here don't know

Best way to view log (had to make a .gz due to text file limits) is right click on the attachment -> 'save link as', and then extract after dl'ing

---

