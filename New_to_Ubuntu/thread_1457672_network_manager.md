---
title: "network manager"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by mavenuparker on 2010-04-18
i uninstalled network manager in ubuntu 9.04 to install wicd....
after i uninstalled the network manager....there were problems downloading the packages for wicd.....
can some one help me to  install network manager back again......now i cant connect to internet in ubuntu.....so synaptic is not working...tell me which files to download and how to install them manually....

---

### Post by 2hot6ft2 on 2010-04-18
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get purge wicd
```
And no you don't need to be connected to purge wicd.
then
```
gksu gedit /etc/network/interfaces
```
add 2 lines so it looks like this
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
save and close
shut down connect to a wired connection and boot up
then
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install network-manager-gnome
```
When it finishes
```
gksu gedit /etc/network/interfaces
```
remove the 2 lines so it looks like this
> auto lo
iface lo inet loopback
save and close
reboot

---

### Post by 2hot6ft2 on 2010-04-18
Another way if you don't like that one is on the one with wicd go to
System > Administration > Synaptic Package Manager

Search for network-manager-gnome
and mark it for install.
Then click on File > Generate package download script
Then moving or saving the script to a usb flash drive which you can take to any linux box that is online and double clicking on it and selecting "Run" or ("Run in Terminal" if you want to be able to see when it finishes) it will download the packages to the same location as where the script is.

Then you take the usb to the machine that created the script and open Synaptic and click on File > Add downloaded packages and point it to the folder where the script and packages are to install them by clicking Apply.

The machine that creates the script is the architecture it will download them for. Not for the one you run the script on to download them.

Your choice. Either way will do the same thing in the end.
:popcorn:

---

### Post by warfacegod on 2010-04-19
Another solution, scroll to the bottom of the link, select your processor type, select location and download it. When its finished downloading, double click the package and Ubuntu should pretty much take care of the rest.



[http://packages.ubuntu.com/jaunty/net/network-manager]("http://packages.ubuntu.com/jaunty/net/network-manager")

---

### Post by anaconda on 2010-04-19
And yet another solution is just to type:
sudo apt-get install network-manager-gnome

it should work, because the install files are already on yout /var/cache/apt/archives if you haven't deleted them.

Uninstalling only uninstalls it does not remove the install files..

PS. you wouldnt needed to uninstall network manager. the wicd installed uninstalls NM after it has downloaded the wicd....

---

### Post by mavenuparker on 2010-04-19
thank ya ppl...thnx fr ur reply

i just love ubuntu.....ubuntu rocks :guitar:

---

### Post by warfacegod on 2010-04-21
Cool. We like it too!:P

So other folks can potentially use the solution, what worked?

---

