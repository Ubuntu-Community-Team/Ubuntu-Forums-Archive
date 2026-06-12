---
title: "dos emulator"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Dave Green on 2010-01-17
Fist day using LInux (ubuntu version 9.10). I want to run a dos program and need a dos emulator application but when I use ubuntu software centre I can not find one listed to download. Can anyone help?

---

### Post by forsaken_pariah on 2010-01-17
Open synaptic and search for dosbox.

---

### Post by lkraemer on 2010-01-17
[http://www.dosbox.com](http://www.dosbox.com) 
[http://dosbox.sourceforge.net/wiki](http://dosbox.sourceforge.net/wiki)

You will need to install Dosbox in Ubuntu by using Synaptics or apt-get.  The folder/subdirectory that contains your older DOS program (EXE, COM,
or BAT) will need to be copied to your Ubuntu /home/loginname folder.

This folder will be mounted as C: Drive in Dosbox so the EXE, COM or BAT
file can be executed.  To mount your C: drive, you will use the mount
command to mount the Linux folder as c and then change to Drive C:\> and
execute your old DOS Program.

As an example:
I had several recipes that were saved in C:\pw\2_LDK\Cookin on an
old Dos machine.  I copied the complete C:\pw folder to /home/larry/C:/.
Then I executed Dosbox from the Ubuntu menu
APPLICATIONS &#8594; SYSTEM TOOLS &#8594; dosbox

When the dosbox window opened I typed the following:
Z:\> mount c ~/C:       and the response was: Drive C is mounted as local Directory /home/larry/C:
Z:\>C:			and the response was:  C:\>
C:\>dir/p		gave a paged directory listing of ~/C:>
C:\>cd pw		and the pw window opened with the word processor running
C:\>pw			and now I have access to my old recipes.


The following commands can be used in dosbox
intro
intro mount
intro cdrom
intro special
help
help /all

Along with a lot of special commands that are shown on their help screens.
  
Now, lets get Sourcer from V-Communications running in Dosbox.  First we
need to copy the DOS subdirectory Sourcer_305 to the Linux folder C:.
This will copy all the files needed to run Sourcer version 3.05.
When the copy is complete, start Dosbox from the pulldown menu.
Then mount the folder as C: and do the following commands:
mount c ~/C:
C:
cd source~1
sr
(NOTE: Once mounted you don't need to repeat that command, just cd to the folder you need to access.)

To UNMOUNT C: use the following command:
mount -u c

Once again it works like a champ.

lk

---

### Post by baddog144 on 2010-01-17
I heartily recommend DOSBox. Works like a charm with most apps and games :)

---

### Post by lisati on 2010-01-17
There's also DOSemu.....

Both DOSBox & DOSEmu are available under "Add/Remove" in 9.04. (I don't currently have 9.10 on any of my machines, so can't check the software centre.)

---

