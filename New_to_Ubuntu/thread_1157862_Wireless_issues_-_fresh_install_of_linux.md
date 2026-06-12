---
title: "Wireless issues - fresh install of linux"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by DirtyRottenScoundrel on 2009-05-13
Hello everybody.

First off, I am an absolute Linux beginner. I know how to pull up the terminal, what sudo means, and how to edit the blacklist file (but not exactly what to do with it), but that's it.

Here's my problem: I have Ubuntu 8.04.2 (the Eee PC version) on my Eee PC 1000H. I'm having issues with doing anything with Wifi. It's a dual boot system and the wireless works fine in XP, but not in Ubuntu. I have a Atheros card and yes it is enabled in the BIOS.

When trying to add a wireless connection via a manual configuration, I do not even get an option for wireless networks. Just a wired connection or point to point connection.

I have found some other people with this problem, but they all recommend installing new drivers, but all of the links are broken and are at madwifi.org, plus I could not follow the instructions on blacklisting exactly 100%.

Thanks in advance for the help.

---

### Post by DirtyRottenScoundrel on 2009-05-13
Any suggestions are welcome. Even a link to another thread so I can look into it. I'm just so inexperienced that I'm not sure what I need.

---

### Post by lkraemer on 2009-05-13
This should get you going:
```

lshw -C network 

```
Make sure there is a reference to Atheros AR242x, then proceed....

[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

Download the latest Madwifi from:
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
(madwifi-hal-0.10.5.6-current.tar.gz)


madwifi-hal-0.10.5.6-current.tar.gz

    * Extract the files
    * Make sure your linux headers and build-essential packages are installed: 

sudo apt-get install build-essential
sudo apt-get install linux-headers-$(uname -r)

    * Unload any drivers already running. 

sudo ifconfig ath0 down
sudo ifconfig wifi0 down

    * Change to the directory where you extracted the driver. 

cd <directory_where_driver_unzipped>

    * From that directory, run the installation scripts: 

cd scripts
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh $(uname -r)
cd ..

    * Complete the installation by compiling the source and installing it. 

sudo make
sudo make install

    * Add the installed drivers to your system. 

sudo modprobe ath_pci

Following this, Network Manager was able to see the wireless card and I was able to configure everything else (WEP / WPA key, etc.) from there. 
Complete instructions are available at MadWifi UserDocs. 
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

REF:
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
[http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/)
[http://madwifi-project.org/wiki](http://madwifi-project.org/wiki)



Just remember that when you download a new kernel you will have to repeat
the process each and every time, and if you pick the previous Kernel from
the Grub menu on bootup, you're Wifi will be functional.......
REF:
[http://ubuntuforums.org/showthread.php?t=1142199](http://ubuntuforums.org/showthread.php?t=1142199)

You can also search the Forum for HOWTO: & AR242x   to find some guides
for your version Ubuntu.

lkraemer

---

### Post by TeoBigusGeekus on 2009-05-13
...and if that doesn't work, try wicd.

---

### Post by DirtyRottenScoundrel on 2009-05-14
cd scripts
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh $(uname -r)
cd ..

What is the first line here? When I type it, I get "No such file or directory"

---

### Post by DirtyRottenScoundrel on 2009-05-14
Well, I figured out that I needed to be within the unzipped directory, but now I'm having issues with these steps:

sudo ifconfig ath0 down
sudo ifconfig wifi0 down

and:
ifconfig ath0 up

in that the terminal tells me I don't have them or something to that effect. I can't remember now. I'm having to travel between two different computers. (in two different locations)

---

### Post by TheDilettante on 2009-05-14
Could you be specific about the trouble you're having with the commands?

---

### Post by TheDilettante on 2009-05-14
I don't remember how it works in the latest release - is there an entry in the restricted drivers manager (system/admin/restricted drivers)?  if so, go ahead and disable them.  reboot, then try the ifconfig steps again.

see if that helps.  and i can heartily recommend wicd, should all else fail.

(am at work, so doing this from memory)

---

### Post by rustutzman on 2009-05-14
Go to [http://www.array.org/ubuntu/](http://www.array.org/ubuntu/) and follow the instructions to update your kernel to that version. With that everything should work. That is how I got everything on my 1000he to work.

Russ

---

### Post by lkraemer on 2009-05-14
OK, First things first.....Is your Wifi a Atheros AR242x?  YES/NO.

If so, then you should have read the Beginners HOWTO:, then downloaded
the Software, and extracted it into a folder somewhere.  Then you should
have changed to that folder in a Terminal Window....etc...

From there you can do a:
```

iwconfig
lshw -C network

```
to see what is being detected......then you are to unload any drivers
already running for what was detected by iwconfig.  I guess I assumed
too much, thinking you knew what your Wifi was detected as.  It could be
ath0, wlan0,etc.....  but the sudo commands are just taking your wired
and Wifi down.....You are the ONLY one that can know what those are being
detected as... because you haven't posted "lshw -C network" or "iwconfig".


Now we need the following run, one line cut & pasted at a time and post
results from each command:
```

lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwconfig 
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```

Once we have that information we can know what is already loaded and
maybe how to get it running.

lkraemer

---

