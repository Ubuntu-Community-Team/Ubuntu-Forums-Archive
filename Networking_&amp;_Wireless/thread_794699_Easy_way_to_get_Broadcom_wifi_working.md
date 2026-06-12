---
title: "Easy way to get Broadcom wifi working"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by n1ywb on 2008-05-14
[LIST=1]
[*]wget and unzip the driver listed in step 2 in this howto [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[*]sudo apt-get install ndisgtk
[*]sudo ndisgtk
[*]click "Install New Driver"
[*]Select the .INF file that you unzipped in step 2
[*]If you are using Network Manager it should now just work. Otherwise do whatever you do to configure your network stuff.
[*]Enjoy
[/LIST]
Worked for me, Kubuntu Hardy Heron, Dell Vostro 1400 with Broadcom 0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

Don't ask me why lspci says it's a USB controller instead of a wireless or 802.11 controller or whatever

---

### Post by cri on 2008-08-01
Worked like a charm on a brand new Dell Latitude D630 with a BCM4310 controller. Certainly the easiest way to get ndiswrapper working for your Broadcom wifi connect.

---

### Post by rlzyoner on 2008-08-01
For some reason, I have a set of steps that I follow when it comes to BCM drivers and Ubuntu and they have always worked for me.

Firstly, I get rid of the existing ndiswrapper snd bcm-43xx-fwcutter
```

sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
sudo apt-get remove bcm43xx-fwcutter
```

Now add bcm43xx to the blacklist file

```
sudo gedit /etc/modprobe.d/blacklist
```
add this line 


"blacklist bcm43xx" (without "")

Reboot the machine.

Next we download the driver (You may have this on your windows partition if dual booting)

Download from [here]("http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html") 

Now unpack the file and move it to your home directory

```
tar -xzvf WLANBroadcom.tar.gz
```
move the folder WLANBroadcom to your home directory
```
mv WLANBroadcom/ /home/username/
```

Now install ndiwsrapper from source

```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
mkdir -p ~/bcm43xx/ndiswrapper
cd ~/bcm43xx/ndiswrapper
sudo wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz
tar xvzf ndiswrapper-1.53.tar.gz
cd ndiswrapper*
make distclean
make
sudo make install
```

Now install the driver 

```
cd /home/username/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l

sudo gedit /etc/modules
```
add this line 
```

ndiswrapper
```(do not use quotes "")

```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```


**Notes**
As far as I know 1.53 is the latest release of ndiswrapper - You may want to verify this on the ndiswrapper site

Also /home/username - replace username with your own username.

Hope this is of some use to people

---

