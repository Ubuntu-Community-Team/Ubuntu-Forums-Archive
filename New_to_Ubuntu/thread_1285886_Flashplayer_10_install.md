---
title: "Flashplayer 10 install?"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Xoanan on 2009-10-08
Hi All

I am having issues installing Flashplayer 10 on FF 3.5;  The installation instructions say 

> Installation instructions for tar.gz

       1. Click the download link to begin installation. A dialog box will appear asking you where to save the file.
       2. Save the .tar.gz file to your desktop and wait for the file to download completely.
       3. Unpackage the file. A directory called install_flash_player_10_linux will be created.
       4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
       5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.



The only problem is that when I unpackage Flash 10, it does not create the directory ./install_flash_player_10_linux.  It creates a .so file instead.  What do I do with that?

---

### Post by philinux on 2009-10-08
Copy or move libflashplayer.so to /home/youruser/.mozilla/plugins

you will have to create the plugins directory first.

Simple ;)

---

### Post by jeremyswalker on 2009-10-08
Why not install flash using Synaptic?

---

### Post by philinux on 2009-10-08
> **jeremyswalker said:**
> Why not install flash using Synaptic?

+1 I agree for 32 bit but for 64 bit you need the 64 bit file from adobe.

---

### Post by Xoanan on 2009-10-08
Thanx All! that worked!

---

