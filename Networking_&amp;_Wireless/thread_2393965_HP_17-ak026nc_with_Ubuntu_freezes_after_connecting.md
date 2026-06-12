---
title: "HP 17-ak026nc with Ubuntu freezes after connecting to the Internet"
date: 2018-06-10
forum: Networking &amp; Wireless
---

### Post by thomaskra on 2018-06-10
Good day, i have a HP 17-ak026nc notebook. I need to work with Ubuntu 16.04 LTS or 18.04 LTS. The problem is that when i connect to the Internet via a LAN cable or WiFi, the operating system (Ubuntu 16 and 18) freezes and i have to shut down the notebook. And it happens even when installing Ubuntu. I have a connected LAN cable - the installer is freezing. Without an Internet connection - everything works. Thanks in advance for the answers.

---

### Post by praseodym on 2018-06-10
Please run the following commands
```

lspci -nnk
lsusb
rfkill list
iwconfig
lsmod
```
Does it work with SecureBoot turned off?

---

### Post by thomaskra on 2018-06-11
Do you need to insert a terminal dump here after entering these commands?

Yes, SecureBoot is off.

---

### Post by thomaskra on 2018-06-12
I entered the above commands, then I connected the LAN cable and Ubuntu fell and stayed frozen with the message:

/dev/sda: clean, 189223/7331840 files, 1470111/29301248 blocks

:-(

---

### Post by praseodym on 2018-06-13
Hm, maybe the disc is full?!
```

sudo apt-get autoremeve
sudo apt-get autoclean
sudo apt-get clean
```

---

### Post by thomaskra on 2018-06-14
I do not think so. The notebook is (as shown in the configuration) 128GB SSD M.2 and 1TB HDD. I install on the SSD and choose to delete the drive during installation. This means that after installation, Ubuntu only takes up disk space. :-O

---

### Post by thomaskra on 2018-06-15
So to close it. I thank everyone who participated :-) and here is the result.
I was unable to solve anything with the HP 17-ak026nc.
So I changed it (though I hate it) for a weaker configuration in the Lenovo V320-17ISK notebook.
Ubuntu 16.04 runs on it without any problem, fast, just great.
Once again thanks and maybe again ... :-)

---

