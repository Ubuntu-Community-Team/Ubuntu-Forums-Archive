---
title: "Brasero says I don't have permission to...????"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by disastrophe on 2010-07-04
Hi there. I just recently made a clean break with windoze and am currently using Ubuntu 10.04/2.6.32-23. I'm rather new to some of the error messages. I was burning an iso of xubuntu and I wanted to perform an integrity check. I loaded the disc and plugged the md5 hash into Brasero. After stammering for a bit it tells me:
"The file integrity check could not be performed. You do not have the required permissions to use this drive." 
Huh? I just burned the silly thing and the disc was mounted. Maybe I'm taking the message too literally, it's a tad ambiguous. But I'm just a little confused. What would permissions have to do with a simple integrity check? Is this a bug or is it just it's little way of saying the disc didn't check out?
Is there a more robust application for performing these tasks? I would appreciate any advice. Thank you.

---

### Post by NUboon2Age on 2010-07-04
It sounds like for some reason the drive has 'permissions' set not including your username (probably root).  I'm not sure how to approach this, but if Brasero was having trouble one thing you might try is to start the program from a terminal with sudo.  So like

```
sudo <programname>
```

This will ask for your authorization and then run as root so it should bypass any permissions issues.

One thing i don't know however is what the name of your program is when starting from the command line.  I don't know if Brasero is called 'brasero' from the command line (sometimes programs have a different name that shows up in the GUI from what the CL name is).  You'd need to know its name.

Secondly i know nothing about MD5 so if its something specific to that, I might be completely off base about all of this.

Good luck, and please report back what works.

---

### Post by disastrophe on 2010-07-04
I actually tried that before I posted and nada. It is simply "brasero" from the command line. I've seen winders vista/7 give similar messages when unable to read media but that's usually because it's locked by another process (such as itself if it has two exploder windows open, but that's another story lol. ;)) 
The hash on the downloaded ISO checks out just fine but I do need to verify the discs, I don't want an install failing and mangling things up. I may lack the experience to deal with such an event constructively in a dual boot environment. Hopefully it's just a case of bad media or a bad burn.

---

### Post by disastrophe on 2010-07-04
Update:
I have tried a few things with the following results:

Brasero always ends with the same error when attempting to verify the discs. _(0_ for 5 now.) I got cdck from Synaptic which only does timing checks and got these results - Discs burned with Brasero/CD DVD Creator always came out with the last four or five sectors as unreadable. (maybe can be ignored?)
Discs burned with Gnome baker. I just got it this morning to see if it made any difference. - cdck showed a bunch of sectors toward the end as unreadable. Up to 42. (trash can)
Booted into Kubuntu, installed and ran K3B - burned fine and it was able to verify the discs easily. cdck showed no probs either. I ran a couple of more as tests and they checked out as well.  I also noticed cdck was able to perform the timing checks much faster on discs burned with K3B.
>
>
I used the same ISO to burn all discs. Gnome/Brasero/GB - _0_ for 5.  KDE/K3B - _2_ for 2. 
Too bad about Kubuntu's multimedia difficulties, DVD playback and such. 
Well, I'm getting low on discs lol. Better shoot up to the store.:rolleyes:

---

### Post by philinux on 2010-07-04
I run gnome but use k3b. Gnomebaker is not to bad either.

---

### Post by RedRat on 2010-07-04
I have always had problems with Brasero, it is a dog. I use GnomeBaker and K3b, both of those work fine. I have read here in the forums, a lot of people have problems with Brasero. Try one of these other burning programs.

---

### Post by disastrophe on 2010-07-04
Yeah, I'll try it out in Gnome. As long as it doesn't add a bunch of KDE sub systems it seems like the way to go, I tried running the two environments in a concurrent install when I first started with Ubuntu and they kind of trip all over each other, as well what looked like a really bloated global heap(windoze speek), thanks!

---

### Post by disastrophe on 2010-07-04
Woo hoo! Works great, just make sure not to take the recommends from Synaptic, you'd practically end up with KDE lol. Thanks again!
Somebody either needs to fix Brasero or remove it from the default Ubuntu install, that's the kind of stuff that could keep a lot of winders users away.

---

### Post by rocksockdoc on 2012-01-12
This problem appears to be a bug within Ubuntu.
- [URL="http://ubuntuforums.org/showthread.php?p=11604710#post11604710"] **     [COLOR=#980101][B][ubuntu]**[/COLOR] What do you use to verify a DVD image was successfully burned to optical disc?  [/B]
[/URL]
I'm not sure how to file Ubuntu bug reports against "wodim" ... so if you know how, please let me know.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210648&stc=1&d=1326311812[/IMG]
> BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: Error trying  to open /dev/sr0 exclusively (Device or resource busy)... giving up.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: WARNING: /dev/sr0 seems to be mounted!
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom:  Device or resource busy. Cannot open '/dev/sr0'. Cannot open SCSI  driver.
BraseroBurn: (at burn-job.c:113) BraseroReadom called brasero_job_error
BraseroBurn: (at burn-job.c:1140) BraseroReadom finished with an error
BraseroBurn: (at burn-job.c:1174) BraseroReadom asked to stop because of an error
        error           = 4
        message = "**You do not have the required permissions to use this drive**"
BraseroBurn: (at burn-task.c:182) stopping BraseroReadom
BraseroBurn: (at burn-job.c:906) BraseroReadom stopping
BraseroBurn: (at burn-process.c:709) BraseroReadom got killed
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible targets try '**wodim** -scanbus'. Make sure you are root.
BraseroBurn: (at burn-process.c:417) BraseroReadom stderr: readom: For possible transport specifiers try '**wodim** dev=help'.
...                      

---

