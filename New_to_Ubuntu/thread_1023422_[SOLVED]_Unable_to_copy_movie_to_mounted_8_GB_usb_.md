---
title: "[SOLVED] Unable to copy movie to mounted 8 GB usb memory  stick"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Russell Burrows on 2008-12-27
Running Ubuntu latest 32 bit version.
Downloaded and installed and works fine.

Toshiba laptop satellite L305D-S5892

On removable 1 Gb, 2 Gb and 4 GB mounted usb memory sticks everything works fine with ability to copy movies, music, etc from desktop folder to usb mem. sticks with no problem.

But.

On inserting an 8 Gb Kinston or Sandisk or other 8GB mem stick then thats when the fun starts.

Mount and un-mount are no problem.

It begins to copy the music, movie, document, etc. file and hangs at 58.5 MB copied.

Fixes tried:
Reformat 8 Gb mem sticks, double reformat, triple reformat to either fat32 or ntfs and nada.

[B]Triple reformat on three separate computers to fat32 and nada, no work on MY laptop.

Tried the same 8 Gb mem sticks on Xp and Vista computers and they all work great and then I try these same 8 GB mem sticks in my laptop and nothing, nothing and nothing!

Used search function for a gui fix and tried search words usb and glitch, not working, not supported, mem stick failure and nada, nothing and I have no idea what to try next.

Used google, altavista and ask search engines to try to find a fix and I found some non gui funny code that I am in no way going to experiment with to try and see if that funny code in something called a terminal may work or it may kill my laptop.

Thanks for reading this.[/B]

---

### Post by nhasian on 2008-12-27
not sure if this will help or not but have you checked with toshiba to see if you have the most recent bios for your laptop?  since we know the usb drives work fine in another computer, it must be something in the toshiba.

---

### Post by egalvan on 2008-12-27
> **Russell Burrows said:**
> 

Fixes tried:
Reformat **8 Gb** mem sticks, double reformat, triple reformat to either **fat32 **or ntfs and nada.

Triple reformat on three separate computers to **fat32** and nada, no work on MY laptop.


First, FAT32 has a 4GB file-size limit. You CANNOT copy an 8GB file intact to a FAT32 file-system.

Second, the fact that they work on another computer only proves that the sticks are working...
and in fact tends to point the finger at your computer.
Your computer may not be able to "see" such large sticks. The USB controler chips may not be up to date.

As the other poster suggested, check for a BIOS update.

I am not familiar with your computer model, so you will have to check with the manufacturer for info on this.

I use Ubuntu with large USB memory without issues...

ErnestG

---

### Post by Russell Burrows on 2008-12-28
Thanks for the replies.

I just inserted an 8 Gb mem stick formated to ntfs with a six GB movie file as a test.

It mounts fine and it copies the entire test movie file to a desktop folder intact.

The problem is when I want to send the test movie from the desktop folder to the memory stick that the fun starts.

I just placed the same stick into the laptop and tried to copy the same test movie file from the desktop folder back onto the memory stick and it begins to copy and stops at 58.2 MB

"error while copying "test movie"  

show more details

error writing to file: input/output error





And this only happens when copying from desktop folders to usb memsticks that are larger than 4 GB?


I just re-did the test using 1.8 Gb chunks of the test movie and they failed to transfer to an 8 gb fat32 formated mem stick.

But.

The same 1.8 Gb movie chunks when sent to a 4 Gb memory stick work just fine.

So its more of a glitch than a real problem.

As far as updateing the bios:

I tend to never try and "fix" a running system.

---

