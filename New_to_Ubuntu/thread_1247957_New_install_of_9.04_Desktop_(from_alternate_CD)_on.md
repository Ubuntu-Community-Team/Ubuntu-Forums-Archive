---
title: "New install of 9.04 Desktop (from alternate CD) on ASUS P5GC-MX - X won't display"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Sootah on 2009-08-23
I just installed 9.04 on a play computer I have with an ASUS P5GC-MX motherboard. The regular install CD wouldn't work, it wouldn't load the graphical install interface. I then used the alternate CD to install, which went off without a hitch.

Anyway, now that I've booted for the first time, it shows the pretty Ubuntu loading splash page and then once it gets to where you'd log into the desktop (X) my monitor simply displays the message "Cannot display this video mode". I've dropped to a root shell with networking and looked at the /etc/X11/xorg.conf file, and it has everything as default in there. I then tried to add the following lines to the "Devices" section: 

Driver "intel"
Option "AccelMethod" "XAA"

This worked for me some time ago on a Presario SR1503WM that wouldn't load X, but had no effect on the P5GC-MX. I figured where the mobo has the Intel 945GC Chipset that it'd work, but unfortunately, it did not.

Suggestions?

Thanks in advance for your help!

-Sootah

---

### Post by Sootah on 2009-08-23
Oh, also, I tried the "dpkg-reconfigure xserver-xorg" command at root terminal to no effect, as well as the option in the recovery menu to attempt to fix graphical problems.

Thanks again!

---

### Post by Sootah on 2009-08-23
Anything?

---

