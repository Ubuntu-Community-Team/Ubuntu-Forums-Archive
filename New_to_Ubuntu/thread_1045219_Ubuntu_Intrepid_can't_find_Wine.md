---
title: "Ubuntu Intrepid can't find Wine"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Peterfc on 2009-01-20
Hi 

Just install Wine by using Synaptic Package Manager. I then installed Windows Photo Story 3. Looked in Applications and didn't find wine. I then rebooted and after reboot i still can't find Wine. Their was an update of Wine in the last few days so i think i must have the latest Wine installed.

---

### Post by stderr on 2009-01-20
Hi. 

If you open up a terminal (Applications -> Accessories -> Terminal) and run this:

```
ls -l /usr/bin/wine
```

you should get a response something like this:

```
ace@ace1:~$ ls -l /usr/bin/wine
-rwxr-xr-x 1 root root 5496 2008-10-27 01:38 /usr/bin/wine
```

showing your wine executable. If you don't get that line, run this:

```
sudo dpkg -l wine
```

which will show if wine is installed or not. 

```
ace@ace1:~$ sudo dpkg -l wine
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  wine           1.0.1-0ubuntu2 Microsoft Windows Compatibility Layer (Binar
```

This is mine. The "ii" on the left tells us it's successfully installed.

You should have a menu entry under Applications -> Wine -> ..., if not I'm not sure why you don't. You could try uninstalling and reinstalling it, but I'm not sure I'd bother.

Your virtual Windows environment by default actually resides in your home directory (represented by a tilde ~) in a directory called .wine. So, you can launch applications manually... just like in Winblows.

```
nautilus .wine/drive_c/Program\ Files/
```

That will start the nautilus file manager in your Program Files directory. You should be able to navigate to where the application is installed and launch it (it should default to being launched with wine). It it doesn't, try right clicking and launching with wine.

If you're struggling, you can try to launch it via the command line.

```
wine .wine/drive_c/Program\ Files/My\ Application/myfile.exe
```

If you get confused over when you need a backslash and when you don't (the backslash is an escape character, and is needed before spaces or special characters) you can just hit tab and let it autocomplete the rest (up to where it needs more input).

We can add any of these to the menu manually... by right clicking the menu and selecting Edit Menu, and creating a new item with the command, say,

wine ~/.wine/drive_c/Program\ Files/......

---

