---
title: "Wireless Connection Not Showing In the Network Settings"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by agirlnameddanni on 2007-01-05
okay, well. I am using Ubuntu 6.06, Drapper Drake. 
And after in the terminal doing updates, I rebooted my computer, and I noticed that my internet wasn't working anymore. 
I went to the Network settings, and discovered that of the three types of connections, one (wireless connection), the one i was using was completley gone! and I can't find the interface ath0 anymore either... in the terminal, i used the commands

```
sudo iwconfig ath0 essid "network name"; sudo iwconfig ath0 key "WEP"; sudo dhclient ath0
```

after doing that, it told me that there was no such divice. I was on another forum, and some of the people there said that my updates messed one of my packages up. They told me to reinstall the package entitled linux-restriced-modules-general. first of all, i dont have that specific package, so i tried the next best one, (linux-restriced-modules-common), but that didn't download because it said there was a failure to connect to the required page, and i am guessing that is because i have no internet. 

I am using a Dlink card...the chipset is Atheros. 
Please help me in any way possible! Thanks so much!

---

### Post by jpeddicord on 2007-01-05
I have a DLink + Atheros card here, so it should be working fine.

Type this in the terminal to add the card to the modules list (it may have been accidentally removed):
```
sudo modprobe ath_pci
```(Note: if it is not a PCI card, type ath_ and press TAB twice to see available options.)

After you run the modprobe command above, run this to tell the system to automatically load the card module:
```
sudo depmod
```

Once completed, you can either restart your PC or just type this to restart the networking functions:```
sudo /etc/init.d/networking restart
```

Hope this helps!

-Jacob

---

