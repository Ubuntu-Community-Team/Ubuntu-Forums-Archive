---
title: "I need help wolf4sdl-1.6"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by Shadowdoom on 2011-02-13
I'm trying to play wolfenstein 3d on ubuntu 10.04 with wolf4sdl-1.6 and did this:

[LIST]
[*]cd /home/user/Downloads/wolf4sdl-1.6/
[*]make
[/LIST]

But I got this:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make: *** [id_ca.o] Error 1

What should I do?

---

### Post by spikoley on 2011-02-13
Post the README file or install directions.

---

### Post by Shadowdoom on 2011-02-14
Here is the readme from wolf4sdl-1.6

---

### Post by spikoley on 2011-02-15
> **Shadowdoom said:**
> Here is the readme from wolf4sdl-1.6

Is there another file with directions on how to install it?

---

### Post by lisati on 2011-02-15
It is common to do a ./configure before a make. Have you done that yet?

---

### Post by Shadowdoom on 2011-02-15
There's no configure file.
Here is another readme file that comes with wolf4sdl-1.6

---

### Post by kiddykoff on 2011-10-16
newest version is now 1.7

I'm trying to take my wolfenstein purchase from steam work in linux. (maybe even better)

here is the readme file

and once again, there is no configure file.

the website can be found [here]("http://www.chaos-software.de.vu/").

---

### Post by andlinux on 2011-10-27
Is it working for you ?

---

### Post by kiddykoff on 2011-10-28
this isn't really simple for me to try out. and i haven't had the time to try it out.

---

### Post by andlinux on 2011-10-28
I compiled it but then i get a message that it can't find the data files.
I copied my wolf3d datafiles in the same map but i have no idea what i have to do with the version.h file. If i open that file then i see all the versions but i have no idea how i can select one.

---

### Post by a-hole on 2012-07-09
What a pain in the ***...

I had a wild hair, and decided to pull out my old copies of *Wolfenstein 3-D* and *Spear of Destiny*, and was rather surprised to find the information to be terrible in all respects.

Perseverance, however, tends to pay off, but I feel as though I owe it to the community to help out (since I've so many times been helped out, you know). Here are my findings for installing and playing these games in Ubuntu (Mint 11, AMD64):

First, go here: [http://www.chaos-software.de.vu/downloads.html](http://www.chaos-software.de.vu/downloads.html)

and download the source code for Wolf4SDL.

Then, extract the zipped archive, and open "version.h" in a text editor. Locate the lines which begin with "#define SPEAR", and the comments following it (beginning with "Wolf3d Full v1.1 [. . .]"). Whichever version of Wolfenstein or Spear of Destiny you own, note the items to be defined for that version, and uncomment those items, commenting the rest as needed. (To uncomment a line, remove the "//" that leads off a line, and to comment a line, add "//" to the beginning of the line.)

For the full version of Wolfenstein 3-D (Activision), these lines should read as follows:

```
//#define SPEAR 
//#define SPEARDEMO 
//#define UPLOAD 
#define GOODTIMES 
#define CARMACIZED 
//#define APOGEE_1_0 
//#define APOGEE_1_1 
//#define APOGEE_1_2 

```[Optional step if installing both Wolf3d and SoD]
Next, open "Makefile" (not "Makefile.dc") in a text editor, and find the line beginning with "BINARY ?=". Change "wolf3d" to a legal name for the game you're installing. If it's Wolfenstein, you may leave it as is, but if it's Spear of Destiny, I recommend "spear". The relevant line on my SoD Makefile reads as follows:

```
BINARY    ?= spear 
```[/optional step]

[Optional step for smarter installation of compiled applications]
Next, install "checkinstall" from the repositories ('sudo apt-get install checkinstall'). This utility will package the installation as a .deb package and integrates it with Synaptic (which makes for easy removal as well as cleaner system management).
[/optional step]

Open Synaptic (or use 'apt-get install') to install the following packages:

-- libsdlmixer1.2-dev
-- libsdl1.2-dev
-- libsdl1.2debian    <-- This one is probably already installed.

It may also be necessary to install one of the following:

-- libsdl1.2debian-alsa
-- libsdl1.2debian-nas
-- libsdl1.2debian-oss
-- libsdl1.2debian-pulseaudio    <-- I'm using this one, but I suspect I should actually be using ALSA; one of these is probably already installed (and if so, you should leave it alone).

If you installed "checkinstall," open a shell, navigate to the directory for the extracted source code, and run 'sudo checkinstall' from within that directory. Note that "checkinstall" has various options for your custom .deb package; tinker with these as you like.

If you didn't install "checkinstall" or don't want to use it, run 'sudo make install' from within that same directory.

* Note: it may be necessary to mark 'Makefile' as executable. You can do this with chmod or through Nautilus.

Assuming this is successful, the game is installed. Now you simply need to copy the data files for whichever version you own off of your CD(s) and into a directory of your choosing.  To run the game, navigate to the directory in which the data files are held, and run 'wolf4sdl' (or whatever you named the application when you edited 'Makefile'). If you want, you can also create a shell script to navigate to that directory and start the game, including any switches you prefer (windowed mode, resolution, etc.), and even add this script to your launcher for ease of use -- I assume interested parties can either figure that out themselves, or already know how (anyway, there are plenty of tuts for that sort of thing).

This all worked for me. It was a pain in the ***, but it was all worth it the first time I heard an SS say, "You butthole" (I know, but that's what I always thought they were saying). Also, I play keyboard-only (when I first played Wolfenstein and SoD, mice weren't supported), so I have no advice regarding mouse or gamepad use.

I still have my "Official Hint Manual" for Wolf3d (including complete maps for all six episodes), so it's been fun getting 100% on everything, but I wouldn't mind some similar intel for SoD... off to the Google machine.

Best of luck!

---

