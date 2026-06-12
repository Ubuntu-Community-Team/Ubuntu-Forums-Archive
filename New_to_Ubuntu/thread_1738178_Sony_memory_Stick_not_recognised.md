---
title: "Sony memory Stick not recognised"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Evanfox on 2011-04-24
Hi all, 

I mount a sony memory stick on my vaio but it seems that it is not recognized in my system.
Note that this was not the case in windows for some reason.

Any ideas?? :confused:

Thanks!

---

### Post by mynameisnotbob on 2011-04-24
Are you fully updated?

---

### Post by grahammechanical on 2011-04-24
How do you know it is not recognised? What are you trying to do with it? More information will help. It is my understanding that Linux operating systems can read and write to a Windows type file system but Windows cannot read and write to a Linux file type system. So, the format of the memory stick is not the problem.

Are you mounting the memory stick? Click on Places and the file manager will open. Do you see anything in the side panel that would represent your memory stick? There  might be a label giving the size of the memory stick or an icon with an image that represents a USB port. If you click on that icon you will mount the memory stick. The file manager should open a window giving you access to the memory stick.

Regards.

---

### Post by Evanfox on 2011-04-25
> **mynameisnotbob said:**
> Are you fully updated?

Yes I'am fully updated thnx


@Graham
I mean I cannot find it anywhere. It i my understanding that it should show up just as any other usb memory stick (which btw work fine!).

I went to places as you said but unfortunately I can't find anything representing my memory stick.

---

### Post by stoneage on 2011-04-25
It sounds like you didn't get a clean shutdown in Windows. The drive is effectively still mounted on the Windows machine. Ubuntu can't mount it because it is already mounted - on the Windows machine.

I'm guessing if you plug it into a Windows machine and use the 'Safely Remove' option it should mount fine in Ubuntu afterwards.

If that is the problem, it is Windows to blame for not cleanly unmounting the drive.

:D

---

### Post by The Cog on 2011-04-25
Did you have to install drivers into Windows to be able to read the memory stick? I think that Sony are rather fond of making non-standard parts so that you have to buy their over-priced parts to work in their cameras etc.

---

### Post by Evanfox on 2011-04-25
> **The Cog said:**
> Did you have to install drivers into Windows to be able to read the memory stick? I think that Sony are rather fond of making non-standard parts so that you have to buy their over-priced parts to work in their cameras etc.

No I don't remember installing anything, the system could recognize the memory stick, without further tweaking in windows.

---

### Post by The Cog on 2011-04-25
Hmm. Try running this command:
```
tail -f /var/log/messages
```
and leave it running (it prints anything that gets added to the log) and then watch it while you plug the stick in. See if any useful messages get produced.

---

### Post by Evanfox on 2011-04-26
> **The Cog said:**
> Hmm. Try running this command:
```
tail -f /var/log/messages
```and leave it running (it prints anything that gets added to the log) and then watch it while you plug the stick in. See if any useful messages get produced.

I mounted and unmounted the stick a couple of times but no new messages show up.

---

### Post by The Cog on 2011-04-27
What makes you think it's being mounted? 

I didn't expect to see messages when the stick is mounted/unmounted. I expext to see messages as the stick is plugged in.

---

### Post by Evanfox on 2011-04-30
that's right, yes, I mean when I plug it in!! :)

---

### Post by The Cog on 2011-04-30
I think you will find that with a normal memory stick, you will see lots of messages as it is inserted. If so that would confirm that the Sony stick is not compatible - somehow nonstandard.

---

### Post by Evanfox on 2011-04-30
> **The Cog said:**
> I think you will find that with a normal memory stick, you will see lots of messages as it is inserted. If so that would confirm that the Sony stick is not compatible - somehow nonstandard.

You're right, I do get some messages when I plug in another usb stick, but not with that sony memory stick.

---

