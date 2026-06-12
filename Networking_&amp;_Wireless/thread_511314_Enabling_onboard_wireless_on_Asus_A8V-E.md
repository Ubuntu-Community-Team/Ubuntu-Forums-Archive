---
title: "Enabling onboard wireless on Asus A8V-E"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by fragility14 on 2007-07-27
I'm using Kubuntu 64bit edition, and it is fantastic, except that I still have not taken the time to enable my onboard wireless. My motherboard type is Asus A8V-E Deluxe, which has an onboard Marvell 88W8310 wireless controller.


Hopefully there are simple directions for taking care of this, though I havnt been able to find any on google...thank you for any help!

---

### Post by fredj on 2007-07-27
We need much more information. Open a terminal and type sudo lshw -class network. Post the output
from that here. What sort of security does your wireless network use, is it WEP or WPA.

---

### Post by kevdog on 2007-07-27
My guess is that you will have to use ndiswrapper, do you have a 64-bit Windows driver??  This is a must for ndiswrapper.

---

### Post by fragility14 on 2007-07-29
description: Ethernet controller
       product: 88W8310 and 88W8000G [Libertas] 802.11g client chipset
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@00:07.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:da000000-da00ffff iomemory:da010000-da01ffff irq:3




so...it sees that its there, but on network manager it doesn't show up at all...I dont have the windows 64 bit driver but imagine I can get one once I know what to do with it.

---

### Post by kevdog on 2007-07-29
Get the 64 bit driver (with the .sys, and .inf files) and then follow the instructions for installing ndiswrapper below  (read through it a couple times before starting -- it really will not take you that long):

First there are a few things you need to do to compile from source -- install the build-essential package along with the linux header files.  Here is how to do this in case you dont have an internet conneciton:

```
If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```


Ok, next grab the ndiswrapper source files from: _[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)_
You want ndiswrapper-1.47

Working at command line
```
cd ~
mkdir ndiswrapper
cd ndiswrapper
Place the ndiswrapper-1.47.tar.gz inside this ~/ndiswrapper

```
To proceed
```
tar -zxvf ndiswrapper-1.47.tar.gz
cd ndiswrapper-1.47
make distclean
make
sudo make install
```

Verify installation with
```
ndiswrapper -v
```
I cant remember the exact output but make sure you dont get any errors.

Next create and place your Windows XP wireless driver into ~/driver:
```
cd ~
mkdir driver
cd driver
```

Ensuring the ***.sys and ***.inf file for the WinXP driver are in the~/driver directory:
```
sudo ndiswrapper -i *****.inf
```

Verify installation with:
```
ndiswrapper -l
```
Make sure no errors are reported and you get something like:
> 
bcmwl5: driver installed
device (14E4:4320) present


Ok, to insert the ndiswrapper module into the linux kernel:
```
sudo depmod -a
```

Ensure you dont get any errors when running this command.  Then:
```
sudo modprobe ndiswrapper
```

To verify there wasnt any errors:
```
dmesg
```
and look for something like:
> ndiswrapper version *version* loaded

Next lets make an alias for wlan0 associated with ndiswrapper
```
sudo ndiswrapper -m
```

And ensure that the ndiswrapper module is loaded at boot:
```
echo "ndiswrapper" | sudo tee -a /etc/modules
```

I recommend rebooting at this time.
```
sudo shutdown -r now
```

Additional modifications may be needed to your /etc/network/interfaces and /etc/iftab files, since the wireless interface we are know using is going to be known as wlan0, and not eth0, eth1, ath0, etc.  Im not sure how your previous setup was configured, hence possibly the need to further alter these files.  I also recommend that you turn off any router encryption (WEP,WPA), and any MAC filtering at the router for the time being until we can verify basic connectivity.  We can build these complexities into the setup once everything is up and running.

---

### Post by fragility14 on 2007-07-29
I got as far as installing the .inf file, when I tell it to install it says it is already installed, when I do ndiswrapper -l it says the driver is invalid...

got it of of asus' website, and it is for 64 bit windows, things seem to work fine, it said something weird about the version earlier on

> brad@brad-desktop:~/ndiswrapper/ndiswrapper-1.47$ ndiswrapper -v
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/nd                     iswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)

---

### Post by kevdog on 2007-07-29
Remove all the previous drivers installed and then install again

cd /etc/ndiswrapper
sudo rm -R *

Then
sudo ndiswrapper -i *****.inf  <----As before

Then check with 
ndiswrapper -v

---

### Post by fragility14 on 2007-07-30
it's saying I need version 1.9, which I guess it means of utilities because I got that from adept...

now when I do 

ndiswrapper -v

it says "Utils Error, no version specified"


tried to get all of the different packages off of adept and get

utils Error: no version specified!
driver modinfo: could not open ndiswrapper: No such device

---

### Post by fragility14 on 2007-07-30
it actually did work after reboot, despite not going through the later steps and ndiswrapper -v not working

---

### Post by kevdog on 2007-07-30
So everything works OK now???

---

### Post by patrickfromspain on 2007-07-30
just for the record... the onboard wifi card is CRAP. I got a RT2500 with which I get much better reception..

---

### Post by fragility14 on 2007-07-30
actually, I had to move the computer, and now after rebooting it does not work anymore, but it still says its installed with ndiswrapper ****.inf and it says it is already installed, I am going to go through the other steps, because it had started working at random and once it worked I didnt mess with it anymore....


ndiswrapper -l

shows the driver as being installed

sudo depmod -a does nothing but goes to the next command line

sudo modprobe ndiswrapper

"no module found"

since it says that the driver is installed but isnt showing, I am going to not mess around more till someone has an idea...this is really odd...it was working just earlier in the day


dmesg gives a bunch of weird errors about IDE and HDB (using SATA)


checked /etc/network/interfaces and it showed a list including wlan0 looking just like the other devices shown

---

### Post by kevdog on 2007-07-30
Something is strange

Try a reboot, and if that doesnt work, please post

ndiswrapper -v

---

### Post by User X on 2007-08-02
I am in the same boat, I have the A8V-E Deluxe.

I am running ndiswrapper 1.47 with the XP drivers that came on the Asus CD.  I get the drive loaded, and device present note when doing an "ndiswrapper -l" but when I try to connect to my ssid I never get assigned an IP address.  It reports I am connected to the network but I can't access anything.  I can't even ping the router I am connected to...?  I have tried wifi radar, network manager, and wicd to no avail.

---

### Post by tsagas on 2007-09-27
___

---

