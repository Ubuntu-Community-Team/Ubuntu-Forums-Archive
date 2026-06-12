---
title: "Can't find cups library when installing dymo printer drivers"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by phubert28 on 2010-06-05
64 bit Ubuntu 10.4

I downloaded the dymo-cups-drivers-1.2.0.tar.gz and unpacked it... tried runing ./configure and received:

error: Can't find cups library

From all I have read, however, Dymo printers, simply do not work fully directly under Linux.

Still, I would like to go as far as I can in configuration (it looks like I'll need to run WinXP as a VM in vbox if I want it to work WITH Dymo software!... and I have little confidence for that at this point...)

From Dymo's SDK doc:

The following products can work only when shared over the network from a Windows machine.
This is due to limitations in the USB support in these printers – Linux USB support only
recognizes fully compliant USB devices.
   • LabelMANAGER 400
   • LabelMANAGER PC

---

### Post by davidmohammed on 2010-06-05
does this [howto]("http://ubuntuforums.org/showthread.php?t=861781") help?

---

### Post by phubert28 on 2010-06-05
That was where I started, David. And I posted my problem (above) there as no more than:

I tried Mike555's instructions (with sudo), but got the error message:

configure: error: Can't find cups library

What I find odd, however, is that in Nautilus I can see the dymo-cups-drivers-1.2.0 directory, but from terminal using ls -Al, I do not, though cd navigates into the directory... ???

---

### Post by davidmohammed on 2010-06-05
dont quite follow - you've downloaded the drivers file and it is downloaded into ~/Downloads

correct?
You have unpacked it in this directory as a directory called (for example) ~/Downloads/drivers

then in a terminal you can 

cd Downloads/drivers

at that point you do sudo ./configure and get the error. Correct?

... just wondering if this is a 64bit vs 32bit issue and if cups is in a different directory from 32bit.

Look inside the file configure.  Search for your error message.  Where is it expect CUPS?  Suggest change the expected file/folder location to where it is in your 64bit installation.

---

### Post by phubert28 on 2010-06-05
Well, actually it's unpacked into /home/paul/dymo-cups-drivers-1.2.0

I'm looking into a 219K shell script in that directory...

Navigating TO that directory and keying "configure" doesn't find the command (shell script)

Now, mind that I know essentially nothing about bash... found the IF FI with the 'not found' message, but it looks like IT is echoing a line # ... something I DON'T see in the actual error message ...

There was quite a list of "configure" files in the FIND I ran.

Nevermind, I'm probably wasting my time (and yours) anyway... most likely I need to access the printer FROM Windows if I want it to do what I need - ESPECIALLY since the Dymo PROGRAM I need only runs under Windows!

In the configure.log I see the line #: 3513.
It was looking for "lcups" and I wasn't able to find that in a search (unless, of course, it's a variable!)

Looks like (if it is a variable) it may have been SET to $LIBS - tho I don't see THAT defined...

**

So far I don't see a way to display line #'s in gedit... TRIED to display in emacs23 but saw no line #'s!!  ---O.K. in the 'status' bar or whatever, at the bottom, not in-line with each line of text as I was expecting!

---

### Post by richud on 2011-01-10
missing libs... works fine in x64 ubuntu 10.10

sudo apt-get install libcups2-dev
sudo apt-get install libcupsimage2-dev

then 

./configure
make
sudo make install

I added printer then manually pointed it to ppd files it creates in
/usr/share/cups/model/XXXXXX

hope it helps!

---

