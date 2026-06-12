---
title: "NDISWrapper Install Help"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Het Irv on 2007-07-10
I give up.
Here is my Situation:

I am running Ubuntu 7.04 in a dual boot environment with Windows Xp. The only connection I have to the Internet is on the Windows side with my "WMP54GS" Linksys Card.  I have downloaded the NDISWrapper.tar.gz file while in Windows and transfered it to my Linux Partion.   I have placed it on the desktop and extracted the files to the desktop using the GUI. I then try to change to the directory by using "cd /ndiswrapper-1.47".  I then get the error "ndiswrapper-1.47 not found"   

This post will show my utter n00bess to Ubuntu and all things Linux. But Oh well.

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

### Post by VON_CAPO on 2007-07-10
**_Proceeding:_**

It works with a fresh install of Feisty.
Notice: in Feisty is not necessary to uninstall the Gnome-network-manager.

---> echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist     (copy and  paste in terminal)

Install the following packages:
-  build-essential
-  ndiswrapper-common
-  ndiswrapper-utils-1.9
The last two I am not sure if they are necessary but their install does not hurts.

Paste the ndiswrapper-1.47.tar.gz file on the Desktop

---> cd ~/Desktop     ( Desktop in Uppercase )

---> tar -xzvf ndiswrapper-1.47.tar.gz

---> cd ndiswrapper-1.47      (NOT cd /ndiswrapper-1.47)

---> make

---> sudo make install

Paste the WMP54GS Windows driver (I think your card has the same chipset than mine ( Broadcom 4318 ) on the Desktop, the files are= " bcmwl5.inf " and " bcmwl5.sys ".
You can download them from the thread located at ---> [http://ubuntuforums.org/showthread.php?t=197102&highlight=compiz18](http://ubuntuforums.org/showthread.php?t=197102&highlight=compiz18)
The link to the driver is ---> [http://ubuntuforums.org/attachment.php?attachmentid=11584&d=1150897000](http://ubuntuforums.org/attachment.php?attachmentid=11584&d=1150897000)

---> cd ~/Desktop

---> sudo ndiswrapper -i bcmwl5.inf  ( YES, the .INF one )

---> sudo depmod -a

---> sudo modprobe ndiswrapper

---> sudo ndiswrapper -m

Reboot your machine.

Good luck. I my case this method works like a charm.

**EDIT:** OOPS, KEVDOG answered first. 
                  Two responses in a few minutes...!!!  :lolflag:

---

