---
title: "How to install a driver tar.gz from usb device?"
date: 2014-02-05
forum: Networking &amp; Wireless
---

### Post by zok_Halsen on 2014-02-05
Well I'm having this little issue with my dual i210 lan port's, I've acquiered drivers from Intel's support page for the adapters and I'm wondering how I could be able to install the tar.gz file witch is located on a usb, any help is appreciated! 
**(**please be very specific and detailed, I also do not know how to locate the usb's path[B])


[/B]Thanks in advance!

---

### Post by praseodym on 2014-02-05
Do you have a graphical interface or is it a server?

Check:
```

sudo fdisk -l
```with and without stick. If there is a GUI then unpack the tar.gz via double-click to "Downloads" and change the directory:

```
cd ~/Downloads/[COLOR="#FF0000"]Nameofthe folder[/COLOR]
```
Then check
```

make
sudo make install
```

---

### Post by fdrake on 2014-02-05
first what are you trying to install ? can you post the url of the download link and the name of the driver?
also extract the archive and find for a reademe/installation text file that will guide you for the installation. 
how to install

---

### Post by chili555 on 2014-02-05
Are you trying to compile igb-5.0.6.tar.gz? What trouble are you having with your device? Maybe we can help.

---

### Post by zok_Halsen on 2014-02-06
I'm running on a p9d ws board, its server 13.10(answer to praseodym, my nics are i210  (dont think its the i210-T because its a workstation)and I've seen others having this issue, for some reason I need to apt-get install make to install the make funcion to install the driver, I've mounted the usb to a folder in media and unziped the tar.gz entered the dir that it created, but I cannot do the ./configure it only tells me that theres no file or the make and make install and theres no internet so i cant get it, I dont have a spare networkcard. OS is fresh so if anyone could compile it to the absoulete latest kernel (heard it should support the nics by default) I'll be checking in here for a while so expect answers to all your future questions, I'm not too femiliar with using linux systems as you may allready have guessed but I have been using it before back in 2012 with no problems, 

Fdrake: This is the file I'm trying to install, [here]("http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/13663/eng/igb-5.0.6.tar.gz&lang=eng&Dwnldid=13663&DownloadType=Drivers&OSFullname=Linux*"), I've opened the readme file with nano but its seem to be empty.

Chili555: My nics are detected but they're not turing on and on boot it keeps waiting for configuration, cabels and everythings working but I've seen others with the same nics having the same issues.

---

### Post by chili555 on 2014-02-06
To compile the file is really simple, *if you have a working internet connection!!!* All you need to do is:```
sudo apt-get install build-essential linux-headers-generic
cd ~/igb-5.0.6/src
make
sudo make install
```Get the system to unload the old driver and reload the new:```
sudo modprobe -r igb && sudo modprobe igb
```And see if you can get an IP address:```
sudo dhclient eth0
```Simple, eh? Sure, if you have a working internet connection! But, since you haven't one, it is just about impossible to download the file, the build tools, the kernel headers and their dependencies and the dependencies of the dependencies, etc., etc.

It seems far preferable to me to at least try to troubleshoot your current setup rather than just throw a new driver at it.

I assume your server is without a GUI desktop and therefore without Network Manager. Networking is therefor controlled in /etc/network/interfaces. May we see your file? ```
cat /etc/network/interfaces
```

Also, the module igb is included in 13.10 by default. What is it doing under the hood?```
dmesg | grep -e igb -e eth0
```

---

### Post by zok_Halsen on 2014-02-06
Cat:
> auto lo
iface lo inet loopback

auto p2p1
iface p2p1 inet dhcp
for some reason dmesg is giving out: > [2.332074] IPv6: ADDRCONF(NETDEV_UP): p2p1: link is not ready
There's absolute no reason for me to be running IPv6, cant seem to find anything that would be usefull or network related in the dmesg.
ifconfig -a, display's both the nic's but as p2p1 and p3p1, the haven't recived any addresses.

---

### Post by chili555 on 2014-02-06
How about:```
dmesg | grep p2p
```

---

