---
title: "make erroring out"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Jim Rogers on 2007-01-25
make all fails with the following:

Entering directory '/usr/src/linux-headers-2.6.17.10-generic
*** No rule to make target 'driver/module' STOP
Leaving directory '/usr/src/linux-headers-2.6.17.10-generic
make all [ERROR 2]

In reading another post concerning this problem.. bigdave146 stated he "Installed gcc, make, kernel headers, and source from Synaptic. I went to the synaptic site but could not fathom what I was supposed to do.... There is link to some Debian stuff and there is on another page a list of downloads ... No explanation as to which to get....

My purpose is to compile and install drivers for my Linksys WMP54g wireless card which has the Ralink rt61 chip set and I have downloaded the files from Ralink and have everything set for the compile...

Mystified at present.

---

### Post by Jim Rogers on 2007-01-25
OK, it was a dumb question. Using the synaptic manager, I found that the header files are out there.

So apparently there is something in the makefile that does not resolve itself and the compile errors out.

"No rule to make target 'driver/module'"

A rule is missing??? then I guess it back to Ralink and see what is missing ????

Works for me, I will give that a try.

---

### Post by Jim Rogers on 2007-01-25
Boy oh boy!
Senior moments..... Not good for former Sr. Systems Analyst....

Make does not like directories with spaces in the directory name.......Windoze stricks again.

Good compile, now let's see if I can follow the rest of the directions.

Sorry for the band width

---

### Post by port on 2007-03-19
ur a genious i was having the same problem, took out the space in the directory and it works!! ahhh

---

