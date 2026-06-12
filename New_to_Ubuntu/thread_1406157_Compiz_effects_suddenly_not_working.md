---
title: "Compiz effects suddenly not working"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by raequin on 2010-02-13
I do not really understand what goes on with the updates; just that sometimes I have to delete header files or something in order for Grub to still start XP by default, and that I download and install every update brought up by the Automatic Updates manager.

So I guess a recent update has jacked up my settings.  I often use Compiz negative effect (see [this still unsolved thread]("http://ubuntuforums.org/showthread.php?t=1352066")) as well as whatever effect it is that allows you to assign windows to different zones of the display using keyboard shortcuts.  Anyway, today that stuff is not working anymore.

I use these things a lot so your help will be greatly appreciated (as always).  Also of note, when I started using the computer today some sound effects were enabled (I had previously set it for "none" sounds), and I had four desktops instead of two like usual.

Thanks.

---

### Post by Shpongle on 2010-02-13
is any compiz runing at all ? , what happens when you try 
compiz --replace , also you can try a previous kernel if you think it was an update that might have done it.its a good idea to keep the previous kernal installed for events like this. you can select the kernal at boot on the grub menu screen

---

### Post by raequin on 2010-02-13
Here's the results:

```
matt@phoenix-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator
[ERROR]: Option "command0" already defined

```
...
```
[ERROR]: Option "maximize_effect" already defined
^C*** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x0000000002becbd0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f79daf2add6]
/lib/libc.so.6[0x7f79daf2c8a2]
/lib/libc.so.6(cfree+0x6c)[0x7f79daf2f74c]
/usr/lib/libGL.so.1[0x7f79dcf21038]
======= Memory map: ========
00400000-0043c000 r-xp 00000000 08:05 10661           
```
You can see in there where I hit ctrl+c because it was just sitting on that last error line (there were a bunch of error lines above it for things already defined).

Also, wrt the kernels, I thought that might help, but I have the same issue when I start with older versions in Grub.

Thanks.  I hope we can get this resolved because I sure do find negative and the window arranger useful.  It is one of my favorite things about Ubuntu, though I would still use it anyway without those.

---

### Post by raequin on 2010-02-13
Yeah, I don't think Compiz is running at all.  None of the other effects (e.g. wobbly windows) are going either.

edit: I just set system-->preferences-->appearance-->visual effects to "extra", and now wobbly windows is back, and negative works, but I had to enable "grid" manually again.  Don't know why these things got disabled, but all is good now.

Thanks.

---

