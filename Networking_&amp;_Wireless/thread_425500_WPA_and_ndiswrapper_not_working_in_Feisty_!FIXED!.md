---
title: "WPA and ndiswrapper not working in Feisty !FIXED!"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by kingcharles1666 on 2007-04-27
Hi,

just wanted to let you know that my 2 week battle with WPA on a USB wifi adapter which required ndiswrapper has been solved!

The fix: install the latest ndiswrapper (currently 1.42)

I am a noob and I managed so everybody can do it. I cut and pasted from several posts to a terminal so I thought I put my steps in one post. maybe helful for someone:

step 1 you probably tried with the ubuntu version of ndiswrapper but that clearly does not work so we must get rid of it:
```
              sudo modprobe -r ndiswrapper 
              sudo apt-get --purge remove ndiswrapper-utils 
              sudo rm -r /etc/ndiswrapper/ 
              sudo rm -r /etc/modprobe.d/ndiswrapper
```

step 2 install some stuff:
```
             sudo apt-get install dh-make fakeroot gcc-3.4 build-essential
```

step 3 get the latest ndiswrapper and unpack it somewhere easy:

[http://sourceforge.net/project/showfiles.php?group_id=93482]("http://sourceforge.net/project/showfiles.php?group_id=93482")

you can unpack with rightclick and select "unpack here" (translation from dutch so may be different...)

step 4
Change your terminal prompt to the directory where you unpacked the ndiswrapper:
```
        cd /path
```

step 5 install ndiswrapper:
```
        fakeroot
```
repeat below command until no messages of removed files are displayed:
```
        sudo make uninstall
```
then continue:
```
        sudo make
        sudo make install
```

step 6 install the win driver:
```
        sudo ndiswrapper -i /path_to_win_driver/driver.inf
        ndiswrapper -l
```
you should get this:
```
        Installed ndis drivers:
        {name of driver}  driver present, hardware present
```
```
        sudo depmod -a
        sudo modprobe ndiswrapper
```

Reboot and keep your fingers crossed!

Please note that whenever you get a kernel update you will need to re-install ndiswrapper. Just follow steps 4 to 6 again and you're done,

---

