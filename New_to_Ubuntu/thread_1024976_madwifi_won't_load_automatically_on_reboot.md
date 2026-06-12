---
title: "madwifi won't load automatically on reboot"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-12-29
How do I get madwifi to load automatically whenever I restart my computer? It works fine when I type in terminal sudo modprobe ath_pci and it brings up the wireless networks just fine. However if possible, I'd like for it to load automatically on startup.

Is there a way of doing this? Can I use the same command that I've seen in this forum for ndiswrapper but replace it with ath_pci? 

sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
sudo init 6

My computer is 32 bit i686, atheros AR5007EG AR242X wireless card

Thanks

---

### Post by adult swim on 2008-12-29
EDIT:  i tried to echo it into modules but it didnt work for some reason.  you could use ```
gksudo gedit /etc/modules
``` and add ath_pci to the end of the file and save it.
EDIT 2: ok you can use ```
sudo echo "ath_pci" | sudo tee -a /etc/modules
``` but it will require a restart for it to be there.

---

### Post by BDNiner on 2008-12-29
how did you setup the card? i am guessing that you are not using ndiswrapper for the drivers?

---

### Post by MenZa on 2008-12-29
Adding ath-pci into /etc/modules will work just fine:

```
echo "ath_pci" | sudo tee -a /etc/modules
```

---

### Post by Brian_Newbie on 2008-12-29
I just used echo "ath_pci" | sudo tee -a /etc/modules then restarted my computer and all the wireless networks show up on reboot.

Thanks very much to adult swim and menZa

---

