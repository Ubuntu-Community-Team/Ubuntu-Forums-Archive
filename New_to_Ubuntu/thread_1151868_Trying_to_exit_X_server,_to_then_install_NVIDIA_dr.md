---
title: "Trying to exit X server, to then install NVIDIA driver"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by swarup on 2009-05-07
I have researched on how to exit the X server so as to install the NVIDIA driver (which I downloaded from the NVIDIA website for 64bit linux). In one place it says to: 

> do Ctrl+Alt+F1 to switch to a virtual console, log in, terminate the Xserver because it is still running :
```
sudo /etc/init.d/gdm stop
```
then start the installer
```
sudo sh /path/to/package.run
```

In another place it says:

> To stop X completely,
```
/etc/init.d/gdm stop
```
You can do this from any terminal

I have tried both the above. But regardless of whether I do "Ctrl+Alt+F1" or simply do "/etc/init.d/gdm stop" from a terminal window, I end up with what looks like an MSDOS screen-- a black screen with a command line cursor. But in such a situation, how can I access the driver's very lengthy file name, to paste it after "sudo sh ...", so as to do the install? They don't expect me to write that entire file name on piece of paper and then handwrite the whole thing into the MSDOS-type terminal window, do they?

---

### Post by Alterax on 2009-05-07
Not necessary to type it all; we Linux folk are WAY too lazy for that.

Just go into the directory and type the first few letters of the filename  (remember--it's case sensitive) and use your [TAB] key.  It'll autocomplete.

---

### Post by barwin on 2009-05-07
> **swarup said:**
> 
I have tried both the above. But regardless of whether I do "Ctrl+Alt+F1" or simply do "/etc/init.d/gdm stop" from a terminal window, I end up with what looks like an MSDOS screen-- a black screen with a command line cursor. But in such a situation, how can I access the driver's very lengthy file name, to paste it after "sudo sh ...", so as to do the install? They don't expect me to write that entire file name on piece of paper and then handwrite the whole thing into the MSDOS-type terminal window, do they?

The "MSDOS" screen is the terminal :)  When you're in X-windows using a "terminal" that's actually a terminal emulator.  When you've exited X you're using the actual terminal.

And no you don't have to write out the entire file name, use tab-completion.  That is, type just the first few letters of the filename and then hit the TAB key and it will complete it for you. If there is more than one possible completion, you may need to hit the tab key more than once, and / or enter a couple more letters and then hit tab again.

Best of luck.

---

### Post by decoherence on 2009-05-07
> **swarup said:**
> They don't expect me to write that entire file name on piece of paper and then handwrite the whole thing into the MSDOS-type terminal window, do they?

nope. just note the first few characters of the filename. type them in and press tab -- it will auto-complete the rest of the name (or as much of it as possible, if there are two files with similar names.) 

press tab twice to see all the possible completions.

---

### Post by swarup on 2009-05-07
Wow, three of you giving the same reply-- I can see this is a skill I should know by now. (Usually when in a normal terminal window, I just do copy-paste of the file, and its name together with its directory all appear automatically.)

Well, I tried a test in a normal terminal window, just to see if the tab system will work for me. I did cd to the desktop, and then at the next command line typed "NVIDIA-L", which are the first several letters of the file name (and yes, they are all capital letters). But nothing happened! What am I doing wrong?

---

### Post by freak42 on 2009-05-07
well it doesn't autocomplete because simply the filename on the command line doesn't make any sense (what shoudld it do with it?)

to execute a file in the current director prepend ./
./filename

the executeable bit must be set use
chmod +x filename

or in your case on the desktop
chmod +x NVI[tab]

hth

---

### Post by swarup on 2009-05-07
Well, I understood the first thing you wrote-- that it needs to know what to do with the file. Anyhow, I went ahead and tried what the other folks were saying to do--that is, to exit X and then try the autocomplete-- and it worked! My NVIDIA driver is now installed. Many thanks to all of you. :P

---

### Post by barwin on 2009-05-07
Np, glad you got it working!

:)

---

