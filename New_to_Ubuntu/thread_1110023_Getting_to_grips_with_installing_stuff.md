---
title: "Getting to grips with installing stuff"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Duffking on 2009-03-29
Hi all. I've installed Ubuntu 8.04 LTS today, and I'm completely new to Linux. I've been playing around with some stuff, and I've decided to try installing a program I have in windows, it's a source port of 'Descent'.

Thing is, I've no idea what I'm doing. I've been googling etc, but can't figure out what I'm doing, still. Here's the readme text:

```
This file describes how to compile D2X-Rebirth from Source.





Requirements



   1.

      C/C++ compiler (gcc/g++)

   2.

      SCons

   3.

      SDL(-devel)

   4.

      PhysFS(-devel)

   5.

      GLU/GL

   6.

      NASM (optional for Assembler-based Texture-mapper in non-OpenGL Build)





Compiling



For Mac OS X, an Xcode project is available (requires Xcode 2.1 or later). Xcode includes the compiler and OpenGL. For Mac OS 9, an MPW Makefile is available. MPW includes the compiler. For the sources to compile, they will need to be made into text files using a typecode changing program, if they were downloaded outside of Mac OS 9 (including Mac OS X). This will also need to be done after any Terminal command (diff, svn update etc) edits the source files.



The SConstruct file provides various options to compile this program.

To get a full list of all available commands, type scons -h within the Source directory.



Currently, the following variables are supported:



'sharepath=DIR'   (non-Mac OS *NIX only) use DIR for shared game data. (default: /usr/local/share/games/d2x-rebirth)

'sdl_only=1'      don't include OpenGL, use SDL-only instead

'sdlmixer=1'      use SDL_Mixer for sound (includes external music support)

'asm=1'           use ASSEMBLER code (only with sdl_only=1, requires NASM and x86)

'debug=1'         build DEBUG binary which includes asserts, debugging output, cheats and more output

'profiler=1'      do profiler build

'editor=1'        build editor !EXPERIMENTAL!

'arm=1'           compile for ARM architecture



&#8216;editor&#8217; is currently *not* supported and will not work.



To compile the source, type:



scons





If you wish to add additional commands, just add them to the scons command.

Example:



scons sdl_only=1 asm=1





To install the compiled binary to your system (/usr/local/bin/), type (as root):



scons install



You can also add the &#8216;install&#8217; command while compile-time. SCons will compile and install the binary right after that.



For Windows and Mac however, it is instead recommended to manually drag the program to the folder containing the Descent data instead of using the install command, or use the -hogdir option when running.



To clean up the source directory after installation, type:



scons -c
```

I've checked the Synaptic Package Manager for... stuff and couldn't find all the stuff listed so I don't know what I need.~

Here's a download link for the files concerned:

[http://www.dxx-rebirth.com/?Downloads:DXX-Rebirth](http://www.dxx-rebirth.com/?Downloads:DXX-Rebirth)

Seriously, no idea what I'm doing. Also assuming anyone can help, will this appear on the main menu after install, or will I be forced to use the terminal to run it? Seems a bit pointless having the nice looking interface if I can't use it. I like pretty things. I don't even know how to install/check if the programs listed at the top are installed, after hours of googling.

---

### Post by Moop on 2009-03-29
I get a 404 error on your link. To compile anything you will need the build-essentials package installed from Synaptic. 

Does this help? [http://ubuntuforums.org/showthread.php?t=1062353](http://ubuntuforums.org/showthread.php?t=1062353)

---

### Post by Duffking on 2009-03-29
> **Moop said:**
> I get a 404 error on your link. To compile anything you will need the build-essentials package installed from Synaptic. 

Does this help? [http://ubuntuforums.org/showthread.php?t=1062353](http://ubuntuforums.org/showthread.php?t=1062353)
I think that link is talking about installing the third in the series (Descent 3) from a disk. The file I tried to link to are source ports of Descent 1/2 respectively, which need to be installed from the source, the idea being that I then take the game files from the original windows install and put them in the linux directory once the port is installed to linux. The text in quotes is taken from the readme. Unfortunately, I don't have a clue what I'm doing.

The link broke because of the smiley, the port's homepage is here, simply click 'downloads'.

[http://www.dxx-rebirth.com/](http://www.dxx-rebirth.com/)

Thanks for replying.

---

### Post by egalvan on 2009-03-29
I went to the web site, and discovered that it is about Descent,
one of my most favorite games!

I will definitlye be downloading everything,
and compiling, making and running...

gotto go dig out my Descent & Descent II out of the closet...

By the way, if you enjoy this work, don't forget to toss the writes a bone...

I'll be donating $10 if it works on my game machine... :)

Thanks for the link to memories...

ErnestG

---

### Post by Duffking on 2009-03-29
Agh, how can installing stuff be so difficult :( Every single guide/thing I look at just seems completely impenetrable. I was looking at one guide earlier and it said 'In a terminal window move to the "duke3d" folder and type make.'

Eh?

From here, btw:

[http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux](http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux)

Seriously, I wish I had some idea what I was doing. Either with this or descent.

---

### Post by Duffking on 2009-03-29
Sorry to double post, but I've been trying other programs. One has gone pretty well up until this point:

> On *NIX run "make" and then "su -c 'make install'" or
   "sudo 'make install'" depending on you *NIX distribution.
   This will compile everything and install the executable (doomsday),
   the libraries (games, renderer, sound), data files and definitions
   files under the directory specified by the configured prefix.

I've tried both these, the first asks for a password, then says 'Authentication Failure', the second says the command doesn't exist?

---

