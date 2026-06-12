---
title: "New problem with Olympus odvr driver Ubunto 8.01"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by LyonTamer on 2009-04-14
I recently upgraded from 7.10 to 8.01. I redownloaded the .deb file for my Olympus vn4100-pc from this website [http://code.google.com/p/odvr/](http://code.google.com/p/odvr/). The driver and recorder worked on the older Ubuntu version. The package installer GDebi shows the driver is installed. But when I run the command odvr -l in terminal, it says "Failed to open Olympus device: couldn't claim interface".

I tried opening the driver from the Google website directly rather than downloading it first, and it prompted, "/tmp/odvr_0.1.4.1_i386.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences."

What does this mean? What association?

---

### Post by t0p on 2009-04-14
Sorry, I can't help with your problem.  I just want to point out that there is no "Ubuntu 8.01".  The version number is 8.10, which indicates it was released in October 2008.

I was also going to say that it's not "Ubunto".  But I'm sure that was just a typo, right?

---

### Post by LyonTamer on 2009-07-02
Not a typo. An alien came and changed some of the keys around while I slept. :D

Seriously though, I found the solution. Save the file to desktop, then open it with Debi outside of Firefox. Code to run odvr in terminal is sudo odvr -l.

---

