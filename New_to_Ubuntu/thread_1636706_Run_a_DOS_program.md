---
title: "Run a DOS program?"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by Greg Mueller on 2010-12-03
I am using 10.04

I have an old CadCam program that runs in DOS. Can I run that in my Ubuntu computer somehow?

My old DOS computer is about ready to die

---

### Post by Zzl1xndd on 2010-12-03
Might work with DOSbox (available via the software centre).

---

### Post by mister_playboy on 2010-12-03
If DOSBox doesn't run it, you could also try a FreeDOS virtual machine in VirtualBox.

---

### Post by lkraemer on 2010-12-04
Here is a HOWTO: that I've posted.  Some of the information may not
apply to your DOS Software, but the same method should make your
software functional.

[http://ubuntuforums.org/showthread.php?t=1569510&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=1569510&highlight=dosbox)

[http://ubuntuforums.org/showthread.php?t=1508508&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=1508508&highlight=dosbox)
Posting #10

[http://ubuntuforums.org/showthread.php?t=1383627&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=1383627&highlight=dosbox)
Posting #3

[http://ubuntuforums.org/showthread.php?t=853174&highlight=dosbox](http://ubuntuforums.org/showthread.php?t=853174&highlight=dosbox)

You may also wany DOSBOX-FE which is a Front End for DosBox.

LK

---

### Post by Penguin=) on 2010-12-04
Get DOSbox OR FreeBox (i think its called) DOSbox is better but its up to you!, you can get them via the Ubuntu Software Center!

---

### Post by Greg Mueller on 2010-12-04
Thanks guys.
This should give me something to experiment with

---

### Post by Greg Mueller on 2010-12-04
I've got DOSbox going and it is showing promise, but I am having trouble getting the contents of the subdirectory (programs and drivers and what nots) on the physical drive into the virtual drive C:
I copied all the files and folders into my hard drive at
 /home/greg/dos/C
When I start Dosbox I have fixed the autoexec.bat to auto mount the C: but there's nothing in it. I can't figure how to mount the C: drive with all the files and subdirectories that I loaded onto my hard drive. When I do a " dir *.* " it shows nothing.

I am having fun tho

I used to be pretty good at running dos before windows came along

---

### Post by mr.farenheit on 2010-12-04
i would give dosemu a try

---

### Post by Greg Mueller on 2010-12-04
I change the autoexec to this

mount c /home/greg/dos/C
C:
cd\nc

now I get file names etc

Now the problem appears to be display drivers when I try to run the cadcam program

---

### Post by Greg Mueller on 2010-12-05
Got most everything to work now. The only weird problem is that the numlock doesn't work unless I hold down the shift key?

---

