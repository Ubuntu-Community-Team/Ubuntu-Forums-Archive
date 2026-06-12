---
title: "Scanjet G4010 in amd64 Meerkat"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by grey1beard on 2010-11-20
Now I know what it would be like going round a steeplechase course without a horse !

In my slow canter round the track in the race called "get your scanner working under 10.10", I can now tell my frontend from my backend.
Reading all the doom-laden posts of other people's problems getting their own scanners working, I've found a couple of posts promising success, and learnt a little in the process.

I've got as far as finding that the Sane backend that I lack is probably 1.0.16, so I have downloaded both the tar.gz and the diff.gz as I have no idea which one I need to make the installation with.

Come to that I have only a vague idea how to do it anyway, with age wiping the memory cells as fast as I can link them up.
Ho hum.
So I'd be very grateful if someone could help me over the next hurdle or two.

John

---

### Post by khelben1979 on 2010-11-21
The [source package].tar.gz is the right one. Once you have unpacked the archive with tar xvfz [source package].tar.gz, you enter the file catalog where the unpacked files are located.

Steps:
1. ./configure
(this checks if your present system libraries in your Ubuntu 10.10 matches what is required by the configure script)

2. make
(this compiles the source code, can take several hours if you're on a slow computer, so be patient! Time to make some coffee.)

3. make install 
(this haveto be run as root, since it installs the compiled source code directly in your Ubuntu system)

B.t.w. your scanner has basic support if you manage to get it working, so don't expect any better resolution from the driver than 100 to 600 DPI.

---

### Post by grey1beard on 2010-11-21
Thanks khelben1979.
It's always reassuring to know that someone out there is watching over you ;)

I had come across the limited functionality that I'd get, but that will do for now.
Regards
John

---

### Post by khelben1979 on 2010-11-21
You're welcome! :-)

---

### Post by grey1beard on 2010-11-21
I've managed to navigate my way through the process of ./configure , make, make install, and restarted the pc.
However, neither Simple Scan nor Xsane can find the live and connected scanner, so I'm leaving the problem for tomorrow.
I'll also post an Absolute Beginners' "How to" on what I did to get this far, for anyone following the same road.
Regards, and goodnight,
John

---

### Post by grey1beard on 2010-11-22
Now started to follow the trail of the scanner, and why I haven't yet got it recognised.

lsusb detects it, but sane-find-scanner doesn't, but suggests
"#...make sure that
 # you have loaded a driver for your USB host controller and have installed a
 # kernel scanner module."
Nor sure what either of these imply, or how to go about finding out, but will follow them up next.

---

