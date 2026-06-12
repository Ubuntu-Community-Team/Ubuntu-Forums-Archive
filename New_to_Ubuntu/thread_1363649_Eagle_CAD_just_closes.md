---
title: "Eagle CAD just closes"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by fiddler63 on 2009-12-24
I have installed Eagle CAD on Ubuntu 9.10.
I can start Eagle ok, but when I try move a component in the schematics the programs just closes.

Everything has been installed via synaptic

If I run Eagle from the console it says "segmentation fault" after its closes (same behavior as above).

Any suggestions ?

Cheers

Kim

---

### Post by fiddler63 on 2009-12-24
Looking at other segmentation fault threads, this happens when I run Nautilus in the terminal.

kim@kim-desktop:~$ nautilus

(nautilus:10469): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
kim@kim-desktop:~$

---

### Post by fiddler63 on 2009-12-25
bump.. 
Its the 64bit Ubuntu I have installed.
Since Eagle CAD is 32bit there might be an issue there.

Been trawling the net but no answers yet

Cheers

kim

---

### Post by fiddler63 on 2009-12-25
Just needed to do this

cp /usr/lib/eagle/bin/eagle ~/.eagle/bin/

See this thread
[https://bugs.launchpad.net/ubuntu/karmic/+source/eagle/+bug/475891](https://bugs.launchpad.net/ubuntu/karmic/+source/eagle/+bug/475891)

The bug is not solved yet, but the above appears to work for now.

Kim

---

### Post by fiddler63 on 2009-12-26
Well, now when I open the Library I get the segmentation fault again.
Back to the drawing board.

---

### Post by Tankerdog2002 on 2009-12-26
We had the same problem.

We solved it by using another CAD program. VariCad for LINUX.

Hope this helps.

---

### Post by fiddler63 on 2009-12-26
Unfortunately, I have heaps for old files for Eagle which I needs to be able to use.
Works OK in Windows and Suse distro

Kim

---

### Post by fiddler63 on 2009-12-26
Upgrading from Eagle version 5.4 to 5.6 seems to have eliminated the issues.
5.6 is not a Ubuntu supported version so you will have to install directly.
Pretty simple as I figured it out :-)

Kim

---

