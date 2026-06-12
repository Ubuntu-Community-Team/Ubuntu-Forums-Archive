---
title: "Can't get to my GUI"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by bledsoe on 2010-05-24
A few weeks ago I somehow messed up my Ubuntu login process.  I was unable to log in normally, and the only way I could get to my GUI was to select the recovery mode in the GRUB bootloader, then select netroot, then run the "startx" command from the command line.

While this was a little inconvenient, and I hadn't yet figured out what was causing the problem, I could at least get to the ubuntu graphical interface and get stuff done.

Now, for some reason, this method no longer works.  When I try it, I just get a completely blank screen after I type the "startx" command, and I have to manually shutdown the computer.

All my files seem to still be there, but I can't get the graphical interface to come up.  Could someone please help me fix this?  Any suggestions greatly appreciated.

---

### Post by anarchywolf46 on 2010-05-24
Did you try reinstalling gnome or kde?

---

### Post by bledsoe on 2010-05-25
Based on another user's suggestion, I installed KDE back when I had the original problem (you can see the whole thread at [http://ubuntuforums.org/showthread.php?t=1476885&highlight=bledsoe](http://ubuntuforums.org/showthread.php?t=1476885&highlight=bledsoe) ), but that didn't seem to address the login problem.

I think I'm now running KDE; what is the exact command I should use to reinstall gnome or kde?

Thanks,

---

### Post by Chronon on 2010-05-25
You can try to fix broken packages if they exist by issuing
```
sudo apt-get -f install
```

Entering
```
sudo apt-get --reinstall install ubuntu-desktop
``` should reinstall the basic ubuntu desktop system.  Replace "ubuntu" with "kubuntu" for the corresponding kubuntu desktop system.

---

### Post by bledsoe on 2010-05-25
Hi Chronon, thanks for the suggestion.

I tried entering the "reinstall" command you suggested, but after I got a "Here are the different packages we're going to install, do you want to continue" message and replying "Yes", my machine sits for a while trying to connect to us.archive.ubuntu.com then flashes several "failed to fetch" messages.

Any other ideas?

---

