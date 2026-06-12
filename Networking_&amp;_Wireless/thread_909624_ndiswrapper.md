---
title: "ndiswrapper"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by bryctucker on 2008-09-03
i have a rosewill RNX-G100 card that is decent, but i want to get it to work with xubuntu 6.06 with ndiswrapper, can this be done?

---

### Post by pytheas22 on 2008-09-03
It should be possible.  Please post the output of these commands so that we can look up your card and find the Windows drivers you need:
```

uname -m
lshw -C Network
lspci -nn
lsusb
```

Also, you may want to consider using Hardy 8.04 instead of 6.06.  ndiswrapper should still work fine on 6.06, but in general it's better to be on Hardy, the most recent long-term-support release of Ubuntu.

---

### Post by bryctucker on 2008-09-03
alright
i did those commands, and copyed them from linux to windows and it messed them up, but here they are anyways

root@bryce-laptop:/home/bryce# uname -m
i686
root@bryce-laptop:/home/bryce# lshw -C Network
root@bryce-laptop:/home/bryce# lspci -nn
0000:00:00.0 0600: 8086:7192 (rev 02)
0000:00:02.0 0300: 10c8:0004 (rev 01)
0000:00:07.0 0680: 8086:7110 (rev 02)
0000:00:07.1 0101: 8086:7111 (rev 01)
0000:00:07.2 0c03: 8086:7112 (rev 01)
0000:00:07.3 0680: 8086:7113 (rev 02)
0000:00:0a.0 0607: 104c:ac17 (rev 02)
0000:00:0a.1 0607: 104c:ac17 (rev 02)
root@bryce-laptop:/home/bryce# lsusb
Bus 001 Device 004: ID 1286:1fab
Bus 001 Device 001: ID 0000:0000
root@bryce-laptop:/home/bryce#


sweet it worked, it was all one line, 

the second thing is that the computer im running 6.06 on

is a pentium 2 233 mhz, with 256 mb of ram,  so thats not the best idea... it took 30 mins for 6.06 to install
but after it gets booted it runs fine

teh card is usb btw, and its a laptop, with no internet connection, the wifi card is its only connection, it use to be running windows 98 se, but i got tired of that bs... so here i am lol

---

### Post by pytheas22 on 2008-09-03
8.04 should run just as fast--perhaps even a little faster, given some performance tweaks in boot time, Gnome etc. that have come out since 2006--on your hardware.  So I'd definitely recommend giving it a try.

I also have to ask you to post:
```

lspci
```

(without the -nn), because the information above doesn't provide everything I expected (probably because the versions of *lspci* and *lshw* on 6.06 give different output than the ones in more recent Ubuntu releases).

---

### Post by bryctucker on 2008-09-03
alrihgt, well hang on to those commands, ill download the xubuntu 8.04 and install it

---

### Post by pytheas22 on 2008-09-03
Actually don't worry about posting more information; I figured out what I needed (the PCIID of your card, which is 1286:1fab).  But do you have the Windows drivers for that card available anywhere?  Because I'm having a hard time finding them on the Internet.  Do you have them on a CD?

EDIT: nevermind; I found drivers too...although if you have them on CD that would also work.

---

### Post by bryctucker on 2008-09-03
alright

i've got the drivers on the desktop of the linux computer, the drivers are for windows, all i really wanted was if you could tell me how to start ndiswrapper, i can't find it

---

### Post by pytheas22 on 2008-09-03
You first have to install ndiswrapper.  Fortunately, it comes on the Ubuntu install CD.  Make sure your CD is in the drive, then go to System>Administration>Software Sources.  Under the "Ubuntu Software" tab, look for the "Installable from CD-ROM/DVD section."  Check the box enabling use of your CD as a repository.  Then close the window.  If you're prompted to reload the sources list, click yes.

Then simply open a terminal and type:
```

sudo apt-get update
sudo apt-get install ndiswrapper* ndisgtk
```

and it should get installed from the CD.

Once ndiswrapper is installed, you can start a GUI application for installing the Windows drivers by typing:

```
sudo ndisgtk
```

Sometimes the CD doesn't want to become a repository; if you have problems, let me know.

---

### Post by bryctucker on 2008-09-03
i don't see adminsitration =(

---

### Post by bryctucker on 2008-09-03
i went to synaptic and added that way, will that work?,  and i do the sudo apt-get install .... that doesn't work, pkg not found

---

### Post by bryctucker on 2008-09-03
its not working i found the -utils in synaptic but thats it

---

### Post by bryctucker on 2008-09-03
did you find a driver or something that might work for my wifi card for linux or just have to use ndis

---

### Post by pytheas22 on 2008-09-04
Sorry, I was away from my computer for a while...

Did you get ndiswrapper installed?  If it's installed successfully, then you should be able to type "ndiswrapper" at the command line and get output like:
```

install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
```

You should have installed both ndiswrapper-utils and ndiswrapper-common.  They're both on the CD, so if your CD is enabled as a repository, Synaptic should find both.

You can also find the ndiswrapper packages on the Ubuntu live CD by opening it up in the file browser (click the "Places" menu in the top-left of your screen, and you should see an item to open your CD), then navigating to pool>main>n>ndiswrapper.  Double-click the packages to install them.

And no, as far as I can tell, your card unfortunately does not have any native driver.

---

### Post by bryctucker on 2008-09-04
nope, the only thing that synaptic found was the -utils, so am i going to have to download this and copy it to the laptop?

and i went through the disk, the only thing there was the -utils, not the commons

---

### Post by pytheas22 on 2008-09-04
I don't know why ndiswrapper-common is not also on the disk--maybe Xubuntu is different, although it shouldn't be--but you can download the packages manually from [http://packages.ubuntu.com:](http://packages.ubuntu.com:) [common]("http://ubuntu.mirrors.tds.net/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb") and [utils]("http://ubuntu.mirrors.tds.net/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb").  Put them on a USB drive, then move them to your Ubuntu computer and double-click to install that should work.

Also sorry for giving you some instructions that were meant for Ubuntu, not Xubuntu (like the System menu)--I forgot that you were on Xubuntu.

---

### Post by bryctucker on 2008-09-04
no prob, im not really new to ubuntu, or experiecned with it, so, all i know is this laptop is WAY TOO OLD to do any thing higher then 6.06 or win98

ill dnld those packages and let you kow how they work

---

### Post by bryctucker on 2008-09-04
i can't find any of the packages just the front end gui, nothing else

---

### Post by bryctucker on 2008-09-04
ill just update it to 8.04, then ill do the stuff again
cause i think i found it for 8.04 not 6.06

---

### Post by bryctucker on 2008-09-04
i got it installed now on 8.04 xubuntu, but i can't get the driver installed, i don't know how to do that, thats what i need help on now, i tryed ndiswrapper -i netNw225.inf, which is the driver .inf for xp - 2000, and i cd into the folder, i don't know what to do now, it said it installed, but its not on there, and the ndisgtk don't work, its not installed

---

### Post by pytheas22 on 2008-09-05
If you type:
```

ndiswrapper -l
```

(that's a lowercase L, not a 1), what does it say?

Also, if you type:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0
iwlist scan
```

are you able to see any networks then?

Finally, does the output of this command:
```

dmesg | grep -e ndis -e wlan
```

mention any errors (like something along the lines of "failed to load ndis driver XXXX....")?

---

### Post by bryctucker on 2008-09-05
the iwlist scan shows my network, now how do i connect to it

---

### Post by bryctucker on 2008-09-05
nvm, i figured it out, thanks man, ill have to remeber how to do that, so i won't have to stir up this much trouble again

---

### Post by pytheas22 on 2008-09-05
I'm glad you figured it out.  If you run into any other problems let me know.

---

