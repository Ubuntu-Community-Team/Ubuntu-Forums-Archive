---
title: "How do I install the Nexuiz 2.5.1 update??"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by TheStabe on 2009-06-26
Could I get a step-by-step?

---

### Post by Shazaam on 2009-06-26
9.04? 8.10?  This might help...
[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)
[https://help.ubuntu.com/8.10/add-applications/C/install-file.html](https://help.ubuntu.com/8.10/add-applications/C/install-file.html)
You can also look at the file with the Archive Manager (Applications>Archive Manager)- most apps come with a README with install instructions.

---

### Post by arch0njw on 2009-07-01
> **TheStabe said:**
> Could I get a step-by-step?

I usually install from the tarballs from their website.  The 2.5.1 update hasn't been packaged in a deb yet.  You can safely remove 2.5 if you have it, and convert over to using the tarballs.

The biggest thing I just ran into with it on my system was needing to have libcurl3 installed.

So... you *could*...

1) remove Nexuiz if you have it installed from DEBs.  Don't worry, your settings are stored in ~/.nexuiz
2) take note of any packages that are uninstalled along with nexuiz.  you might need to put those back
3) download the tgz file from their website
4) unpack the tgz file somewhere that you have 1.4G available (I usually have a ~/bin for this sort of thing)
5) you should be able to run one of the launcher commands from the "Nexuiz" directory

[LIST]
[*]nexuiz-linux-686-dedicated -- for a 32-bit server
[*]nexuiz-linux-686-glx -- for 32-bit single/multi-player GLX graphics (hardware)
[*]nexuiz-linux-686-sdl -- for 32-bit single/multi-player for SDL graphics (software)
[*]**nexuiz-linux-glx.sh** -- GLX graphics & guesses your OS architecture for you
[*]**nexuiz-linux-sdl.sh** -- SDL graphics & guesses your OS architecture for you
[*]nexuiz-linux-x86_64-dedicated -- 64-bit equivalent of above
[*]nexuiz-linux-x86_64-glx -- 64-bit equivalent of above
[*]nexuiz-linux-x86_64-sdl -- 64-bit equivalent of above
[/LIST]
You won't have a menu entry through this approach unless you create one manually.  You'll need to start Nexuiz from the commandline.  Using my preferred hierarcy, I type the following to start it:[FONT=Courier New]
$ cd ~/bin/Nexuiz
$ ./nexuiz-linux-glx.sh[/FONT]

If uninstalling Nexuiz through the package manager removed anything else, you can either reinstalled it by searching for it through the package manager, or through the command line by typing "sudo apt-get install " and then the package names.  For example, I had to install libcurl3, so...  [FONT=Courier New]sudo apt-get install libcurl3[/FONT] ... was what I needed.

Let me know if that works for you.

---

