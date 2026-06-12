---
title: "Installing driver for wireless card"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by andycski on 2008-08-13
I have just installed ubuntu 8.04.1 (noobie) and it recognizes my Atheros AR242x card but it doesn't appear to have a driver as it won't work. In going through the help section, I was directed to open the Ndisgtk packet to install the driver, but I can't find this on my system. Any suggestions?

---

### Post by chili555 on 2008-08-13
Please see post #4 here: [http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=865971&highlight=AR242x)

---

### Post by andycski on 2008-08-14
I did the above (going on line with a wired connection and putting commands in the terminal), but couldn't get past the first line. "install build-essential" could not be found. I went through the rest of the commands but it didn't work. I assume the driver could not be loaded because of the lack of build essential package. I looked in the synaptic package manager and couldn't find it there. Any other suggestions?

---

### Post by chili555 on 2008-08-15
Please go to Synaptic. Go to Settings -> Repositories -> Ubuntu Software. Make sure everything is checked. Make sure the server you select is at or near your location. After closing Repositories, press the Reload button. Then search for and install *build-essential* and *linux-headers-generic.*> I went through the rest of the commands but it didn't workIndeed. Since you have evidently run 'make' unsuccessfully, after you get *build-essential* and *linux-headers-generic* installed, please amend the 'make' et al to this:```
**make clean**
make
sudo make install
sudo modprobe ath_pci
sudo reboot
```That will clean up any corrupted bits that may have been made with an improper 'make.'

Post back if you get stuck.

---

### Post by andycski on 2008-08-15
Thanks so much for your help-it worked and I am amazed at the help the community gives, especially to a neophyte

---

