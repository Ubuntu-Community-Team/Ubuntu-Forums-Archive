---
title: "Linux Application(s) (Suites) entirely on USB"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by uWitchDoctor on 2009-03-05
I have recently got an asus eee and I just want to keep the absolute basics on it such as a web browser, email client, calendar, media player, IM and general office apps (Open Office most likely). This is mainly due to limited space but also because the thing just isn't designed for doing much else.

However, I intend to use this little beast in lectures at uni mostly and would benefit from being able to run other apps on it even if they are a bit sluggish. IE, in a programming lecture it might be handy to open Dev-C++ and to be able to write and compile C++ just to help it sink in.

What I want to be able to do is stick these extra apps on SD cards and run them from there. Can this be done with any application? I know in windows you can download portable applications. However in linux, can every application be run portably? It would be fantastic if I could have a web design SD for running Bluefish, JEdit, Eclipse, Gimp and Inkscape or a graphics design SD for running Blender, Gimp and Inkscape... and for when I get bored in lectures and SD for running THPoker and other games :)

*To summarise, can I install and run applications entirely to and from SD cards so everything is on the SD card and nothing is installed on my eee. In theory so I could stick the SD card in another eee which it wasn't installed from and run it still?*

---

### Post by uWitchDoctor on 2009-03-06
Can I do this with chroot?

I have been looking around on the internet for ways to do this. I'm sure with linux there must be a way to install something completely independant and on a USB/SD card so to the app it thinks it is on the machine and runs on the USB/SD and stores everything on the SD/USB.

does anyone have any information regarding my original request?

:)

---

### Post by C.S.Cameron on 2009-03-06
Not sure how to run Linux apps from a flash drive or SD card other than by installing Linux to it.
However I have copied a Wine folder to a flash drive and the apps inside run ok when it is plugged into a computer that has Wine installed.

---

### Post by thtrgremlin on 2009-03-06
You can run linux binaries from another disc, but not a lof of programs are distributed this way. To keep things simple, I would recommend installing ubuntu-minimal onto the flash drive, then you can chroot to the disk, and run the applications from there. It will just use your current window manager and X11 session, so you don't need anything more than minimal installed on the disk.

Would you like some help with what is involved in that? 

The other option is to compile the programs from source just using 'make' and kipping the 'make install' part, then just run the programs with './src/foo', but I don't have much experience with that.

---

### Post by bodhi.zazen on 2009-03-06
another suggestion :

Portable Apps : [http://portableapps.com/](http://portableapps.com/)

Freely available, runs on wine or windows, encryption utilities available.

---

