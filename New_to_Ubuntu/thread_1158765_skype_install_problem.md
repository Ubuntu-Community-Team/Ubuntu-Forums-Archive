---
title: "skype install problem"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by medicalystoned on 2009-05-14
the problem is i can not seem to be able to get skype installed
from synaptic and adept, neither can find it.
from terminal I tried " sudo apt-get skype install", i got E: invalid operation skype

any help for a confused noob would be sweet........ peace

---

### Post by lindsay7 on 2009-05-14
try "sudo apt-get install skype"

---

### Post by AndThenWhat on 2009-05-14
There is a .deb download for Skype I found it on their website:

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

If you ever want to install a program you can search google for a .deb file, they are basically like a .exe for windows.

---

### Post by Jazzy_Jeff on 2009-05-14
I just downloaded skype from [here]("http://www.skype.com/download/skype/linux/choose/?cm_sp=sv|download-_-site|sidebar-_-download_lnk|en_us"). Just download the Ubuntu package and double click on it.

---

### Post by hvacmoose on 2009-05-14
sudo apt-get install skype

---

### Post by medicalystoned on 2009-05-14
> **hvacmoose said:**
> sudo apt-get install skype

that gave me " package not found"

---

### Post by hobo14 on 2009-05-14
You may have webcam trouble if you use the .deb from their website.
See here: [http://ubuntuforums.org/showthread.php?t=1143338]("http://ubuntuforums.org/showthread.php?t=1143338")
Solution is to add medibuntu intrepid to your repos and install from there.

For sound problems read this:
[http://ubuntuforums.org/showthread.php?t=959541&page=6]("http://ubuntuforums.org/showthread.php?t=959541&page=6")
Solution:
sound in - HDA Intel(hw:intel,o),  --- or similar, depends on yoursystem
sound out - pulse
ringing - pulse

---

