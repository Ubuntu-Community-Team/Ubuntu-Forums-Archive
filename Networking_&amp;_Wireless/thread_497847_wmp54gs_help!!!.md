---
title: "wmp54gs help!!!"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by -=Viper=- on 2007-07-10
ok so i was setting up my friends computer and i cant get it set up...how do i use ndiswrapper and what code do i need to input?  also is there a driver for it that i can install?   Thanks everyone!

---

### Post by -=Viper=- on 2007-07-10
> **-=Viper=- said:**
> ok so i was setting up my friends computer and i cant get it set up...how do i use ndiswrapper and what code do i need to input?  also is there a driver for it that i can install?   Thanks everyone!
bump!  does anyone know!??!?! my friend really needs to know

---

### Post by -=Viper=- on 2007-07-10
ok i just called my friend and he tried something with me.  We got this weard responce -_-"

unable to create directory /etc/ndiswrapper/wmp54gs. make sure you are running as root

That is what it said...does anyone know how to solve it :S

---

### Post by kevdog on 2007-07-10
Before going off on a wild goosechase can you post the following:

lspci
lshw -C network

Thanks

---

### Post by -=Viper=- on 2007-07-10
my friend and i cant figure out how to post it :S  can you put it how it should be....it keeps comming up as command not found

edit:  it worked on my pc but it keeps comming up as command not found on his...he has no internet tho
Edit2:  he is trying it now...we will have a solution in 2 min

---

### Post by -=Viper=- on 2007-07-10
lspci
lshw -C network
and then
michael@michael-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:09.0 Ethernet controller: Macronix, Inc. [MXIC] MX987x5 (rev 25)
02:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:0c.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0c.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:0d.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
michael@michael-desktop:~$ lshw -C network

---

### Post by kevdog on 2007-07-10
Ok, we are using command line only here.

Prepare to compile ndiswrapper from source files:
If you have internet connection skip to #4. If you do not have an internet connection (such as a wired connection do the following)
```

#1. Stick in ubuntu installation cd and wait for it to become ready
#2. sudo apt-cdrom add
#3. sudo aptitude update
#4. sudo aptitude install build-essential

```


```

cd ~
mkdir ndiswrapper

```

Download ndiswrapper-1.47.tar.gz from here: [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)
If you dont have an internet connection, then you are going to have to download this file on another computer, and then transfer it to the Ubuntu machine via a USB stick.
Place the ndiswrapper-1.47.tar.gz file in ~/ndiswrapper

Extract, compile and Install ndiswrapper
```

cd ~/ndiswrapper
tar -zxvf ndiswrapper-1.47.tar.gz <---Put in file name here
cd ndiswrapper-1.47 (Or whatever appropriate directory)
make distclean
make
sudo make install

```

Verify the ndiswrapper package has been installed correctly
```
ndiswrapper -v
```
Should get no errors here

I assume you have the wireless driver for your card (in many cases but not all the Windows XP drivers)??? If you do
```

cd (whatever directory the wireless driver is in -- Make sure you have the .sys and .inf files in this directory)
sudo ndiswrapper -i *****.inf <-----Put in file name here

```

Check if driver has been installed properly
```
ndiswrapper -l
```
Should say driver is installed --- no errors

Insert ndiswrapper module into kernel
```

sudo depmod -a <----- Make sure you get no errors after this command
sudo modprobe ndiswrapper

```

To check if module was inserted appropriately:
```
dmesg | grep ndiswrapper
```

There should be no errors listed.

Make sure module runs at boot
```

sudo ndiswrapper -m
echo "ndiswrapper" | sudo tee -a /etc/modules

```

Blacklist native bcm43xx driver which is an alternate driver -- causes conflict
```

echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist

```


Please reboot at this point. 
```
sudo shutdown -r now
```

Ok we may have to do just a few more steps at this point. What I need from you is the following:
```

/etc/network/interfaces
/etc/iftab
lshw -C network

```

---

### Post by -=Viper=- on 2007-07-10
alright ill get it for ya in the next day or two...depending when he can get back on his PC.  I will try to get it done tomarrow though...also do you have a Instant messenger?

---

### Post by izark13579 on 2007-07-11
i am the friend and we got it working thanx alot for all of your help though i look forward to working with you all some more. :p

---

