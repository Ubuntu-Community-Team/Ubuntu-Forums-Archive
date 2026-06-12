---
title: "Can't play DVDS"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-06-13
I am trying to play a DVD I rented, but it's not playing. I tried playing it in the default movie player and it says "Can't read from source." Tried VLC, nothing happens. And yes, I do have libdvdread4 installed. Any help please?

---

### Post by coolbrook on 2010-06-13
I refer to this any time I do a clean or new install.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Consider running through it (or again if you have.)  It doesn't take long at all.  It works for me every time.

---

### Post by 73ckn797 on 2010-06-13
Follow this:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Already mentioned in the link provided UnknownFear. Just the direct path to it.

---

### Post by UnknownFear on 2010-06-14
> **73ckn797 said:**
> Follow this:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Already mentioned in the link provided UnknownFear. Just the direct path to it.

I tried doing it, and I think I did cause I have libdvdread installed, but still nothing :confused:

---

### Post by ddrichardson on 2010-06-14
If you run totem from a command line, then load the DVD and let us know what errors appear in the terminal that might point the way.

---

### Post by UnknownFear on 2010-06-14
> **ddrichardson said:**
> If you run totem from a command line, then load the DVD and let us know what errors appear in the terminal that might point the way.

***Totem: Terminal***
```
unknownfear@ubuntu:~$ totem
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: SSS_DARKSIDE
libdvdnav: DVD Serial Number: 3b4f9bce
libdvdnav: DVD Title (Alternative): SSS_DARKSIDE
libdvdnav: Unable to find map file '/home/unknownfear/.dvdnav/SSS_DARKSIDE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
************************************************
**                                            **
**  No css library available. See             **
**  /usr/share/doc/libdvdread4/README.Debian  **
**  for more information.                     **
**                                            **
************************************************
libdvdnav: DVD Title: SSS_DARKSIDE
libdvdnav: DVD Serial Number: 3b4f9bce
libdvdnav: DVD Title (Alternative): SSS_DARKSIDE
libdvdnav: Unable to find map file '/home/unknownfear/.dvdnav/SSS_DARKSIDE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
** Message: Error: Could not read from resource.
resindvdsrc.c(1100): rsn_dvdsrc_step (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Error reading NAV packet.

```

---

### Post by ddrichardson on 2010-06-14
```
sudo apt-get install libdvdcss2
```

---

### Post by UnknownFear on 2010-06-14
> **ddrichardson said:**
> ```
sudo apt-get install libdvdcss2
```

That did it, thanks a lot ddrichardson.

---

### Post by ddrichardson on 2010-06-14
No worries - if you have problems with anything in the future, try running it from the console - the output will always be helpful in diagnosing the problem.

---

### Post by UnknownFear on 2010-06-14
> **ddrichardson said:**
> No worries - if you have problems with anything in the future, try running it from the console - the output will always be helpful in diagnosing the problem.

Thanks for the tip, will definitely run a program from the console if it doesn't seem to work, or gives me errors.

---

