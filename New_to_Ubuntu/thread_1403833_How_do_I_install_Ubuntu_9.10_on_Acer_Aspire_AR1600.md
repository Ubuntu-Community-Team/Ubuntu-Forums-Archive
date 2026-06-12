---
title: "How do I install Ubuntu 9.10 on Acer Aspire AR1600-E910L"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by RedOctober on 2010-02-10
I just bought this thing 30 minutes ago out of frustration at all my XP EEE boxes are freezing, leaving our business "Sweet Out Of Luck".  I have been playing with Ubuntu 9.10 for a few months now and all I need it to do is run .Rdp connection into a Win2003 Server.  All works on my old test box, however, I am unable to figure out how to load it on the subject machine.

I have Ubuntu on a bootable DVD and on a bootable USB.  I have gone into the BIOS of the subject machine and told it to boot from "Removable Device" (no go) then "CD/DVD" (no go).

I have been through the forums and cannot find what it is I'm doing wrong.  The subject machine simply boots to FreeDos (the OS that it comes with, and sits there at C:\ prompt)

I can go D: to get to D: drive which is the USB stick with bootable Ubuntu on it, but I cannot run WUBI.exe in DOS mode.

I'm stuck.  Any suggestions to get me going on Ubutnu?  Thanks in advance.

---

### Post by RedOctober on 2010-02-10
For all who follow me:

I have made some progress.  I'm using a Samsung SE-S084 External USB CD/DVD drive, with a bootable Ubuntu 9.10 CD in it.  I guess I was not allowing enough time for the Samsung to load it's BIOS-able junk into the brain of the Acer box, so, it was never recognized by the BIOS.

After waiting a while, (and plugging in BOTH USB cable ends of the Samsung), I went into BIOS and wadayano, it's listed as a bootable device.  So, I just set it as the first "Boot From" item and it is now loading.

Thanks for "Dr. Phil -ing" me in my time of need.  I know you were listening even though no one responded in the 5 minutes I went without an answer.  Hopefully this can help some one else.

---

