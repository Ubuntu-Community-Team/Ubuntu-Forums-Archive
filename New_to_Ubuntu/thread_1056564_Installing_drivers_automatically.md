---
title: "Installing drivers automatically?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by lone_wolfII on 2009-01-31
You could definitely call me a beginner with Ubuntu but I do have some experience using the terminal through Uni. 

From my understanding Ubuntu automatically installs all open source drivers automatically. My questions are:

[LIST]
[*]How can I find out what drivers have been installed and which ones haven't?
[*]For drivers that haven't been installed, where's the best place to get them?
[*]Does lshw report hardware configured correctly, or all hardware connected?
[/LIST] 

I'm running 8.10, so I don't have device manager. I'm not worried about looking at/modifying device files or the like, and I should be able to follow whatever instructions you give me, so don't worry about taking it slow! :D

Thanks guys in advance.

---

### Post by Crafty Kisses on 2009-01-31
Depending on what you want to install drivers for there is the "Hardware Drivers" option, which can be easily accessed by going to **System->Administration->Hardware Drivers**. Check and see if anything comes up. For your second question, it really depends again, what do you need drivers for? For you third question I'm pretty sure the following command:
```
lshw
```
Does report hardware correctly, I could be wrong though. To check everything connected via PCI you could just run the following command and it will tell you:
```
lspci
```
There's also a device manager called "GNOME Device Manager" you can download that from the repositories by either going into Synaptic and looking for it, or running the following command:
```
sudo apt-get install gnome-device-manager
```

---

