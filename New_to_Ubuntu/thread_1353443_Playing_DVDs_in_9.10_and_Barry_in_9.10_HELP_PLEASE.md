---
title: "Playing DVDs in 9.10 and Barry in 9.10 HELP PLEASE"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Archie69 on 2009-12-12
Hi all,

Just installed 9.10 and that went pretty smoothly. So far so good. I was really pleased I didn't have to configure anything for video card or sound card which was a huge issue for me when I initially switched. Anyway off to my questions:

1. I tried to watch a DVD and I can't. I remember when I installed 8.04 I had to do some stuff in terminal so I could watch DVDs but I have no idea what it was. Does anyone know what I have to do and how to do it so I can watch DVDs with ease on my computer?

and 

2. I know Barry (the RIM Blackberry program) is in synaptic, but there are about 4 different options to pick from. Do I just install them all or are there certain ones that I have to install? Any ideas? The options are: barrybackup.gui, barrybackup-gui-dbg, opensync-plugin-barry-dbg, and several others.

Any takers? Thanks in advance

---

### Post by sandyd on 2009-12-12
> **Archie69 said:**
> Hi all,

Just installed 9.10 and that went pretty smoothly. So far so good. I was really pleased I didn't have to configure anything for video card or sound card which was a huge issue for me when I initially switched. Anyway off to my questions:

1. I tried to watch a DVD and I can't. I remember when I installed 8.04 I had to do some stuff in terminal so I could watch DVDs but I have no idea what it was. Does anyone know what I have to do and how to do it so I can watch DVDs with ease on my computer?

and 

2. I know Barry (the RIM Blackberry program) is in synaptic, but there are about 4 different options to pick from. Do I just install them all or are there certain ones that I have to install? Any ideas? The options are: barrybackup.gui, barrybackup-gui-dbg, opensync-plugin-barry-dbg, and several others.

Any takers? Thanks in advance
2. use barrybackup-gui
The rest are for debugging

3. you will need medibuntu enabled
install libdvdcss2 and libdvdread4

---

### Post by Archie69 on 2009-12-12
Thats awesome, do I install install libdvdcss2 and libdvdread4 via terminal (if so is it: sudo apt get libdvdcss2)??

Barry should be good. Thanks

---

### Post by sandyd on 2009-12-12
> **Archie69 said:**
> Thats awesome, do I install install libdvdcss2 and libdvdread4 via terminal (if so is it: sudo apt get libdvdcss2)??

Barry should be good. Thanks
doesnt matter.
through synaptic is ok too.

---

### Post by Archie69 on 2009-12-12
Also, would Barry be in a drop down menu (ie. applications, Accessories, etc) or will it open by default when I plug in my blackberry?

---

### Post by 3rdalbum on 2009-12-12
Ubuntu doesn't open programs (generally) when you plug devices in. Barry should appear in your Applications menu.

You need to enable the Medibuntu repository in order to install libdvdcss2 (or it can be installed by the terminal if you follow the directions in the Help program on Ubuntu).

You may also want to install VLC, it works better as a DVD player than Totem.

---

### Post by Synoc on 2009-12-12
> **Archie69 said:**
> Hi all,

Just installed 9.10 and that went pretty smoothly. So far so good. I was really pleased I didn't have to configure anything for video card or sound card which was a huge issue for me when I initially switched. Anyway off to my questions:

1. I tried to watch a DVD and I can't. I remember when I installed 8.04 I had to do some stuff in terminal so I could watch DVDs but I have no idea what it was. Does anyone know what I have to do and how to do it so I can watch DVDs with ease on my computer?


[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
I just posted about this too this should help

---

### Post by Archie69 on 2009-12-14
Thanks all. I got the DVDs to play without issue...so far at least. 

As for Barry, I installed barrybackup.gui however it isn't anywhere to be found in my APPLICATIONS menu. Am I missing something?

---

### Post by emiliec15 on 2009-12-14
If you can't find it, you can call it from the terminal with the command barrybackup

Again in the terminal type:

barrybackup

This should bring it up for you without any issues

---

### Post by Archie69 on 2009-12-14
Thank you to all.
And to all a good night.

---

### Post by running_rabbit07 on 2009-12-14
If you haven't tried it yet, go to System> Preferences> Main menu and search for it and enable it. Sometimes when I do an install I have to do that or log out and back in for programs to show.

:D

---

