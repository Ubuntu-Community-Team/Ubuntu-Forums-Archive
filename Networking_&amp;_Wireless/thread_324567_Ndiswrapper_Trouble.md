---
title: "Ndiswrapper Trouble"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by k2pow on 2006-12-23
I have a Dell Truemobile 1180 and so far I have tried installing many drivers(all of which havent worked) . I used the one that game with the installation disc and a driver downloaded from dell. I used the GUI(forget the exact name) program to install the windows drivers and then when I do ndiswrappper -l it says driver present hardware present(everything thats suppose to happen). Although everything looks nice in the network manager nothing is being detected, and iwconfig doesnt read anything either. Help would be greatly appeciated Ive been struggling with this for weeks.

---

### Post by dbott67 on 2006-12-23
1. Download the recommended driver for your card here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

If you can't figure out the exact chipset use the following commands:
```
lspci
```
```
sudo lshw -C network
```

2. Install **build-essential** from Synaptic (for compiling ndiswrapper)

3. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

4. Compile **ndiswrapper** according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

[COLOR="Red"]Note: any kernel updates will require that ndiswrapper be recompiled[/COLOR]

---

### Post by k2pow on 2006-12-24
I will try that again; however I do believe I have the latest version of ndiswrapper. Has there been any updates to the kernel in the last week cause thats when I last updated? Do you think this will change anything because the driver appears to be loaded its just not working?
Thank you. 

Also my adapter is usb so what is the command instead of lspci for usb?

---

### Post by k2pow on 2006-12-24
Im  a little confused because when I run lsusb and then type that code you said I get a reading that my chipset for the Truemobile is prism2_usb; however I have heard a lot of people say its broadcom. Anyway I downloaded the exact driver that matched my adapter from the list and installed the .inf. Then I had to manually add one of the .sys files to the NETDELUS (my driver) file(because it said to in the list). After I do this I get

netdelus : driver installed
          device (413C:8100) present (alternate driver: prism2_usb)

After that I still dont get any sign of my wireless in the network manager.

Also after I loaded all the modules and did all that stuff it said in the system log that my driver was loaded.

---

