---
title: "Vinagre (VNC) .deb for Ubuntu?"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by ZephyrXero on 2007-10-15
Has anyone seen a .deb for [_Vinagre_](http://www.gnome.org/projects/vinagre/)? I've been looking all over the web but have had no luck so far...

---

### Post by nw_raptor on 2007-10-16
I only got a package for Gutsy (doesn't work on Feisty)

---

### Post by saracen on 2007-11-29
So where is this deb package for Gutsy?

---

### Post by ZephyrXero on 2007-12-13
Yes, a Gutsy package would be great :)

---

### Post by nw_raptor on 2007-12-14
note, this is version 0.3. the latest is 0.4 released on dec 12.

---

### Post by altonbr on 2008-01-31
IF you prefer, you can always run UltraVNC (an open-source, GPLed Windows app) via Wine.

[http://www.uvnc.com/download/index.html](http://www.uvnc.com/download/index.html)

---

### Post by altonbr on 2008-02-01
What's odd about that version 0.3 of Vinagre is that I can't connect on a port lower than 5800. If I try and connect on port 2 (don't ask), it automatically marks me at 5800. Very frustrating...

---

### Post by linuxd00 on 2008-02-23
wow.. vinagre rocks... up to now i havent found any comfortable VCN programs for linux.
i tried tightvnc (which i like a lot in windows) but the interface is quite odd.

too bad i couldnt compile vinage miself... it needs tons of things which are not in the gutsy repos.

cant wait for ubuntu 8.4!

---

### Post by imjustabill on 2008-02-27
Here are some debs I compiled for Gutsy. Make sure you install gtk-vnc first!

---

### Post by pegardan on 2008-03-08
Hi imjustabill, 
I test your binaries and receive the folowing error when i try to execute the application...

vinagre: error while loading shared libraries: libgtk-vnc-1.0.so.0: cannot open shared object file: No such file or directory

Any idea ?

---

### Post by fatagnus on 2008-03-08
same thing here, and gtk-vnc is already installed.

---

### Post by pegardan on 2008-03-08
I found the solutions doing the following symbolic link:

sudo ln -s  /usr/local/lib/libgtk-vnc-1.0.so.0 /usr/lib/

Regards!

---

### Post by pegardan on 2008-03-08
Well... the application open without problems but when i try to open a connection with a vncserver nothings happens (gray window). I put invalid ip's to see if the program is trying to establish a connection but i saw the same result.

Maybe the package is corrupt ... the program in console not throw nothing ... it's strange.

Any advice is welcome!!

---

### Post by AndyCee on 2008-04-03
Sorry if I'm stating the obvious - 

[http://packages.debian.org/vinagre](http://packages.debian.org/vinagre)

Cheers.

---

### Post by altonbr on 2008-04-03
> **AndyCee said:**
> Sorry if I'm stating the obvious - 

[http://packages.debian.org/vinagre](http://packages.debian.org/vinagre)

Cheers.

Nope, didn't even think of it. Thank god I'm using Hardy though...

---

