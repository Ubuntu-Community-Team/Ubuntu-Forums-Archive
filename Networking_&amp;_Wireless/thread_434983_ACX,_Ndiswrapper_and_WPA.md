---
title: "ACX, Ndiswrapper and WPA"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by rebird242 on 2007-05-06
I had a hell of a time getting my ACX 111 card to work with WPA so I thought Id make a posting. A lot of this information is in different sources so I thought I would combine them. Note: the Ndiswrapper manual installation was required due to the version of Ubuntu I was trying to install with had the old version, this may have changed...

1. get the windows driver for your card... if you cant find it i suggested getting the dlink dwl g520+ driver rev a. 

2. download the latest version of ndiswrapper. 
[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

3. Remove any version of Ndiswrapper presently installed

sudo modprobe -r drivername 
sudo rmmod ndiswrapper 
sudo apt-get remove ndiswrapper-utils 
sudo rm -r /etc/ndiswrapper/ 
sudo rm -r /etc/modprobe.d/ndiswrapper

4. Blacklist bad ACX drivers
lsmod | grep acx
sudo rmmod acx
sudo gedit /etc/modprobe.d/blacklist

 Add a new list at the end of the file like this: 

# drivers wireless ACX
blacklist acx

5. Use Synaptic to make sure that your kernel headers are installed

6. Use Synaptic to get package build-essentials

7.
sudo tar xvzf ndiswrapperfilename.tar 
cd /home/username/ndiswrapperfilename/ 
sudo make 
sudo make install

8.Load driver
cd /the_dir_you_put_the_wlan_drivers_into/ 
sudo ndiswrapper -i driver.inf (fill out your own drivers for driver.inf) 
sudo ndiswrapper -l (shows if the driver is installed)

9.sudo modprobe ndiswrapper 
10.sudo ndiswrapper -m
11. sudo gedit /etc/modules
    * Add the following module to the list 

ndiswrapper
12. For WPA use the built in network manager...

---

### Post by danvan on 2007-05-25
Thanks. You made my day.
It works like a charm =D

---

### Post by dukex64 on 2007-06-25
Awesome, this should be a sticky!  I found this guide after 2 days of fiddling around and searching and asking for help on IRC.  Nothing worked until this guide.  Thanks.

---

### Post by ironyCurtain on 2007-06-25
Bravo, this worked beautifully for me on my Zyxel Zyair G-302 v2 which uses the Texas Instruments ACX 111 chipset.  I tried for a long time to get this working with wpa_supplicant but that turned out to be quite the quagmire.

For WPA to work you'll need to create a file /etc/default/wpasupplicant containg only "ENABLED=0", sans quotes.

Also, before I could get the connection to work in NetworkManager I had to run the following command:

```
sudo /etc/init.d/dbus restart
```

and make sure that wlan0 is up:

```
sudo ifconfig wlan0 up
iwconfig
```

After that everying worked swimmingly with WPA using NetworkManager.

---

### Post by rayashworth on 2008-05-02
I just cannot seem to get rid of acx.

ray@sink:~$ ndiswrapper -l
usr11g : driver installed
	device (104C:9066) present (alternate driver: acx)
ray@sink:~$ 

I have a US Robotics 805416 PCI adapter.  It was working fine using driverloader, but I dont want to pay for that.  Install 8.04 killed it.

Thanks
Ray

---

### Post by rayashworth on 2008-05-02
Turned off WEP and all is fine now.  I have a new router on the way, so I will take this up again when I have more time.

Regards
Ray

---

