---
title: "Make a .sh shell script from a .bat"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by SPARTAN-118 on 2009-07-27
Hi all,

I was trying to run a .bat file that inserts ROMs (Read Only Media; aka "backups" for games) into an NES emulator.

However, the file is for Windows.

Is there a way to make a script that does the same thing the batch file does?

Here is the .bat file viewed from gedit:

@nesds arm9.bin 
@ndstool -c nesDS.nds -7 arm7.bin -9 nesds.ds.gba -r9 0x2000000 -r7 0x37f8000 -b icon.bmp "nesDS"

The bat file is "make_nds.bat"; it is for the NES Emulator nesDS, and executes a command that creates a .nds file (the NES emulator) and inserts the ROMs (the NES games) into the .nds file.

I don't really like dual-booting, but, since I have only 1 computer (that is incapable of utilizing a Virtual Machine), unless I can run this kind of stuff, I have no choice but to reboot into slow, agonizing Windows Vista. :(

SPARTAN-118

---

### Post by earthpigg on 2009-07-28
hi,

i am unfamiliar with ndstool and nesds, however...

...make an empty text file, make the first line #!/bin/bash (pronounced crunch bang bin bash), and then every subsequent line a command.

example:
open a terminal.

```
nano test-script
```
make the first line #!/bin/bash
2nd line
```
echo hello world
```

so the entire thing is:
```
#!/bin/bash
echo hello world
```

ctrl+x to close the text editor, press 'y' when it asks if you want to save.

then, to run it:

```
sh test-script
```
should give you:
```
ep@chris-laptop:~$ sh test-script
hello world
ep@chris-laptop:~$ 
```


you can put any acceptable commands you want in there, and they will run in order.

---

### Post by lykwydchykyn on 2009-07-28
Looks to me like this file basically runs a couple of programs, which I assume accompany it.  I'm assuming also that those programs are compiled to run on Windows, and thus will not run on Linux.

So in short, no.

---

### Post by doorknob60 on 2009-07-28
Try dosbox (might work, depending on whether or not the programs it wants to run are for windows or for DOS) or wine with wineconsole. Or try to find something else that does the same thig with Linux, you can probably find it out there somewhere.

---

### Post by SPARTAN-118 on 2009-07-28
Okay, thanks for your suggestions, just let me clear up a few things:

1. The programs that the script runs do come with it.
2. I can't use them to accomplish what I need to do because running the programs individually creates a .gba or .gb file, used with Slot-2 devices, such as GBA Flash Card.

Therefore, you need the script to run in order to create a .nds file.

earthpigg, do you suggest I create an empty shell script and copy down the commands?
I don't think that'll work, since they are Windows commands, not Terminal commands.

Judging by the way the commands are set up, it seems it should be easy to accomplish the tasks this script executes by creating a short Linux shell script.

Anybody know what the Windows commands mean, and if you can make Linux interpret them? If not, then is there a command equivalent to the one that cannot be interpreted?

Thanks,
SPARTAN-118

Looks like I might have to boot into Windows, after all.

---

### Post by SPARTAN-118 on 2009-07-28
> **doorknob60 said:**
> Try dosbox (might work, depending on whether or not the programs it wants to run are for windows or for DOS) or wine with wineconsole. Or try to find something else that does the same thig with Linux, you can probably find it out there somewhere.

No go, doorknob60, the programs are for Windows, not DOS (they are for Win2k+).
DOS is before Win2k, and I highly doubt these programs would work on a '98.

Any other suggestions for emulating Windows w/o running a Virtual Machine?
And where do you get wineconsole, anyway? What exactly does it do? Can it run Windows .bat files?

---

