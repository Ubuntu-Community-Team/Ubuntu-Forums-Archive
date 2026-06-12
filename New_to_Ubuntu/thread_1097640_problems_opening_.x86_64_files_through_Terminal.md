---
title: "problems opening .x86_64 files through Terminal"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Runefoger on 2009-03-16
i have had ubuntu 7.10 (gutsy gibbon) for a while now, but I have never really needed to use Terminal for much.

i have been using Wine to install games as well, but i recently downloaded OpenArena (it's like Quake3:Arena)... problem is, it has file types for Windows, Linux and Mac. since Wine is laggy, i want to run the Linux *.x86_64 file, except i have no idea how to on terminal, nor whether the file needs installing 1st too... (in the past, i have used the Add/Remove tool, which auto-installs the files it finds, but this was a download from the internet)

any help or instruction would be much appreciated.

also, the location of the file is in the folder:
/home/rob/Documents/Games/openarena-0.8.1
if that helps

---

### Post by taurus on 2009-03-16
What's the output of this command from a terminal?

```
ls -la ~/Documents/Games/openarena-0.8.1
```

---

### Post by Runefoger on 2009-03-16
erm... this:

total 14152
drwxr-xr-x 6 rob rob    4096 2009-03-16 11:16 .
drwxr-xr-x 7 rob rob    4096 2009-03-16 11:15 ..
drwxr-xr-x 2 rob rob    4096 2008-10-31 09:49 baseoa
-rwxrwx--- 1 rob rob   10022 2008-10-31 09:53 CHANGES
-rwxrwx--- 1 rob rob   17992 2006-11-10 16:50 COPYING
-rwxrwx--- 1 rob rob    2846 2008-10-31 08:45 CREDITS
drwxr-xr-x 2 rob rob    4096 2009-03-16 11:17 legacy
-rwxrwx--- 1 rob rob   15872 2006-11-26 09:25 libogg-0.dll
-rwxrwx--- 1 rob rob  157696 2006-11-26 09:25 libvorbis-0.dll
-rwxrwx--- 1 rob rob   29184 2006-11-26 09:25 libvorbisfile-3.dll
-rwxrwx--- 1 rob rob     486 2008-04-20 02:56 LINUXNOTES
drwxr-xr-x 2 rob rob    4096 2008-10-31 09:51 missionpack
-rwxrwx--- 1 rob rob 1147324 2008-10-20 22:36 oa_ded.exe
-rwxrwx--- 1 rob rob  772090 2008-10-20 22:36 oa_ded.i386
-rwxrwx--- 1 rob rob  948638 2008-10-20 22:32 oa_ded.x86_64
drwxr-xr-x 3 rob rob    4096 2008-10-22 09:44 OpenArena.app
-rwxrwx--- 1 rob rob 2893146 2008-10-20 13:40 openarena-deprecated.exe
-rwxrwx--- 1 rob rob 2906778 2008-10-20 22:37 openarena.exe
-rwxrwx--- 1 rob rob 1609188 2008-10-20 22:36 openarena.i386
-rwxrwx--- 1 rob rob 2200655 2008-10-20 22:33 openarena.x86_64
-rwxrwx--- 1 rob rob    4063 2008-10-31 09:54 README
-rwxrwx--- 1 rob rob 1673738 2008-08-08 11:13 SDL.dll
-rw-r--r-- 1 rob rob     213 2009-03-16 11:16 stderr.txt
-rwxrwx--- 1 rob rob     425 2008-08-05 11:05 WENEED

---

### Post by taurus on 2009-03-16
Have a look at LINUXNOTES & README to see what they say, especially the LINUXNOTES.  Bet it will tell you what you need to do and how to start the game.

```
cd ~/Documents/Games/openarena-0.8.1
more LINUXNOTES
```
Hit the space bar for the next 24 lines.

---

### Post by Runefoger on 2009-03-16
i already read LINUXNOTES, this is what it says:

"If it doesn't start up at all, you may need libopenal installed.

If It still doesn't start up at all, you may need libvorbis installed. 

If it STILL doesn't start up at all, you may not have hardware OpenGL accellerat
ion. *This is absolutely required*.  Install appropriate video drivers for your 
video hardware.  You can still attempt to play the game in software mode by addi
ng +r_allowSoftwareGL 1, but that's stupid and for 1fps-loving insane peoples. D
don't try this at all."

i am not sure how to find if i have libopenal or lobvorbis on my computer. 

As for the README file, it is simply a Q&A for character models and such in this version.

---

### Post by taurus on 2009-03-16
So you are running Ubuntu x86_64, right?

See if you have all the necessary libraries to run it.  What's the output of this command?

```
ldd openarena.x86_64
```

---

### Post by Runefoger on 2009-03-16
"no such file or directory"

...

and i don't know if i am running Ubuntu x86_64... i thought it was just a file extension.

---

### Post by Runefoger on 2009-03-16
i typed "ldd /home/rob/Documents/Games/openarena-0.8.1/openarena.x86_64" and it instead said "not a dynamic executable"

---

### Post by taurus on 2009-03-16
First, find out which arch you are running.

```
uname -m
```
i686 = 32bit
x86_64 = 64bit

Second, you need to be in that directory first, openarena-0.8.1, unless you use the whole/complete path.

```
cd ~/Documents/Games/openarena-0.8.1
ldd openarena.x86_64
```

---

### Post by dgoosens on 2009-03-16
is there a reason for not installing it with Synaptics ?
it is in the repository I believe...

---

### Post by Runefoger on 2009-03-16
... synaptics? haha. i have never used it before, so i didn't know what it did.

as for Taurus' questions, it is a i686, and for the directory change, it had the same result as me using the complete path; "Not a Dynamic Executable"

---

### Post by Runefoger on 2009-03-16
right, i think i am doing this right...

in synaptic, i have chosen to add a downloaded package... but i don't know what the extension for a package is, and when i found where the openarena.x86_64 file was, the contents of the folder were greyed out, so i couldn't select it...

---

### Post by taurus on 2009-03-16
> **Runefoger said:**
> right, i think i am doing this right...

in synaptic, i have chosen to add a downloaded package... but i don't know what the extension for a package is, and when i found where the openarena.x86_64 file was, the contents of the folder were greyed out, so i couldn't select it...

If you are running i686, you cannot use x86_64 since that is for 64bit.  Therefore you have to try to i386 version.

```
cd ~/Documents/Games/openarena-0.8.1
ldd openarena.i386
```

---

### Post by Runefoger on 2009-03-16
i didnt even need to use code, once you told me that, i double clicked the i686 file and it opened straight away... this seems like a wasted time now.

still, thanks a tonne for your help anyway, at least i understand my system a little better now.

---

