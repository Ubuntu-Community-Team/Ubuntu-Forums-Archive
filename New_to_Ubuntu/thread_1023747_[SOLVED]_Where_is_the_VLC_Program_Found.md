---
title: "[SOLVED] Where is the VLC Program Found?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Hotel California on 2008-12-28
Just installed 8.04 and have been trying to use the built-in Totem DVD player, but am having some issues (can't fast forward and very low volume).

I'd like to try the VLC program, but do not see where to find it on any of my menus.  It looks like it's installed when I search on the Synaptic Package Manager.  Where is that sucker hiding?  Can someone direct me?

Thx.

---

### Post by drs305 on 2008-12-28
Applications > Sound & Video is the menu location.

You can also start it with:
```
vlc
*or*
/usr/bin/vlc
```

For command line entries, you can normally find the location of the run command with:
```

which <appname>

```
For example:
```

~$ which vlc
/usr/bin/vlc

```

---

### Post by wolfen69 on 2008-12-28
go to system>preferences>main menu and add to the menus there.

---

### Post by Hotel California on 2008-12-28
Ooops...says it is not installed on my system.  I thought it installed by default.   I'm installing it now.  This should help, I'd imagine.  Thank you.

---

### Post by joe_pacific on 2008-12-28
I didn't know about the "which" command, thank you for that. 

> **drs305 said:**
> Applications > Sound & Video is the menu location.

You can also start it with:
```
vlc
*or*
/usr/bin/vlc
```

For command line entries, you can normally find the location of the run command with:
```

which <appname>

```
For example:
```

~$ which vlc
/usr/bin/vlc

```

---

### Post by Hotel California on 2008-12-28
Thanks all.  It's working now.  Just downloaded and installed it from the Package Manager.

---

