---
title: "[SOLVED] Wireless adapter issues li1818"
date: 2007-12-21
forum: Networking &amp; Wireless
---

### Post by TheGreatSage on 2007-12-21
Hi all

There have been a few threads started by users experiencing the same problems as myself with the onboard wireless adapter for the fujitsu siemens li1818.

I have scoured the net and tried various suggestions, using ndiswrapper etc, but I am unable to get the device active.

I see no wireless device when I type iwconfig. ndsiwrapper is sucsesfully added to etc/modules, but no joy.

The details of the wlan are 
AMILO Li 1818
Integrated Wireless LAN (WLAN) solution for IEEE 802.11
a/b/g

Any help much appreciated

Regards


Jez

---

### Post by TheGreatSage on 2007-12-21
Ive got the apdapter working now after a lot of reading, tinkering and rebooting. :)

I am having problems getting the laptop to connect to my router using the GUI. I have tried using terminal, but for some reason, terminal doesnt like my wep key?
I can connect with security disabled, so I know the drivers are now working.

sudo iwconfig wlan0 essid <AP NAME> ap <AP MAC ADDRESS> key <KEY IN HEX>

I am using this command to setup a connection, but as soon as I use a key, I get unrecognised wireless request "my key"

I am guessing that I am using the wrong command.... ie key as key seems fine, but maybe ket is not the option for the type of key I am using?

:confused:

Anybody?

---

### Post by TheGreatSage on 2007-12-21
I was barking up the wrong tree from the start,as I was trying to install ndiswrapper (which I hadn't even downloaded), but didn't have build-essential installed.

Thanks goes out to victorbrca , as I followed most of his advice in another thread on the forum.
Here is what I had to do for those who may not of found a solution.

First, I should of installed build-essential 
```
sudo aptitude update
sudo aptitude install build-essential
```


Make a directory & then download drivers and ndiswrapper.

```
cd /home
mkdir downloads
cd downloads
wget http://digitaltelecomsltd.com/apps/SiS163u.sys
wget http://digitaltelecomsltd.com/apps/sis163u.inf
wget http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz

```

Unzip thedownloaded ndswrapper file  & install.
```
tar -xzvf ndiswrapper-1.50.tar.gz
cd ndiswrapper-1.50
make distclean
make
sudo make install

```

Install drivers.
```
ndiswrapper -i sis163u.inf

```

Check if the driver is being used by device
```
ndiswrapper -l
```

The result should be

```
sis163u : driver installed
         device (0BF8:100F) present
```

Then, load the module into the kernel with
```
modprobe -i ndiswrapper

```
Let ndiswrapper associate the right device file with the driver
```
ndiswrapper -m

```
Typing the following, you should see your wirless network.

```
iwlist wlan0 scan

```

I used the following command, but It doesn't seem to be working, as I always have to manually start Wireless networking.Infact, I have reversed the process, to see if it was actually doing anything.
Once the test editor appears, hit esc i to insert text the add ndiswrapper on a new line at the end of the file. The hit esc : wq <enter>( I had issues here as I'm not familliar with vim)

```
sudo vim /etc/modules
```

I also tried entering my wep keys using terminal as I was having issues using the gui.This did seem to kick start my connection.

```
sudo iwconfig wlan0 essid <AP NAME> ap <AP MAC ADDRESS> key <KEY IN HEX>
```

I can now connect, but I have to click on the network icon at the top right of screen and select 'connect to other wireless network' and input details there.Very wierd, as my network doesnt seem to be broadcasted when I look via the gui or if i type iwlist  scan. Not ideal, but it will do for now.

---

