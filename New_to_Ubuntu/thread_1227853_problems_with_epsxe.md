---
title: "problems with epsxe"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by nightingale42 on 2009-07-31
been messing around with this for several hours (tried to get a non-responsive pcsx to work and eventually gave up and went for epsxe and wound up having several issues with plugins). looking around a bit solved my first problem, but i can't quite work this one out.  there is a post in the archives with my error, but while it was solved, it glossed right over my problem -> [http://ubuntuforums.org/showthread.php?t=687336](http://ubuntuforums.org/showthread.php?t=687336)
i get that it is a video driver/graphic problem, what i don't get is how to fix it >_>

ran epsxe in terminal 
 * Running ePSXe emulator version 1.5.2.

(gui) file > run cdrom

 * Memory handlers init.
 * ePSXe: PSX BIOS loaded [/home/dragon/epsxe/bios/SCPH1001.BIN].
 * Init internal cdrom ... CD_Init: open of "bios/scph1001.bin" failed (2)
CD(0,2,16) read ioctl failed (9)
CD(169,6,32) read ioctl failed (9)
CD(169,6,33) read ioctl failed (9)
 * NTSC cdrom detected.
 * Init gpu[0][libgpu.so]
Gdk-ERROR **: GLXUnsupportedPrivateRequest
serial 40 error_code 162 request_code 143 minor_code 16
Missing shader extensions!

](*,)
can anyone help me? quite frustrated at this point

---

### Post by Alexander_Morozevich on 2009-08-01
I also get a similar error, here is:

 * Running ePSXe emulator version 1.6.0. 

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
 * Memory handlers init. 
 * ePSXe: PSX BIOS loaded [/usr/local/games/epsxe/bios//Dtlh3000.bin]. 
 * Loading ISO Format [BIN/IMG2352] ok
 * NTSC cdrom detected. 
 * Init gpu[0][libgpu.so] 
unknown chip id 0x9612, can't guess.
Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
  serial 64 error_code 9 request_code 55 minor_code 0

:confused:

---

### Post by nightingale42 on 2009-08-05
bump

---

### Post by nightingale42 on 2009-08-10
bump

---

### Post by charrah on 2009-10-18
Killing pulseaudio then running it as root works for me, or alternately setting LD_LIBRARY_PATH=/usr/lib/gtk-2.0/modules/ and then running as root for slightly more convenience.

EDIT: I meant to say that the above fixed the 'Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so' message and sound for me. For the other things, do you have all the prerequisite libraries installed?
```
+ libncurses.so.5
+ libdl.so.2
+ libXt.so.6
+ libz.so.1
+ libgtk-1.2.so.0
+ libgdk-1.2.so.0
+ libgmodule-1.2.so.0
+ libglib-1.2.so.0
+ libXi.so.6
+ libXext.so.6
+ libX11.so.6
+ libm.so.6
+ libc.so.6
+ libSM.so.6
+ libICE.so.6
+ /lib/ld-linux.so.2
```
Those are the alleged required libraries. If you know you have all those on your computer already (try the locate command) then I'm not sure what the trouble is.

---

