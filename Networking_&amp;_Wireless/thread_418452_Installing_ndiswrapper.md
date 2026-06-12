---
title: "Installing ndiswrapper"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by The SDX on 2007-04-22
Hi! I just installed Ubuntu, and I love it so far. However, I'm having a big problem. My Linksys WUSB54G isn't working. I've read some tutorials on how to install ndiswrapper, but I can't because the only way I can access the internet on my Ubuntu machine is through my wireless card (which is the one I'm trying to get working). Also, I've tried the "sudo make install" thing, but I think I need to install that stuff from Synaptic to get that working. But, like I said, my Ubuntu machine has no internet access. :confused:  Could someone help me get this working? I don't want to have to go back to Windoze.

---

### Post by spd106 on 2007-04-22
Ndiswrapper is on the install cd, so you can install through synaptic. You will need the windows driver.

---

### Post by The SDX on 2007-04-29
Great! I'll try that.

---

### Post by The SDX on 2007-04-29
Well, ndiswrapper isn't on the CD. :(  I tried the "sudo apt-get ndiswrapper" in terminal, but it said package could not be found.

---

### Post by spd106 on 2007-04-29
That's very annoying, it was on Edgy's desktop cd. I suppose it had to give for compiz or something.

I suggest that you download the ndiswrapper-utils-1.9 and ndiswrapper-common packages and transfer them over by some other means (USB disk?). Just double-click on the files to start the install process, do ndiswrapper-common first. You may want to grab ndisgtk from universe too.

Click [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=ndiswrapper&searchon=names&subword=1&version=feisty&release=all") for a download page.

These files (except ndisgtk) are definitely on the 7.04 alternate cd, sorry for the error.

---

