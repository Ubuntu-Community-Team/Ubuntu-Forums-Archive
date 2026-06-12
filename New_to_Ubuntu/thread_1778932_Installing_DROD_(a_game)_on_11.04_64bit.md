---
title: "Installing DROD (a game) on 11.04 64bit"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by Blatm on 2011-06-09
Hi,

I just got my first Linux computer and I'd like to install DROD: Architect's Edition (from forum.caravelgames.com/downloads.php ) on it.

I downloaded the Linux file (.run file), ran it, and my terminal looked like

```
[FONT=monospace]
[/FONT]blatm@Bob:~/Downloads$ sh DRODAESetup-1.6.7.run
Verifying archive integrity... All good.
Uncompressing DROD: Architects' Edition........................................................................................................................................................................................................................... 

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gdk-WARNING **: locale not supported by C library

```An installation window popped up, I chose a directory for the stuff and a directory for the symbolic links, and now I have a /drod-ae directory.

In it is:
```

blatm@Bob:~/drod-ae$ ls -l
total 24
-rw-r--r-- 1 blatm blatm 2813 2011-06-06 19:06 Caravel DROD Licensing Overview.txt
drwxr-xr-x 8 blatm blatm 4096 2011-06-06 19:06 Data
-rwxr-xr-x 1 blatm blatm  355 2011-06-06 19:06 drod-ae
-r--r--r-- 1 blatm blatm 1327 2011-06-06 19:06 drodae.xpm
drwxr-xr-x 2 blatm blatm 4096 2011-06-06 19:06 Libs
-rwxr-xr-x 1 blatm blatm 1285 2011-06-06 19:06 uninstall

```I think drod-ae is the relevant executable, though I had to chmod +x drod-ae.

When I try to run it, I get

```

blatm@Bob:~/drod-ae$ ./drod-ae
./drod-ae: 16: /home/blatm/drod-ae/drod-ae.bin: not found

```I can also try and run it from my folder browser. I get a window asking me "Do you want to run "drod-ae", or display its contents? "drod-ae" is an executable text file."  and giving me the options Run in Terminal/Display/Cancel/Run. Neither  Run does anything, and Display opens the file in a text editor:
> 

#!/bin/sh

DRODAE_HOME="/home/blatm/drod-ae"

if test "x$LD_LIBRARY_PATH" = "x"; then
    LD_LIBRARY_PATH="$DRODAE_HOME/Libs"
else
    LD_LIBRARY_PATH="$DRODAE_HOME/Libs:$LD_LIBRARY_PATH"
fi

DROD_1_6_RES_PATH="$DRODAE_HOME/Data"
DROD_1_6_DAT_PATH="$DRODAE_HOME/Data"

export LD_LIBRARY_PATH DROD_1_6_RES_PATH DROD_1_6_DAT_PATH

"$DRODAE_HOME/drod-ae.bin" "$@"
I'm very new to Linux so I don't really know what to do. Any help would be much appreciated.

I made essentially the same post on the DROD forums: forum.caravelgames.com/viewtopic.php?TopicID=31841 . There's a bit of back and forth there which might help understand the situation better. I don't have enough experience to know what kind of information is helpful, so please just ask for anything I failed to mention.

---

### Post by KIAaze on 2011-06-09
The problem is quite simple: The developers forgot to include the binary ("drod-ae.bin") in the installer.
"drod-ae" itself is just a wrapper script to make sure the binary will run correctly by setting up some environment variables.

You should report the problem to them by using one of their mail addresses: [http://caravelgames.com/Articles/Contact.html](http://caravelgames.com/Articles/Contact.html)

P.S.: I tried the "DROD RPG: Tendry's Tale" demo and it installed and ran without any problems, despite me using 64-bit (but I already had ia32-libs installed which is probably necessary). So, assuming that the game engine hasn't changed much between versions, I think that once the developers are made aware of the missing binary, it will be quickly fixed.

I heard about DROD before. But this is the first time I actually tried it. Looks quite fun. :)

edit: Actually, the source code is available! :)
[http://forum.caravelgames.com/viewsitepage.php?id=98165](http://forum.caravelgames.com/viewsitepage.php?id=98165)
So it might be possible to compile the binary yourself, or use one from the other installers. I'll try it eventually later.
My first attempt of reusing the binary from DROD RPG for AE failed.

---

### Post by Blatm on 2011-06-09
Thank you very much for the great reply. I've emailed bugs@caravelgames.

---

