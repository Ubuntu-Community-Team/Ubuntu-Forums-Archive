---
title: "Problems with ndisgtk"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by MikeTrevX on 2008-01-13
Hey I know there are a lot of people that have had similar problems and I've had a look around the forums and the community docs ( WifiDocs/Driver/Ndiswrapper ) but I dunno my problem seems to be somewhat different. 
I've just installed 7.10 and am trying to get my wireless card working, I don't have a wired connection on the ubuntu comp. but have wireless internet on my laptop. 
I've downloaded the recommended files (as found on the aforementioned community document) and tried to install them through the terminal  

sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils*.deb
sudo dpkg -i --force-depends ndisgtk_*.deb

Each one came up with and error message 

dpkg: error processing ndiswrapper-common_*.deb
  cannot access archive: No such file or directory 

etc. 

I tried it before and after extracting the files to BOTH the desktop and my home directory. 


My other problem is that some of the literature says that I should install ndisgtk through the synaptic package manager (ndiswrapper both common and utils) are installed, but Synaptic package manager cannot find/show the ndisgtk so I cannot install it. 

Any help would be hugely appreciated. I'm a first time linux user so assume I don't know anything please as I really don't. I'm trying to set-up ubuntu for my sister and I intend on using it more extensively once I understand it more. Thank you for your patience. 

Michael T.

---

### Post by csat on 2008-01-13
I suggest you to first of all get informed and tell this forum which wifi board you are trying to configure because there are many tutorials out there that deals with different hardware.

A good information about your hardware can be extract if you go to a console terminal and type sudo lspci -v <enter>

---

