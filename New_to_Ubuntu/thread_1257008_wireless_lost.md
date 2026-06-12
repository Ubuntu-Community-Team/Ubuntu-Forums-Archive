---
title: "wireless lost"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-09-03
I did a kernel update last night and system wouldn't boot so I reinstalled ubuntu. Now wireless won't connect-it was recognized right away before. I installed drivers but no luck it is a BCM4306 wireless. By the way I got the GRUB update from this website and I warn everyone it can make your system unbootable. I followed the directions VERY carefully and still lost everything.
[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)
Don't use unless you are a lot smarter than me!

---

### Post by LowSky on 2009-09-03
Not to be mean, but why did you install software, that you really don't need if the older version is stable and works?

Now to the wireless... go to 
System, Administration, Hardware Drivers
enable the driver, it should be listed.

---

### Post by LewRockwell on 2009-09-03
> **LowSky said:**
> Not to be mean, but why did you install software, that you really don't need if the older version is stable and works?

Now to the wireless... go to 
System, Administration, Hardware Drivers
enable the driver, it should be listed.

Furthermore, your experience is a wonderful testimonial for our repeated...Repeated...REPEATED...

Shouting and yelling to back-up, Back-up, BACK-UP


Unless, of course, you don't mind "losing everything"

not that you initially lost anything...

at least not until you wrote over all of it with your re-install...

{{sigh}}

.

---

### Post by cmcanulty on 2009-09-04
I had everything backed up and the reason I downloaded it is because it said there were many improvements in the new kernel also I was getting error messages with any packages I installed.

---

### Post by lkraemer on 2009-09-05
From your post, it appears you installed Ubuntu 9.04.
You didn't say if you have a dialup or ethernet connection
avaliable, but this post will get your Wifi working for the
Broadcom card.

Open a Terminal Window and use these commands to get
more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted.
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist     OR for 9.04 use:
                                  cat /etc/modprobe.d/blacklist.conf
iwconfig
cd /
cd /lib/firmware
ls -alt
cd /b43
ls -alt

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

(You are looking for any *.fw files in /lib/firmware/b43 or
/lib/firmware/b43legacy and if you had a Wired LAN connection and
went to SYSTEM -> ADMINISTRATION -> HARDWARE DRIVERS and enabled the
Hardware Drivers with a LAN connection there should have been folders
created and files inserted for the Restricted Drivers to work.)

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.

Once you have the Manuf & Hardware info, use Search or Google for
"HOWTO: & 4318" or whatever your Broadcom model is to find a good guide.

It will be your decision on what to use.

For #2 above:
If you just need the Broadcom firmware for b43xx it can be found on
the internet.

Now search through dmesg for any references to Broadcom firmware,
looking for missing firmware or what is causing the Wifi to
not function. There might be a clue. Is the firmware installed
in /lib/firmware or possibly in /lib/firmware/b43 Once again
dmesg might give you a clue. ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)

If lsmod shows module b43 and others installed you will
need to blacklist them, since you are going to be using b43xx.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist
and add the necessary modules to blacklist.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
Post the output of iwconfig above.

#3 doesn't appear to be supported by 9.04 according to searches of the forum.

REF:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[http://ubuntuforums.org/showthread.php?t=870086&highlight=HOWTO%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=870086&highlight=HOWTO%3A+Broadcom)


I just stuck with the windows drivers.
PM me if you want that info.

lkraemer

---

