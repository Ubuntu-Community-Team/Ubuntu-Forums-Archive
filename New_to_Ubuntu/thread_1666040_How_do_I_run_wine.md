---
title: "How do I run wine?"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by Veltia on 2011-01-13
A few months ago, I reset my calculator (TI-89 Titanium) during which a few programs was installed. One of these called "Stat list".
Now my maths teacher asked me to re-install "Stat list" on my calculator, which I want to comply, however having switched to Ubuntu in the mean time presents a bigger challenge, seeing as in order to be able to download those things I need Windows. No biggie, I just download and install Wine through the Ubuntu Software Center. As said as done...

...how do I run wine so that it makes an actual emulation of Windows?

Thanks in advance. I'm fairly new to Ubuntu and I like it so far.

EDIT: Never mind, got it to work now. I had to check "Emulate virtual desktop". Now I just need to find out how to download something from Wine Internet Exploder.

---

### Post by PunkLV on 2011-01-13
> actual emulation of Windows
That would be a Virtual Machine running windows, with all Cd-keys and other stuff.

If you want to run it on Ubuntu via Wine, then you should check [http://appdb.winehq.org/](http://appdb.winehq.org/) for your program in Supported list. If the program you need does not have some strictly-windows modules then it should run and install just fine by rightclicking installer "Open with Wine".

---

### Post by Vaphell on 2011-01-13
wine takes over when you execute .exe file (must be set to executable). You can also use terminal
```
wine /some/windows/program/to/run.exe
```

---

### Post by [Snc] on 2011-01-13
> **Veltia said:**
> A few months ago, I reset my calculator (TI-89 Titanium) during which a few programs was installed. One of these called "Stat list".
Now my maths teacher asked me to re-install "Stat list" on my calculator, which I want to comply, however having switched to Ubuntu in the mean time presents a bigger challenge, seeing as in order to be able to download those things I need Windows. No biggie, I just download and install Wine through the Ubuntu Software Center. As said as done...

...how do I run wine so that it makes an actual emulation of Windows?

Thanks in advance. I'm fairly new to Ubuntu and I like it so far.
note: **W**ine **I**s **N**ot an **E**mulator - it is "just" an API wrapper.

so wine just emulates basic and kernel APIs of windows, that means, that you can install and run windows programs (in my experience, if the program is "certified for windows *whatever") *so if the software doesn't do weird stuff, it will run.

once you installed wine, you can go to "Applications" -> "Wine" -> "configure wine"

and install/uninstall software for windows from there ... or just double click the MSI or setup executable

PS note also, that if weird stuff happens during install - crashes, setup just disappears, etc, move the installation file to the WINE C: folder, you can find it in the menu: "Applications" -> "Wine" -> "Browse C: drive"

---

### Post by mastablasta on 2011-01-13
have a look here:
[http://www.winehq.org/docs/wineusr-guide/index](http://www.winehq.org/docs/wineusr-guide/index)
 
Basically you wiuld type in terminal wine and then programme you wan to launch.
 
WINE is not and emulator, so don't expect MS Windows enviroment to pop up.

---

