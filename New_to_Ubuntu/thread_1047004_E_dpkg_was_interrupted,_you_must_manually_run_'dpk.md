---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by rlogan on 2009-01-22
Hi all

I have attempted to install ndas drivers after compiling them from source from ximeta site. Managed to install first component after creating deb file , likewise ndas admin file was made in .deb file. The install of the admin appeared to hand and silly me quit the terminal process.

Back at terminal it suggested to run sudo dpkg --configure -a, which appears to resume the install of the above file. I left it for at least 30mins and no action. Did CTRL-Z to quite process and back to square one.

I have tried deleting the lock file in /var/lib/dpkg and this did nothing. also saw suggestion on the forums to kill all apt processes but that does nothing. 

Any suggestion to get me back in the update arena would be great.

Thanks in advance

Richard:(

---

### Post by x33a on 2009-01-22
ctrl+z does not kill a process, it just stops it to be resumed later. ctrl+c kills a process.

restart your computer and again try the installation.

---

### Post by indytim on 2009-01-22
If your system is still unhappy after re-starting, try the following:

```

sudo apt-get -f install
sudo dpkg --configure -a

```

IndyTim

---

### Post by rlogan on 2009-01-22
Thanks for your replies x33a and indytim.

Have tried below previously but no joy.

sudo apt-get -f install
sudo dpkg --configure -a

Even the Ctrl C was not exiting the application, tried and tried and tried and eventually got it to exit. Tried the above again, no joy.

So I removed the lock file from dpkg and that allowed me to get apt working again. 

To make things worse the ndas drivers must still have issues with 8.10 and were causing lockups. So thought better of the whole affair have removed the ndas drivers via dpkg. The system became stable again and then I could use synaptic and apt smoothly.

If anyone finds a way to get the NDAS s/w working on 8.10 please let me know, I think I will plug the media player into the usb...so much less heartache. Well until I find a better installation guide/process.

Thanks for all of your help

Richard

---

