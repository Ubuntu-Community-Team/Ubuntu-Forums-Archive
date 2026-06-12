---
title: "No program control at all"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Oathanvil on 2011-02-17
Everything has stopped working in UBUNTU! Any desktop Icon's already installed via "wine" will launch like World of warcraft as an example.

I cannot install ifranview using wine or any other new .exe files. irfranview is a simple picture handling software program a friend is already using in a wine install.

In fact I cannot even get "wine" to uninstall so I can try a fresh re-install after a system restart.

Any action by the end users gets me a working ubuntu mouse icon for 10 seconds then nothing at all happens.

no error messages no screen flicker nothing. 

I feel like I am sailing a brand new shiny ship with no rudder, all inputs are ignored but wow my desktop looks great.

Only thing that I can notice is application focus for Firefox refuses to open on the primary lcd and always opens on the lower res display even if i try to min/max it or ALT drag it back over to the primary display it refuses to remember where its supposed to open.

ok very frustrated I have no user control over the desktop or any applications.

---

### Post by ajgreeny on 2011-02-17
I have not bothered with wine seriously for a long time, but I know that to get irfanview to run you either need to copy from your windows install the dll file mfc42.dll, (at least that is what I think it is called) or use winetricks from the software centre to get the equivalent library file.  When you try to install irfanview it is even gracious enough to tell you that you need that file.

With regard to your other problems;  WOW, is something I know nothing about.  I am not a gamer.

To uninstall wine you can just use normal means, but you also need to remove the hidden folder **.wine** in your home, which is where all the programs you install with wine are really installed, along with all their configurations, etc etc.  If you leave that intact, all your wine installed programs will still be there, and still have any of the problems that you are trying to get rid of.

Your other more general problems sound to me like a hardware incompatibility, so what have you got in the machine?

---

