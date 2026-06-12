---
title: "true.combat.elite_0.49-english.run"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by aparolin on 2009-12-22
i downloaded "true.combat.elite_0.49-english.run" file (453.3mb) and it is located in desktop.  i went to the file properties/permission and checked box to allow executing program.

"username"@oem-desktop:~$ sudo sh ./true.combat.elite_0.49-english.run
sh: Can't open ./true.combat.elite_0.49-english.run

what am i doing wrong???

thanx for yur help...

---

### Post by howefield on 2009-12-22
Navigate to the desktop before running the install command.

```
cd Desktop
```

---

### Post by aparolin on 2009-12-22
this is what happens---

aparolin@oem-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory

---

### Post by howefield on 2009-12-22
Linux is case sensitive, I wrote

```
cd Desktop
```

---

### Post by aparolin on 2009-12-22
ahhhh

did not know that;

i will give it a try...

srry for my ignorance...

---

### Post by aparolin on 2009-12-22
now it says this;
am i cursed???

aparolin@oem-desktop:~$ cd Desktop
aparolin@oem-desktop:~/Desktop$ sudo sh ./true.combat.elite_0.49-english.run
[sudo] password for aparolin: 
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit [http://www.liflg.org](http://www.liflg.org)
Searching Return to Castle Wolfenstein: Enemy Territory....
Could not find Return to Castle Wolfenstein: Enemy Territory
aparolin@oem-desktop:~/Desktop$

---

### Post by SlickRick on 2009-12-22
looks to me that you need Return to Castle Wolfenstein: Enemy Territory installed. Do you have it installed?

---

### Post by aparolin on 2009-12-22
i know; it doesnt make sense;
the file says true combat elite... 

back to the drawing board (start over?)

i dont have Castle Wolfenstein: Enemy Territory; but i would like to have it

---

### Post by Seq on 2009-12-22
> **aparolin said:**
> i know; it doesnt make sense;
the file says true combat elite... 

back to the drawing board (start over?)

i dont have Castle Wolfenstein: Enemy Territory; but i would like to have it

True Combat Elite is a mod for Enemy Territory. So you need ET installed first. The [True Combat Elite Install Instructions]("http://www.truecombatelite.com/tce.php?page=support#installation") cover this.

---

### Post by aparolin on 2009-12-22
wow; 

do i have egg on my face.. (i sqrewed up)

my apologies to all;

i should do better research...

again
thanx for your help

---

### Post by Seq on 2009-12-22
> **aparolin said:**
> wow; 

do i have egg on my face.. (i sqrewed up)

my apologies to all;

i should do better research...

again
thanx for your help

It happens to all of us. :)

---

### Post by SlickRick on 2009-12-22
looks like you can download enemy territory from the [_download page_]("http://www.truecombatelite.com/tce.php?page=downloads"). Just click on tux and all four files needed are there.

---

### Post by aparolin on 2009-12-22
greetings to all again;

i was all pumped up to get castle wolfenstein up and running.
but i see; not so easy.
after downloading "et-linux-2.55.x86.run", this was my result...


aparolin@oem-desktop:~/Desktop$ sudo sh ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/aparolin/.setup5916: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1


bummer;
i am guessing a number of issues will have to be addressed... 
i am running intel pentium r (d) 2.8ghz, so i know i have the power, but what else?
what to do?

---

### Post by aparolin on 2009-12-22
ok got the installer to work with:

sudo apt-get install libgtk1.2
when i run the program the resolution changes to 800x600, then this message:

aparolin@oem-desktop:~$ et
ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/aparolin/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
X Error of failed request: BadMatch (invalid parameter attributes)
  Major opcode of failed request: 1
  Minor opcode of failed request: 0
  Serial number of failed request: 41
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 42
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 18
  Minor opcode of failed request: 0
  Serial number of failed request: 43
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 8
  Minor opcode of failed request: 0
  Serial number of failed request: 44
X Error of failed request: BadWindow (invalid Window parameter)
  Major opcode of failed request: 12
  Minor opcode of failed request: 0
  Serial number of failed request: 45
X Error of failed request: BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request: 136
  Minor opcode of failed request: 7
  Serial number of failed request: 50
X Error of failed request: BadValue (integer parameter out of range for operation)
  Major opcode of failed request: 154
  Minor opcode of failed request: 26
  Serial number of failed request: 50
Received signal 11, exiting...
Segmentation fault

i prefer 1024x768 resolution.
do i need a joystick??  i would like to use the mouse...

stumped...now

---

