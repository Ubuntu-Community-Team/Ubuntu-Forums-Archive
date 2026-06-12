---
title: "GSPCA headache"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by Formerly on 2011-01-30
I'm using the most recent linux version and attempting to install GSPCA in order to use my webcam for "tinychat.com" which seems well-documented on many standpoints for this basic procedure. The GSPCA document itself has a "read_and_install" file to help those who are attempting at installing not need to search, the instructions are all there.

> ow do I use it?
================

Well, first you need to compile the driver (see below), then you need to make
sure that the v4l infrastructure is set up and then load the driver. After
you've done that, any v4l enabled application, such as spcaview, gqcam, xawtv,
gnomemeeting, camE etc should work.

Supported kernel versions
=========================
The driver should compile and run successfully against most stable versions of
the official Linux 2.6.x kernel upto version 2.6.11 (from <http://www.kernel.org/>)

Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build 

if all goes right the module is compiled and load in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer
or in the sourceforge project bugs report. <http://sourceforge.net/projects/spca50x/>.

Trying a v4l app
================
goes to gspcagui directory
be sure to have libsdl installed with the header
then
make
as root
make install
Plug your webcam and run
gspcagui -d /dev/video0
adjust video0 to your hardware
Press the G button and wait for the webcam probe
you can now play, the two windows are active 
mouse can be used to select a Region of Interess within the grabbing windows
then press the center of the pad to zoom:)
Picture and avi are implemented just press the button to start/stop

That is all the information that I have been using within this document, my problem occurs on home base. the 'make [config|menuconfig|xconfig]; make dep'. command doesn't seem to be recognised, assuming I'm supposed to use this on my terminal.

> make: ***No rule to make target `[config'. Stop.
And from there all other 3 commands say "command not found"

In short, my problem with installing GSPCA is that ... Nothing is working? The majority of documentation I can find is years old, I checked the list and my webcam is supported by this driver substitution. As well, I went through the procedures to make my webcam "allow" to share on tinychat.com so now my icon will appear but the chat itself will not recognise my webcam to view. Webcamstudio and cheese won't work properly either, everything seems to be one big twisted mess.

If this explanation is understandable by anyone who knows how to help, I'd like to ask for an easy to understand walk-through to fix my current problems? I would be very appreciative

- Joe

---

### Post by robsoles on 2011-01-30
Assuming I've figured out what is required from you to get this going, please try the following. Note but that [COLOR=Blue]I[/COLOR] haven't compiled this specific package.

Open terminal and navigate the prompt to whereever the archive has been unpacked;
```
user@system:~$ cd Downloads/whatever-its-folder-is/
user@system:~/Downloads/whatever-its-folder-is$ sudo bash
[sudo] password f...
user@system:~/Downloads/whatever-its-folder-is# ./make
...
... lots/(some at least) of output
...
user@system:~/Downloads/whatever-its-folder-is# ./make install
...
... more output
...
user@system:~/Downloads/whatever-its-folder-is# exit
```That last instruction there hands in your 'root credentials' in terminal and it is important that you don't "muck around" as root.

Please post back the output from terminal from the command you entered to the end of the errors, if there are errors from any command ;)

---

### Post by no2498 on 2011-01-30
from 8.04 and up GSPCA is already in the kernel 
install xawtv and cheese try the cam in them
for tiny go to the adobe site find the settings manager 
allow and remember the site's you use the cam on

hope this helps

---

### Post by Formerly on 2011-02-01
Okay, so I'm assuming then that GSPCA is already in the kernel and that would mean I don't need to go through the whole headache of trying to get it working. After that I installed Cheese and uninstalled this "webcamstudio" program I had and restarted. I can't find how to decompile xawtv after extracting it.

At this point Cheese works perfectly, xawtv is extracted but not decompiled, and I can see my webcam on the "selection" screen of tinychat yet when clicked my video doesn't show. What would the course of action be from here?

Also, thank you both for your help so far :)

---

### Post by no2498 on 2011-02-03
if your using fire fox install grease monkey
i use opera it works good for me

---

### Post by Formerly on 2011-02-09
Greasemonkey didn't seem to do anything, as I can tell it allows user made scrips for firefox? Maybe there is a user made script I should use for it that I didn't see?

The odd part is that in the selection screen for my webcam I can see it in motion, after selection on the cam screen it only shows a microphone icon.

---

### Post by no2498 on 2011-02-10
open your package manager look for xawtv the top 1 in the list should be came its a re wright of xawtv install it too
xawtv is on the bottom of the list

? is your adobe up to date

the way i install adobe is look in the package manager for flash
remove what the system has installed not a conpleat removal
go to adobe site install flash
then in a terminal i reinstall the extras

---

### Post by robsoles on 2011-02-10
> **no2498 said:**
> open your package manager look for xawtv the top 1 in the list should be came its a re wright of xawtv install it too
xawtv is on the bottom of the list

? is your adobe up to date

the way i install adobe is look in the package manager for flash
remove what the system has installed not a conpleat removal
go to adobe site install flash
then in a terminal i reinstall the extras

Checkout 'flashaid', it is an addon for firefox in Ubuntu which semi-automatically (details what it is going to do with a 'do it' type button, then you have to enter sudo password in terminal that opens) removes all possibly conflicting flash-type items and then downloads and installs the correct version of flash for your system for you - most painless way I've fixed flash problems in Ubuntu ever.

---

