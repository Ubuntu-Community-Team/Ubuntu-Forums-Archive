---
title: "Can't copy CD...What's wrong?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by sdim on 2011-01-18
Hi, everyone.
It seems that this time I'm left astounded at the thing I'm going to describe below.
I wanted to make a copy of a CD, so I popped it in the tray and clicked on Nero Linux 4 (at first).
When I clicked on "Copy CD" I got an error message saying that the process failed, and that within 1 second. I tried it again, but the same message appeared.
I re-inserted the CD and right-clicked so as to copy it using Brasero. The Copy dialog window came on, but no copy. It just went dead right there.
The funny thing is that when I rip the tracks of a CD, no problem. When I create an audio CD with Brasero or Nero, everything is OK.
When I copy a DVD, everything is OK. It won't copy a CD, that's the thing.
Isn't that a bit strange? It's never occured before in the 3 years I've been using Linux.
A thing I have to say, though, is that a week ago I changed mobo/CPU/RAM, which made the sound volume a bit lower than it was before.
Could it be that it has something to do with the issue I described above?
I would appreciate any help, as I don't know what to do.
Many thanks.

P.S. Here is the log file with Nero's error message:
```
    Linux (LinuxMint 10 'julia') 2.6.35-22-generic-pae (i686)
    Nero API version: 9.7.0.132
    Using interface version: 9.0.1.4
    Installed in: /usr/lib/nero/
    Application: Nero AG\Nero Linux Express
    Internal Version: 9, 7, 0, 132

    Recorder:             <HL-DT-ST DVDRAM GH22NS40>Version: NL00 - HA 2 TA 0 - 0.0.0.0
    Adapter driver:      <ahci>                    HA 2
    Drive buffer  :      2048kB
    Bus Type      :      via Inquiry data
    Excluded drive IDs:
    WriteBufferSize: 83886080 (0) Byte
    BUFE           : 0
    Physical memory     : 4022MB (4118748kB)
    Free physical memory: 3449MB (3532408kB)
    Memory in use       : 14 %
    Uncached PFiles: 0x0
    Global Bus Type: default (0)
    Check supported media : Disabled (0)

    18.1.2011
    NeroAPI
    11:19:58 PM   #1 NEROAPI 2 File NeroAPI.cpp, Line 7164
       Initialization failed
       
```

---

### Post by Mark Phelps on 2011-01-18
Check your preferences for the Copy operation.  It's generally done one of two ways:
1) directly from one CD to another
2) to a folder on the drive, and THEN, to a second CD

If 2) is set up with an invalid path, or insufficient space, the COPY operation will fail.

---

### Post by sdim on 2011-01-18
Thanks for the answer, but I can't find the info you asked.

---

### Post by sdim on 2011-01-19
Strange thing:
k3b copies the CD fine, but Brasero and Nero Linux, don't.
In Windows, though, everything is OK.
On the other hand, when I plug in an external DVD-RW I have, no problem. It copies everything with either Brasero, Nero or k3b.
I can't figure out what's happening. Is it hardware or software?

---

