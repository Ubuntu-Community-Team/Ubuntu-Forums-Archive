---
title: "Question about Network-manager installation"
date: 2007-03-09
forum: Networking &amp; Wireless
---

### Post by Armo on 2007-03-09
I know that im supposed to run the command

sudo apt-get install network-manager

but I need to be connected to the internet to pull the file. I cannot connect until the NM is installed. Is there a way for me to download the tool in a different machine, then install it from a USB drive?

Thanks in advance

-Armo

---

### Post by taurus on 2007-03-09
You can get it from here.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Armo on 2007-03-09
Thanks, I got it downloaded. BTW did i mention Im a total noob? I need to know how to install it from the USB drive.

---

### Post by Armo on 2007-03-09
oh wow, it just froze, again.

---

### Post by taurus on 2007-03-09
What froze? 

When you insert your USB thumbdrive, it should mount automatically to /media/usbdrive.  Open a terminal and run

```
sudo dpkg -i /media/usbdrive/*.deb
```

---

### Post by Armo on 2007-03-09
Ubuntu froze. The keyboard wasnt responding and clicking on icons did nothing.  I restarted the system the only way I know how, pulling the plug. I guess thats bad right?

---

### Post by taurus on 2007-03-09
Did you install Dapper or Edgy and what is the spec of your machine?

---

### Post by Armo on 2007-03-09
Dapper..Edgy I know nothing about those, maybe theyre installed but i dont remember the names. I cant find anything that will show me my specs on the machine, i know its a P4 with about 1g of ram (or 512) not sure. Its an IBM thinkCentre I got from a friend to play with and learn linux on.

---

