---
title: "How to compile a software from its source ..."
date: 2011-02-04
forum: New to Ubuntu
---

### Post by Linyx on 2011-02-04
[SIZE=2]I have downloaded a Software name Avidemux as a source code, now i want to compile it and[/SIZE] [SIZE=2]make it run....so i cd to that directory and typed "./configure[/SIZE]" [SIZE=2],but it showing me the message[/SIZE]..
> "[SIZE=2]bash: ./configure: No such file or directory"[/SIZE], [SIZE=2]Then i tried to compile it by the command "make" but its shows me an error message 
[/SIZE]> "[SIZE=2]make: *** No targets specified and no makefile found.  Stop.[/SIZE]"But now thats not a problem, i get that from my repository easily...

[SIZE=2]But, if i get the source-code of a certain software, How can i install that software..?
I means compilation is same for all softwares...? as far as i know, These three steps are necessary for configuring,Building & copying the build(binary-file) to usr/local/bin directory:-[/SIZE]
```
$cd source-direc 
$./configure
$make
$make install
```

---

### Post by Wtower on 2011-02-04
It depends on the source. I hope the following link helps:

[http://everydaylht.com/howtos/system-administration/compiling-software-from-source-code/](http://everydaylht.com/howtos/system-administration/compiling-software-from-source-code/)

---

### Post by vivek.pandey on 2011-02-04
first of all you need to make sure that the folders of the software are in your home directory or else change your directory to the that directory.for example you downloaded the software in tar or any other compressed form.
extract its content in the home directory.see that if you are running config then its present in home
or the better option is you can change the directory
for example 
vivek@neo:`$cd src
vivek@neo:~/src$./configure
vivek@neo:~/src$make
etc
etc hope this will help....can ask more if problem is not solved):P):P):P):P):P

---

### Post by Elfy on 2011-02-04
from [http://www.avidemux.org/admWiki/doku.php?id=build:install_2.5](http://www.avidemux.org/admWiki/doku.php?id=build:install_2.5)

cmake  *path to source dir*
make
make install

I assume you know it's available from the repos.

---

### Post by ebasa on 2011-02-04
Any reason you don't just use the one in the repositories?

---

### Post by Paqman on 2011-02-04
> **ebasa said:**
> Any reason you don't just use the one in the repositories?

This.

Getting your software from the repos is not only easier, it's better for the security and stability of your system.

---

### Post by vivek.pandey on 2011-02-04
> **ebasa said:**
> Any reason you don't just use the one in the repositories?

there are some ubuntu softwares you cannot find in your repositories...eg john the ripper

---

### Post by Paqman on 2011-02-04
> **neo_aryan said:**
> there are some ubuntu softwares you cannot find in your repositories...eg john the ripper

Actually, [that is in the repos]("http://packages.ubuntu.com/maverick/john"). 

The point being: for packages like Avidemux and John the Ripper where you can get them from the repos, that's the best way to go in almost every case.

Even for software that isn't in the repos, compiling from source should be a last resort, used only where there's no .deb package or PPA available.

---

### Post by Linyx on 2011-02-04
Thanks for all Replies, But the post objective was to find the way to compile the source code....However, now now i understood that compiling software can be different for different Sources.....

[SIZE=1][COLOR=Black]**@**[/COLOR][/SIZE]forestpiskie:-

I have did that earlier, but it was giving the error message at 1st Code, i-e **cmake, **Sorry i forgot that error message....

---

### Post by oldos2er on 2011-02-04
[http://www.avidemux.org/admWiki/doku.php?id=build:compiling_avidemux](http://www.avidemux.org/admWiki/doku.php?id=build:compiling_avidemux)

---

### Post by Linyx on 2011-02-04
Ok, so i have tried these commands,

The Output of "cmake ." is:-

```
#####################################
Configure Started
#####################################

-- Source dir is /home/assassin/Downloads/avidemux_2.5.4

Please do an out-of-tree build:
rm CMakeCache.txt; mkdir build; cd build; cmake ..; make
CMake Error at CMakeLists.txt:28 (MESSAGE):
  in-tree-build detected


-- Configuring incomplete, errors occurred!

```

---

### Post by oldos2er on 2011-02-04
Have you tried running the commands it's telling you to run?

---

### Post by Linyx on 2011-02-05
> **oldos2er said:**
> Have you tried running the commands it's telling you to run?

Yes...I have tried that ....but after that...in vain....

> CMake Error at cmake/admFFmpegBuild.cmake:135 (message):
  Yasm was not found.
Call Stack (most recent call first):
  avidemux/CMakeLists.txt:189 (include)


-- Configuring incomplete, errors occurred!


---

### Post by oldos2er on 2011-02-05
> Yasm was not found.

```
sudo apt-get install yasm
``` and retry *cmake ..*

---

### Post by Linyx on 2011-02-06
> **oldos2er said:**
> ```
sudo apt-get install yasm
``` and retry *cmake ..*

Ok, so i Now i get this error..

```
#####################################
Configure Started
#####################################

-- Source dir is /home/assassin/Downloads/avidemux_2.5.4

-- Checking GCC support
-- ********************
-- Check if GCC is Unix - Yes
-- Check if GCC is x86 64-bit - Yes
-- Check if GCC is MMX2 capable - Yes
-- Check if GCC is SSSE3 capable - Yes

-- Checking for pkg-config
-- ***********************
-- Found pkg-config

-- Checking for Libxml2
-- ********************
-- checking for module 'libxml-2.0'
--   package 'libxml-2.0' not found
Could not find Libxml2

-- Checking for pthreads
-- *********************
-- Found pthreads

-- Checking for zlib
-- *****************
-- Found zlib

--[B] Checking for GTK+
-- *****************
-- checking for module 'gtk+-2.0'
--   package 'gtk+-2.0' not found
Could not find GTK+

-- Checking for GThread[/B] [B]
-- ********************
-- checking for module 'gthread-2.0'
--   package 'gthread-2.0' not found
Could not find GThread
-- Could not find GThread[/B]

-- [B]Checking for Qt 4
-- *****************
Could not find Qt 4

-- Checking for gettext[/B] [B]
-- ********************
Could not find Gettext
-- libintl not required for gettext support[/B]

-- Checking for OpenGL
-- *******************
-- OpenGL is only available for Qt 4.6 or later

-- [B]Checking for SDL
-- ****************
Could not find SDL

-- Checking for XVideo[/B] [B]
-- *******************
Could not find XVideo
[/B] 
-- Checking for SpiderMonkey
-- *************************
Skipping check and using bundled version.

-- [B]Checking for Vpx
-- *****************
Could not find Vpx
[/B] 
-- ADM_coreConfig.h generated
-- CLI config.h generated
-- GTK config.h generated
-- Qt4 config.h generated


-- Configuring FFmpeg
patching file config.mak
Hunk #1 succeeded at 60 with fuzz 2.

*********************
***    SUMMARY    ***
*********************
   [B]GTK+        No
   Qt 4        No[/B]
*** Miscellaneous ***
   gettext     Yes
[B]   OpenGL      No
   SDL         No
   XVideo      No[/B]
*********************
*** Release Build ***
*********************

-- avsfilter binary uncompressed
/bin/tar: Record size = 8 blocks
avsload.exe
pipe_source.dll
CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
LIBXML2_INCLUDE_DIR (ADVANCED)
   used as include directory in directory /home/assassin/Downloads/avidemux_2.5.4/avidemux/ADM_userInterfaces/ADM_commonUI
LIBXML2_LIBRARIES (ADVANCED)
    linked by target "avidemux2_cli" in directory /home/assassin/Downloads/avidemux_2.5.4/avidemux

-- Configuring incomplete, errors occurred!

```I have bold the missing dependency for the software...Should i have to install it One-by-One...?

---

### Post by oldos2er on 2011-02-06
If you read the link I gave you in post #10, you'll find a list of dependencies to install.

---

### Post by Linyx on 2011-02-09
> **oldos2er said:**
> If you read the link I gave you in post #10, you'll find a list of dependencies to install.

Thanks 4 Support....

---

