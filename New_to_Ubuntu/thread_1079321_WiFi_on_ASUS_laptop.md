---
title: "WiFi on ASUS laptop"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by shoot2kill on 2009-02-24
i have an ASUS X51RL which i am trying to install ubuntu on, everything seems to work fine, except wifi. 

i cant figure out wether it is the actual wifi that isnt working or wether it is the hardware button that enables the wifi that isnt working..

could anyone point out how i can find out, and how i can resolve this problem??

NOTE: i have no internet access on the laptop, but i do have access via another PC, where i can use Pen drive for transfer of files..

---

### Post by ja660k on 2009-02-24
you need to find out what brand/model your wifi card is,
please post output of;
```
lspci
```

then you need to find drivers for the wifi card and patch them using 
ndiswrapper.

---

### Post by shoot2kill on 2009-02-24
think this is the only relevent information...

---

02:00.0 Ethernet Controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by ja660k on 2009-02-24
yep, thats it.

do you still have windows partition? if so navigate to that file system and go to program files->atheros->driver (or somehting simelar to that)
and take the .inf

if you dont have the windows partition, you will need to download a driver for it. (cannot find one for the moment, search on google. i will be too)


when you get that install
```
sudo apt-get install ndiswrapper
```
and 
```
sudo apt-get install ndisgtk
```

run ndisgtk and install the driver. 
reboot, and hopefully that should do it!


OR you can look into madwifi. i dont know how to use it, but i hear it works

---

### Post by shoot2kill on 2009-02-24
Ok, when i get the driver, is there another way of installing ndiswrapper as i have no internet access through ubuntu until i get wthe wifi working..

is there a file i can download and install manually ??

---

### Post by ja660k on 2009-02-24
oh right,
you can 'force' your laptop to connect to internet via wired connection by using

```
sudo dhclient eth0
```

i guess you could download the package from ndis website and copy it over and compile it in ubuntu?

ndis wrapper download:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

---

### Post by shoot2kill on 2009-02-24
well, i am currently in uni, and cannot connect to wired network...

i will try the link you posted and let you know.. 

thanks..

---

### Post by ja660k on 2009-02-24
im not sure if i will be online to help but
im sure if you will find something on google that will be helpfull.

goodluck mate.

---

### Post by avtolle on 2009-02-24
Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) for another way to get your Atheros wireless card going (if you are using 8.10, that is). It has worked for me twice.

---

### Post by Scunnered on 2009-02-24
shoot2kill

Did you get the laptop from Linux Emporium.  I got one from them and like you had initial problems with wireless set up.  They offered excellent support and talked me through the proceedure. I dont remember having to install drivers for the AR242

Everything now works smoothly.  Suggest that if you did not buy from the Emporium you ask your supplier for assistance and see how you get on.

---

### Post by shoot2kill on 2009-02-24
> **avtolle said:**
> Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) for another way to get your Atheros wireless card going (if you are using 8.10, that is). It has worked for me twice.

Thanks for this.. worked great...

---

