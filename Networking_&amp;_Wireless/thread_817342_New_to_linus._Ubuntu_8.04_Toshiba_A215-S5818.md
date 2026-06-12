---
title: "New to linus. Ubuntu 8.04 Toshiba A215-S5818"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by ToiletDucky on 2008-06-03
I have the Toshiba A215-S5818. I was doing a little digging and saw where others had similar problems, though different machines, with getting their Atheros wireless card to work. 

My card is showing as a AR242x 802.11abg Wirless PCI express adapter [168c:001c] ---whatever all this means lol.

I know when I start Ubuntu it says that it's using drivers for this card. It shows the box is checked and gives the idea that everything is running fine. However when I click "edit wireless networks" there are no wireless networks shown. I'll admit I'm an idiot and doing my best to learn here so please don't tar and feather me just yet. Either A) I'm missing some place where I can simply click a "refresh" style button to bring up the wireless networks or B) This card isn't working.

Any help would be very welcomed. 

Duck:(

---

### Post by ToiletDucky on 2008-06-04
bump* I'm really hoping someone here can help me get this going or I'm going to have to go back to vista.

---

### Post by cudaman73 on 2008-06-04
I don't know for sure the support of madwifi with an AR242x series card, but I know that for mine (an AR5418) I have to compile a new version of madwifi (the drivers that support atheros cards) in order for it to work. Perhaps you should try that?

[http://ubuntuforums.org/showthread.php?t=785040&highlight=atheros+ar5418](http://ubuntuforums.org/showthread.php?t=785040&highlight=atheros+ar5418)

Above is the link I used to troubleshoot my wireless.

---

### Post by ivze on 2008-06-04
First, try to see your networks in Administration->Network->Wireless Connection.
If this don't go, you definitely have troubles with your cadr driver.

Disable your current driver and try the following.
Install "ndiswrapper" application from Add/Remove, possible, that it will work. Ndiswrapper makes a linux wireless driver of a windows one. Be guided by the application.
If you have any troubles, post here.

Have luck!

---

### Post by 47_MasoN_47 on 2008-06-04
I had trouble with network manager (the default network management applet) and wireless connections.  I installed wicd [[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html]](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html]) and it works great now.  I use it on all my laptops.

---

### Post by Promaster91 on 2008-06-04
I have a similar model to you. Here is what you need.
First disable Atheros Hardware Access Layer [HAL]:
Go to System>Administration>Hardware Drivers and uncheck Atheros Hardware Access Layer then reboot.

This will download the drivers.
```

wget http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz

```
Then untar it. And open it.
```

tar xfz madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007

```
Then compile the C files.
```

sudo make

```
Then install them.
```

sudo make install

```
Then you want wifi to start every time you boot.
```

sudo gedit /etc/modules

```
KEEP THE STUFF THAT IS ALREADY THERE and add this line.
```

#Wifi Driver
modprobe ath_pci

```
Then reboot
```

sudo reboot

```

---

### Post by steveneddy on 2008-06-04
> **ToiletDucky said:**
> 
 New to linus.



I'll bet he's happy.

---

### Post by ToiletDucky on 2008-06-04
> **Promaster91 said:**
> I have a similar model to you. Here is what you need.
First disable Atheros Hardware Access Layer [HAL]:
Go to System>Administration>Hardware Drivers and uncheck Atheros Hardware Access Layer then reboot.

This will download the drivers.
```

wget http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz

```
Then untar it. And open it.
```

tar xfz madwifi-nr-r3366+ar5007.tar.gz
cd madwifi-nr-r3366+ar5007

```
Then compile the C files.
```

sudo make

```
Then install them.
```

sudo make install

```
Then you want wifi to start every time you boot.
```

sudo gedit /etc/modules

```
KEEP THE STUFF THAT IS ALREADY THERE and add this line.
```

#Wifi Driver
modprobe ath_pci

```
Then reboot
```

sudo reboot

```

Goldmaster thank you very much for the help. If I may ask does it matter where I put the #Wifi Driver part/modprobe ath_pci part? I did everything you stated then I restarted my laptop. I unplug the cord and left click on the network icon in the top right and there is no sign of anything available. I right click and only have the "edit wireless networks" option but there are no wireless networks showing.

When that didn't work, or at least isn't working yet, I tried the windows driver option with the converter. Still no joy.

---

### Post by ToiletDucky on 2008-06-04
I reinstalled ubuntu and for some reason keep getting an Error2 while trying the run the above commands.

make[3]: *** [/home/chance/madwifi-ng-r3366+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/chance/madwifi-ng-r3366+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/chance/madwifi-ng-r3366+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [modules] Error 2

---

### Post by Promaster91 on 2008-06-04
Try rebooting and then install the drivers.
Also try to run these two commands in your terminal.
```

sudo ath_pci
sudo wlan_scan_sta

```

---

### Post by Coffeeman51 on 2008-06-04
Ok this is the fix that worked for me...

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

These are detailed instructions and don't assume that you have any experience with linux or ubuntu...

Be aware that when there is a kernal update, it may disable the fix and you will have to redo it...I keep all the instructions and tar files saved in my documents folder for reference and in case I need them again...

hope this helps

---

