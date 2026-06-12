---
title: "compiz exiting in the dark of night"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by SteveGoTex on 2010-06-22
I have an Optiplex 210L, to which I have added, on a separate SATA drive, Ubuntu 10.04. The primary drive has XP-Pro SP3 on it, and all is set up dual boot.

I installed Ubuntu via the Minimal Install CD, and then added the gnome desktop, and the apps that I wanted, as I went along.

The machine has Intel integrated graphics, and I have been able to set up compiz with no problems, in the "Extra" setting on the System->Preferences->Appearence dialog.

However, overnight, the system reverts to Metacity, apparently on its own. I leave the system on, and logged in. When I wake up the display I find that compiz has "left the building."

Is there anything I can look at to see what is going on? Is there some type of monitoring I can turn on to learn why compiz is quitting?

Thanks in advance for your comments and help.

I just started using Ubuntu in the last few weeks. I love how much more responsive my old machine has been, and how much more readable my display is to my aging eyes.

Steve G

---

### Post by ibuclaw on 2010-06-22
Have a look at a file named **.xsession-errors** in your home folder.

Though, for best debugging practise. Delete and Recreate a blank file in it's place. Then leave your computer on over night. If Compiz has been replaced by Metacity, open it for reviewing.

Regards

---

### Post by SteveGoTex on 2010-06-22
Thanks, I have cleared out the file. Will report any changes.

Steve G

---

