---
title: "How to remove a stored wireless connection?"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by GroupB on 2007-10-26
Hello,
I have recently switched from Windows to Ubuntu on my Dell laptop.  My home wireless network has been working great.  After initially configuring it and entering my key, Ubuntu remembers my WPA key and connects automatically.  However, lets say I wanted it to not attempt to connect automatically to that network.  Essentially, I was wondering how would I remove this connection from Ubuntu's memory?  I couldn't find an option to delete a configured wireless connection on any of the options under the network manager.  Thanks,

---

### Post by slight on 2007-10-26
As far as I can tell there's no simple way to do this, which is pretty appalling to be honest.

Anyway, you can do it manually, but be careful.

You'll need to use the terminal I'm afraid, enter the following, replacing "<net name>" with the name of the remembered network you want to remove (remember to change both instances!).:

gconftool-2 --shutdown
cp -R .gconf .gconf_backup
rm .gconf/system/networking/wireless/networks/<net name>/*
rmdir .gconf/system/networking/wireless/networks/<net name>/
gconftool-2 --spawn

If anything goes horribly wrong you can do the following to restore your gconf settings:

gconftool-2 --shutdown
mv .gconf .gconf_broken
cp -R .gconf_backup .gconf
gconftool-2 --spawn

---

### Post by GroupB on 2007-10-26
Thanks for the quick reply. It does seem very silly this feature would not be included in the Wireless Manager GUI (like it is in Windows XP).  I suppose it is not a big deal, but it would be nice to be able to delete old/unused wireless connections.  Is their an easy way to at least see a list of the remembered networks in Ubuntu so I can then try to use your procedure?  I have already used my laptop at home, work, friends houses, public hot spots, etc. and can't possibly remember all the wireless network names I want to delete.  Thanks again for the assistance,

---

### Post by penguins! on 2007-10-26
I've been trying to do the same thing but for some reason there is no "network" key at all under system in gconf. I've checked in gconf-editor and in the .gconf folder - there's just  nothing there. Still running Feisty, any ideas?

Thanks.

---

### Post by kevdog on 2007-10-26
If you were using wicd instead of network manager -- I guess this wouldnt be an issue -- Just a heads up!

---

### Post by penguins! on 2007-10-26
Thanks, but definitely using network manager. Odd.

---

### Post by jacksenechal on 2008-01-26
There is a GUI method for doing this, or at least something close. You can go to System->Administration->Keyring Manager and delete the stored key for the wireless connection (presuming it is a secured connection). 

I'd changed my wireless authentication from WPA2 to WPA (to allow windows XP to connect...). Network Manager wasn't able to connect to it anymore, and wasn't smart enough to ask me to reauthenticate. Deleting the stored key fixed the situation.

---

### Post by chewearn on 2008-01-26
Yes, do as jacksenechal said.  I have done this a few times, and it's always by deleting via the keyring manager.

---

