---
title: "Starting ath5k driver automatically"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-10-12
Had some trouble switching to ndiswrapper for my WG311T - I uninstalled ndiswrapper, but upon reboot, no drivers are started for my wifi.

I need to do a "sudo modprobe ath5k" to get anything going.

How can I make it automatically load the drivers for my card?

---

### Post by anewguy on 2010-10-12
Well, what you need to do is add it to the list of modules to be loaded at boot.  To do that:

- open a terminal window

- type:

sudo gedit /etc/modules

go to the end of the file and add a line that says:

ath5k

Save the file, close the editor and reboot - you're wireless should be there.

BTW - I'm glad you were able to get through ndiswrapper, especially since it seems you were probably following the manual instructions for ndiswrapper  (load, depmod -a, ndiswrapper -m, modprobe, etc.).  For future reference, there is a GUI'd front end to ndiswrapper called ndisgtk that does all of that for you.  After you install ndisgtk, you just start it by going to System/Administration/Windows Drivers, do an "Add" or "New" and point it to your Windows XP .inf file - that's it!  It takes care of everything else for you.

For others following this thread:

ndiswrapper is a utility to use Windows XP wireless drivers to get your wireless working in Ubuntu.  Some argue it is not needed - however they have not used one of the many adapters that don't have native or restricted drivers.  For all of those adapters you need ndiswrapper.  ndisgtk is a GUI'd front end to ndiswrapper and takes away a LOT of typing and possible mistakes.

You don't need a network connection of any sort to install either of these.

The files to install ndiswrapper are on the LiveCD at:

/pool/main/n/ndiswrapper

Be sure to install the "common" file first.

The files to install ndisgtk are on the LiveCD at:

/pool/main/n/ndisgtk



Just FYI.

Dave ;)

---

### Post by Pas_sa on 2010-10-14
Thanks! That worked brilliantly. I'll mark the thread as solved. I've been wondering how to do that for ages, on a ThinkPad Edge I used for two months, I had to modprobe the iwlagn driver at boot manually after screwing with ndiswrapper!

And yes, should have clarified.. I was using ndis-gtk. I've always used it for my WG311T - for some reason it didn't work in 10.10, so I'll just have to use the slightly less reliable ath5k driver.

Cheers! Very thorough reply. :)

---

