---
title: "Urgent! boot failure, login failure"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by trinian on 2009-03-20
I use Hardy Heron on a generic Elonex-powered webbook. I didn't power it up for a month, using an HP Pavilion with Windows instead, but then decided to clean out the webbook and retrieve some files. I open it, LOG IN NORMALLY, but the pointer was jamming randomly + the display had foggy areas where colours were switched. Since I couldn't move the pointer I pushed the 'off' button on the machine then managed to move the pointer to restart. 20 minutes all in all.

When it restarted it did the automatic fsck (/dev/sda1), which failed.

[COLOR="DarkSlateBlue"]Error reading block 16449577 (attempt to read block from filesystem resulted in short read) while getting next inode from scan.

/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY.
(i.e., without -a or -p)
fsck died with status 4[/COLOR]

So basically the root filesystem is mounted in read-only mode (automatically), the maintenance shell gets started, but if I run an fsck for /dev/sda1 manually, I get the same error message with block 16449577.

Restarting the system (ctrl+D) and hitting Esc to get out of the automatic fsck gets me to the login screen, but when I type my username and password I get the following message:

[COLOR="DarkSlateGray"]GDM could not write to your authorisation file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.[/COLOR]

What the hell?! If it's restarted, then shouldn't the read-only mode for the filesystem that got switched on for the manual fsck earlier be, well, irrelevant and not apply? Shouldn't the home directory be open for writing?

If you have had similar problems, please let me know how and if you fixed them. I'm  in Romania until May, Ubuntu is pretty exotic here and I can't get pro help other than getting the machine wiped clean and installing Windows on it, losing my folders in the process. I really need to recover my files from it before April 1. And I was thinking of installing Ubuntu on my main laptop as well as a dual boot, but that depends on how this issue plays out... Help!

---

### Post by Nxion on 2009-03-21
I had to say it but in my experience it sounds to me like the hard drive is bad. Do you have a Live cd you can boot off of to retive the data that you need?

---

### Post by theozzlives on 2009-03-21
As I was reading, I was thinking "bad hard drive" glad I got a confermation. Did you try ctrl+alt+F1 at the lonin screen and log in the console. If your read only you can still get your files off.

---

