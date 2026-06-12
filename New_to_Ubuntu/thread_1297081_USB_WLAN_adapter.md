---
title: "USB WLAN adapter"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Axxl on 2009-10-21
Hi!
I'm having a little bit of trouble getting my internet connection working. I'm writing this from within WinXP. The thing is, I can only find a 32-bit windows driver for my wlan-adapter. My question now is, will it work in a 64-bit Ubuntu if I use ndiswrapper?

---

### Post by NightwishFan on 2009-10-21
Perhaps use google to search for Linux compatibility or tutorials on your specific card. To find out your card model and driver used, run this in a terminal.
```
sudo lshw -c network
```
or
```
sudo iwconfig
```

If you want to use Ndiswrapper, here is a page for help on Ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Axxl on 2009-10-21
Thanks, I used ndiswrapper to install it, but it doesn't seem to work. I followed these instructions:

After you download the tarball, right click on it and select 'Extract Here'. Now in a terminal CD into the folder that you just extracted from the tarball. Install time using ndiswrapper!

    >sudo ndiswrapper -i WlanUTG.inf (Installs the driver)
    >sudo ndiswrapper -l (Checks to see if the driver installed)
    >sudo ndiswrapper -m (Creates the wlan0 alias)
    >sudo modprobe ndiswrapper (Loads the new driver)

After that the driver is installed, but is still not quite activated. To activate the driver click on System> Administration> Hardware Drivers


Problem is I don't see any driver in System> Administration> Hardware Drivers window. That's why I was wondering if it is possible at all to install a 32-bit driver on a 64-bit Linux.

sudo ndiswrapper -l says the driver is installed.

---

### Post by NightwishFan on 2009-10-21
I am sorry I could not be of much help. I am actually not sure if ndiswrapper works like so. Do you reboot after you installed the driver?

---

### Post by Axxl on 2009-10-21
yes

---

### Post by NightwishFan on 2009-10-21
What does this command tell you:
```
sudo iwconfig
```

---

