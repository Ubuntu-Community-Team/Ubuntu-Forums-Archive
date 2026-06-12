---
title: "New User - Looking to modify a program"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by KarlJr on 2010-05-29
Hello All,

I am have been using Ubuntu for a few months now.  I am using Ubuntu 10.04 LTS as my only operating system on my home computer.  I am really enjoying the look and feel.

I would like to get started in programming in the Ubuntu environment.  My programming experience is in RPG, COBOL and MS Excel macros.  I understand that I have a learning curve ahead of me but I don't know how to get started.  I have been searching the forms but didn't find the absolute beginners guide to modifying a program.

What I would like to do is modify the Simple Scan program to scan photographs.  I want to limit the travel of the scanner and set a default crop area to my photo size.  I picked this as a starting point only because I have a personal use to the modifications.

Any and all suggestions are welcome.

Thank you,
Karl Jr

---

### Post by lykeion on 2010-05-29
A look on the source for simple-scan tells me it's written in C, so if you wish to work with the code you'll first need to know the basics of C.

The package page of simple-scan [http://packages.ubuntu.com/lucid/simple-scan](http://packages.ubuntu.com/lucid/simple-scan) had a link to the project homepage, [https://launchpad.net/simple-scan](https://launchpad.net/simple-scan)
From there you can download the source code and have a look.

Personally I know very little C (and nothing of COBOL) so I couldn't give you a good start direction. But you could search this forum. When I did just now I found this post:
[http://ubuntuforums.org/showpost.php?p=2045086](http://ubuntuforums.org/showpost.php?p=2045086)

Good luck

---

### Post by anewguy on 2010-05-29
I'm sure you know, but RPG and Cobol are high-level languages - Cobol more "as spoken", RPG a little more cryptic (too many dang indicators!).  C will be a totally different animal for you to learn (been there).  Along with C itself, you will probably need to become familiar with the libusb calls and the actual command structure of the scanner involved.  I say this because libusb gives you access to the low-level commands and structures for communicating with USB devices, and the scanners will probably each have their own (although one would hope, somewhat standard) command set.  I've used libusb calls on other devices but haven't tried a scanner yet.  I wanted to as the lamp in my scanner doesn't turn off once it's on in Linux.  I've tried tons of suggestions to no avail, so I started running USB traces in Windows so I could see the command structure so I could write them in a C program for Linux, but the command set appears to be very complex and the manufacturer didn't want to release them to me.

I mention libusb specifically because in order to tell the scanner to limit its travel, you're going to need to communicate with the scanner itself, and you'll need to know it's command set.

I understand the reason for wanting to do this, but in all honesty this is a tremendous undertaking for someone new to C and to libusb.  I would honestly suggest adding the scanner support package to GIMP, scan using GIMP and crop using GIMP.  No, it's not automatic, but much easier in the long run.  GIMP is also scriptable, so once you get the sequence worked out to scan, crop, save you should be able to create the script to do it (or even better yet, post in a forum for help as someone may have already done so).

Dave ;)

---

### Post by Locke_99GS on 2010-05-29
Sources can be had easily by adding the source repositories, then using "apt-get source" to retrive the source for a particular package.

---

### Post by KarlJr on 2010-05-31
Thanks for the help.  This will give me a place to get started and other things to consider.

---

