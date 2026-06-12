---
title: "Windows virus on usb flash"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by hooldus on 2011-04-10
Is there a possibility that viewing the infected flash disk in Ubuntu will somehow affect Windows 7 SP1 64-bit installed, that is installed in dual boot? Ubuntu is installed using Windows Installer, so is not in the extra partition.

---

### Post by Enigmapond on 2011-04-10
I would say it's very unlikely. You would actually need to access it with Win7 for it to be effected

---

### Post by seawolf167 on 2011-04-10
I *very, very highly* doubt it. You can clean the virus with clamav

```
sudo apt-get install clamav
```

the main purpose of which is to ensure that Windows-related viruses are not transfered to other computers.

---

### Post by irv on 2011-04-10
If you are running Wubi within windows, Ubuntu is running from a large file with contains the whole OS. If the virus is on the USB drive and you infect the large file that contains the OS in reality you have an infected file on your windows partition. But again this is going to be unlikely. I hope this answers you question.

---

### Post by hooldus on 2011-04-10
Thanks guys for your answers. 

So it’s actually not a bad idea, when a friend comes and begs you to copy some file to his usb flash drive, make a restart and accomplish this assignment in Ubuntu. Looks a bit weird, but I am on a bit paranoid side :)

---

### Post by norm7446 on 2011-04-10
Microsoft calls this FUD. Don't worry it will pass.

---

### Post by Learning Linux 2011 on 2011-04-10
A Windows virus will be looking for Windows files, which it will not find in Linux.

---

