---
title: "GNOME MPlayer runs better without GNOME?"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by liatodua on 2011-02-16
Hi,

I have an old IBM T30 laptop. I tried Ubuntu and had lots of problems with it. One was GNOME MPlayer. It was smashing the picture and at some point was losing sound and then just stop. Many people around here complain about this player so I decided it is just not-really-a-good-one and uninstalled it and installed VLC. Became a bit better but still crashing often. I was given a very complicated advise how to do improve sth with my old and not properly supported sound card. I did it and comp crashed completely (may be I made some mistake. Do not know)

The issue is that now I have Lubuntu and the GNOME Player performs just fine! No soundcard-videocard-whatever issues!

The only strange thing is that every time I try to watch a movie it shows a message:"Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory". But I just close the message and the movie runs  fine. 

I thought I should tell this to the gurus here. May be it is useful. And what the hell this error message means? Should I care? Can I get rid of it?

---

### Post by SteveDee on 2011-02-16
> **liatodua said:**
> ...The only strange thing is that every time I try to watch a movie it shows a message:"Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory". But I just close the message and the movie runs  fine....

The issue is caused by Gnome Mplayer attempting to use the default VDPAU, which does not exists.
To remove the message:-
 - launch Gnome Mplayer,
 - select Edit->Preference.
 - Enter a "Video Output" option that is supported on your system

You will probably find that "xv" works OK (although on the Compaq D510 I have to use "x11").

---

### Post by 3rdalbum on 2011-02-16
Gnome Mplayer works fine in Gnome; but on older hardware or for high resolution video you might want to turn off Compiz (visual effects window manager):

```
metacity --replace
```

To turn it back on again:

```
compiz --replace
```

Note that this will do nothing useful in Lubuntu; it doesn't use the Compiz window manager.

---

### Post by liatodua on 2011-02-16
> **3rdalbum said:**
> Gnome Mplayer works fine in Gnome; but on older hardware or for high resolution video you might want to turn off Compiz (visual effects window manager):

```
metacity --replace
```

To turn it back on again:

```
compiz --replace
```

Note that this will do nothing useful in Lubuntu; it doesn't use the Compiz window manager.

I tried ```
metacity --replace
```  but received: 

The program 'metacity' is currently not installed.  You can install it by typing:
sudo apt-get install metacity

---

### Post by liatodua on 2011-02-16
> **SteveDee said:**
> The issue is caused by Gnome Mplayer attempting to use the default VDPAU, which does not exists.
To remove the message:-
 - launch Gnome Mplayer,
 - select Edit->Preference.
 - Enter a "Video Output" option that is supported on your system

You will probably find that "xv" works OK (although on the Compaq D510 I have to use "x11").

Done. I selected "xv". Just fine. The error message disappeared. Thanks

---

### Post by liatodua on 2011-02-18
> **3rdalbum said:**
> Gnome Mplayer works fine in Gnome; but on older hardware or for high resolution video you might want to turn off Compiz (visual effects window manager):

```
metacity --replace
```

To turn it back on again:

```
compiz --replace
```

Note that this will do nothing useful in Lubuntu; it doesn't use the Compiz window manager.

It seens I do not have any of those programs installed:

```
liatodua@LT:~$ metacity --replace
The program 'metacity' is currently not installed.  You can install it by typing:
sudo apt-get install metacity
liatodua@LT:~$ compiz --replace
The program 'compiz' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-core
```

---

