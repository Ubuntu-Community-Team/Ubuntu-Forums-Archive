---
title: "New and needs his TV to work."
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Ekcore on 2010-03-22
hi I'm pretty new to the Ubuntu OS, I sued Unix back 5 years ago with a College program and haven't been back until now. Windows start up and what not was aggravating me to no end. Tried to reinstall vista but was missing the driver CD that came with my laptop, so I made the switch! I have a pretty High end laptop for gaming but i mainly use my Xbox for that, I have no problems yet, but i have been scouring the net for instructions on how to use a TV through HDMI to watch movies and still have the main OS on the laptop screen.

I have updated everything fully, got website streaming to work no the problem lays with the Desktop extension, but not really an extension.  Any help at all would be much appreciated.

EKcore.

---

### Post by jimv on 2010-03-25
Not exactly Ubuntu help, but you can download the drivers for Windows using Ubuntu, burn them to a disk/put them on a thumbdrive, and then install Windows again.

If you need a list of hardware, just type "lspci" in a terminal.

---

### Post by Zzl1xndd on 2010-03-25
With some more information we maybe able to help out. Are you able to get anything to display on the TV? If so it is likely that you just have it set to mirror the display. If you have an Nvida or ATI card it would be best to use their tool to set up dual monitors. 

If you do not have anything displayed on your other screen please let us know what kinda of Video card you are using.

---

### Post by wojox on 2010-03-25
Here's the command to run in the terminal for your graphics:

```
lspci | grep VGA
```

---

