---
title: "Auto run wbar at session start"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by Warpnow on 2009-02-05
Where can I put the command to make it run?

tried rcS and rc.local neither seem to work.

---

### Post by swoody on 2009-02-05
It doesn't launch normally when you add it to System>Preferences>Sessions?

---

### Post by Warpnow on 2009-02-05
I'm running this on a beta operating system based on Ubuntu with XFCE. I need to know how to do it from the command line,

---

### Post by cardinals_fan on 2009-02-05
> **Warpnow said:**
> Where can I put the command to make it run?

tried rcS and rc.local neither seem to work.
Do **NOT** put it in the system startup files!

If you have Xfce, you should be able to use xfce4-autostart-editor.  Otherwise, I imagine the config file is in .config/xfce4/

---

### Post by spcwingo on 2009-02-05
Does it have a home/user/.config folder?  If so, create a folder named autostart in there and put in that a .desktop file to start wbar.  Mine looks like this:

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Wbar
Type=Application
Exec=/home/jonathan/.wbar.sh
Icon=
Terminal=false
StartupNotify=false
Hidden=false
GenericName=
GenericName[en_US]=
```

As you see I have it pointing to a script in my home folder.  It looks like this:

```
#!/bin/sh

(sleep 7s && wbar -bpress -above-desk -pos bottom -isize 50.0 -idist 12.0 -nanim 3.0 -zoomf 1.8 -jumpf 1.0 -balfa 85.0 -falfa 100.0) &
```

I also have my custom .wbar config file in my home directory.  By default wbar looks in your home folder first, then defaults back to the one named dot.wbar at /usr/share/wbar.  Let me know if this helps at all.

---

### Post by spcwingo on 2009-02-05
Just thought I would let you know that just I tried my above suggestion with Xubuntu 8.04 and it worked like a charm.  ;)

---

