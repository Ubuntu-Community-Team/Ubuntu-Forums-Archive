---
title: "newbie managed to screw up boot! help please..."
date: 2009-03-08
forum: New to Ubuntu
---

### Post by cairnzi on 2009-03-08
hi people, i wa messing round with my new kubuntu 8.10 and have really screwed up the boot, when i boot al i get is. [COLOR="#000000"][minimal bash-like line editing is supported. for the first word, tab lists possible command completion. anywhere else tab lists the possible completions of a device/filename. ] grub>[/COLOR]

can some kind person please assist in telling me what silly thing i have done and how if possible to sort it? ps. i do not have access to my live cd until tommorow so hoping that there is a way to fix without it, many thanks from a daft newbie:(

---

### Post by rraj.be on 2009-03-08
Type this command

```
sudo startx
```

or 

```
sudo start kdm
```

If it reports any error, Then post the error report correctly so we can help you as far as we can.

---

### Post by cairnzi on 2009-03-08
both commands come back with: error 27 unrecognised command.

any thoughts? cheers.

---

### Post by rraj.be on 2009-03-08
Try with sudo in front of the command

---

### Post by Skripka on 2009-03-08
> **rraj.be said:**
> Try with sudo in front of the command

That won't do much...seeing as how our OP  does not even have linux loaded-and is dealing with the GRUB console.

---

### Post by cairnzi on 2009-03-08
still same error with both commands, think i may have really screwed this up,any oher ideas?,thanks.

---

### Post by Skripka on 2009-03-08
> **cairnzi said:**
> both commands come back with: error 27 unrecognised command.

any thoughts? cheers.

Do you remember what you were messing around with?

When GRUB loads-do you get a listing of OSes to load-or just the console?

---

### Post by cairnzi on 2009-03-08
can remember the last command i entered, but it was to do with removing the 3,2,1 count down on the grub start up,it was entered in the konsole, it was somthing like- gksudo gedit/boot..... basically to just speed up the start up sequence by removing the 3,2,1 countdown, pretty pointless looking back now;)
no i dont get a os menu just. grub>

cheers.

---

### Post by fmfrisch on 2009-03-08
I would pop the live CD in, boot it, move important files to USB and then reinstall. Not really solving the problem. But if you don't know what file you edited it's probably the faster way.

For future reference, the count-down can be removed through Start-up manager (GUI) which minimizes the chances of screwing up a script.

---

### Post by cairnzi on 2009-03-08
@fmfrisch, yeah seems to looking like the easiest way to do it, will wait a wee while and see if anybody can think of a solution, if no the will just do as you sugest, didnt no you could remove the count down that way, many thanks.

---

### Post by Skripka on 2009-03-08
> **fmfrisch said:**
> I would pop the live CD in, boot it, move important files to USB and then reinstall. Not really solving the problem. But if you don't know what file you edited it's probably the faster way.

For future reference, the count-down can be removed through Start-up manager (GUI) which minimizes the chances of screwing up a script.

Well, there are a few differenet ways to go:

1) Repartition and nuke-this will always work...but you'll lose everything you don't have backed-up

2) Reinstall Ubuntu, but only erase your OS paritition....note this will only work if you have seperate /home and /root partitions...also there are many hidden files in /home which can wreak havoc on reinstall-they should be erased before doing this.

3) Reinstall Ubuntu on a different drive, and then move things back over....this is the safest of the "Nuke It" school of thought.  You'll end up with a perfectly healthy Ubuntu-on reinstall, and haven't lost anything.

The above are the nuclear options.  They are drastic, but you'll end up with Ubuntu back at least.  They can also be simpler and faster for inexperienced users than trying to fix something--if you don't have lots of time and effort invested in an install.

4) Odds are--what the OP needs do in redo the menu.lst file, as it got corrupted or damaged....not necessarily reinstall GRUB, but fix a b0rked menu.lst file.  And for that You'll want a SuperGRUB disk...there are other ways-but a SuperGRUB is a good thing to always keep around.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[http://supergrub.forjamari.linex.org/?section=documentation#grub_restore](http://supergrub.forjamari.linex.org/?section=documentation#grub_restore)

---

### Post by cairnzi on 2009-03-08
@Skripka cheers for the links and suggestions, didnt relise there were that many ways to do it:D

---

### Post by cairnzi on 2009-03-08
im trying to boot from my usb drive which has the supergrub disk on it but my laptop says "disk error press any key to reboot" any ideas whats the matter with it? cheers.

---

### Post by tracerbullet on 2009-03-08
Sounds like you messed up the GUI in GRUB.

Did you back up the files you edited before you messed with them? This is normally the most important step of editing any file that plays a part in running your computer.

If you did, then you can use the GRUB console (this is when you see "grub>" printed on the screen, and you can type commands) to remove the messed up file and replace it with your backup.

I'll leave it to someone else to post the exact commands to type.

---

### Post by cairnzi on 2009-03-08
@tracerbullet, not really sure if it was backed up, but hopefully somebody will have an idea, but if all else fails will just boot from livecd tommorow, cheers.

---

### Post by melrokz on 2009-03-08
Try typing:> bootat the grub> prompt. What happens?

---

### Post by tracerbullet on 2009-03-08
Well if you're not particularly attached to whatever was in your grub files, you could boot from a live CD and do a manual install of grub on the hard drive in question.

This can be accomplished in a few easy steps. I'm sorry I can't be of any more help concerning specifics. :(

---

### Post by cairnzi on 2009-03-08
@melrokz nothing much really, just the grub> prompt and nothing else?

---

### Post by cairnzi on 2009-03-08
ive been typing in some random comands and when i type in "boot" itsays "kernel must be loaded before booting" dont no if this any help or not?

---

### Post by sandyd on 2009-03-08
> **cairnzi said:**
> ive been typing in some random comands and when i type in "boot" itsays "kernel must be loaded before booting" dont no if this any help or not?
can you post menu.lst here while booting from your livecd (when you can use it i mean)
l
if you do, maybe it can be corrected, having a small typo in the file isn't really the reason to reinstall


OR (not recommended, use as a last chance thing)

since your going to reinstall anyways...........

boot livecd


RENAME the menu.lst file in the /boot/grub folder of your had disk

type this in terminal
```

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)

```

does that do anything?

---

### Post by ranch hand on 2009-03-08
I would put in your live cd and go to terminal and type
```

sudo grub

grub> find /boot/grub/stage1

```

If that returns with a (hd0,?) where ? is the partition number, you can easily fix this.

---

### Post by cairnzi on 2009-03-08
cheers for the replys guys, will try this tommorow when  get home, many thanks

---

### Post by presence1960 on 2009-03-08
> **cairnzi said:**
> hi people, i wa messing round with my new kubuntu 8.10 and have really screwed up the boot, when i boot al i get is. [COLOR="#000000"][minimal bash-like line editing is supported. for the first word, tab lists possible command completion. anywhere else tab lists the possible completions of a device/filename. ] grub>[/COLOR]

can some kind person please assist in telling me what silly thing i have done and how if possible to sort it? ps. i do not have access to my live cd until tommorow so hoping that there is a way to fix without it, many thanks from a daft newbie:(

Pop in the live CD and try restoring grub :
> 
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition nr is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

---

### Post by presence1960 on 2009-03-08
> **presence1960 said:**
> Pop in the live CD and try restoring grub :

After you get your OS running again make a backup copy of grub. Open terminal and cd to grub directory and enter in terminal

> sudo cp menu.lst menu.lst-backup

This way you have a copy of your working grub menu. If anything goes wrong with it you can use the live CD to compare the 2 copies and make necessary adjustments.

---

### Post by ranch hand on 2009-03-08
An other good thing to do, once grub is restored, is leave the 3 second delay there.  If some thing is wrong and you want to use the other options on the menu, you need that time.

If you just hit enter when the menu comes up it will boot then.

I don't have a 3 second delay.  I don't have less than three OS intallations on any drive.  I have a 10 second delay on 2 and on an external I have it set for 100.  I just find the one I want and hit enter.

---

### Post by cairnzi on 2009-03-09
@ all who helped cheers, my laptop is now working fine and dandy, will be leaving the 3 countdown alone from now on me thinks and having a good read of the begginers guides, again many thanks.:D ps, where has the option gone to mark the thread as solved? its not in the thread tools drop down menu anymore? cheers.

---

### Post by Eldera on 2009-03-09
[post]4527051[/post]

---

### Post by cairnzi on 2009-03-09
@Eldera cheers.

---

