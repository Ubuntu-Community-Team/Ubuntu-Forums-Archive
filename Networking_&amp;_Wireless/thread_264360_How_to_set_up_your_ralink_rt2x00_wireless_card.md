---
title: "How to set up your ralink rt2x00 wireless card"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by Salmonman on 2006-09-24
Im not making any guarantees about the instructions in this article working, but it worked for me :D It's basically an adaptation of an article I read in Personal Compter World (in the Hands On > Linux section) along with the ubuntu forum post on rt61 cards [http://ubuntuforums.org/showthread.php?t=132980](http://ubuntuforums.org/showthread.php?t=132980). I literally mixed and matched the two until something worked - the only thing I need now is a bonafied wakeup script so I don't need to repeat it after every reboot :confused:

Some things to note perhaps are that I am running default kernel in
**Dapper Drake 6.06**
My wireless card is the
**Edimax EW-7128g**
(RaLink chipset & driver rt2500) and I use
**WEP**
(WPA not supported ).

**The tutorial**

DO NOT EVER USE GNOME's OWN NETWORKING TOOL AFTER THESE STEPS.

step 1
on a computer connected to the internet, go to [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

now check whether your kernel is new or old.
ubuntu breezy badger uses an older kernel than dapper.

New - download the 2.x driver series that matches your card. it is recommended that you download the latest (and greatest) nightly CVS build from serialmonkey.

Old - download the 1.x driver series. again, go for the latest build.

step 2
check the card chipset. there is a list of hardware under the rt2500, rt2570 and rt61 that have been tried and tested in different versions of linux. if your card isn't there, you can still have a search around for potential support on [http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

now download the one that matches - for example, mine is an Edimax EW-7128g and it is a rt2500 - so I downloaded the latest rt2500 CVS nightly build.
step 3
extract and install...
	```
$ tar xfvz rt2500-x.x.x.xx-tar.gz
```
you may also need what ubuntu calls "build-essential" in order to compile the driver source. to do this, type...
	```
$ sudo apt-get install linux-headers-386 gcc-3.4 build-essential
```
ok, change to the directory in which you downloaded the rt2x00 driver...
	```
$ cd rt2x00...[wherever your driver is].../Module
```
and now start building it with "make"...
	```
$ make
```
now the newly made module has to be copied into the headers
	```
$ sudo cp rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/Wireless
```
and now attempt to load the driver module...
	```
$ sudo depmod -a
$ sudo modprobe ra0
```
now you can check to see if the driver was loaded...
	```
$ iwconfig
```
that should display information about your ra0 network interface.

step 4 - **_N.B. MUST be repeated after EVERY reboot_**
this is the last step, and this details information such as "essid" - your access point's/router's name, and the WEP key...
        ```
$ sudo dhclient ra0
$ sudo iwconfig ra0 essid <my essid>
$ sudo iwpriv ra0 set NetworkType=Infra
$ sudo iwpriv ra0 set AuthMode=SHARED
$ sudo iwpriv ra0 set EncrypType=WEP
$ sudo iwpriv ra0 set DefaultKeyID=1
$ sudo iwpriv ra0 set Key1=<my wep key>
$ sudo iwpriv ra0 set SSID=<my essid>
```
and finally connect to your access point with...
	```
$ sudo dhclient ra0
```

---

### Post by JebusWankel on 2006-09-24
For the wake up script check the readme file that came with the driver. It will probably have instructions, though not necessarily a script.

---

### Post by Salmonman on 2006-09-25
> **JebusWankel said:**
> For the wake up script check the readme file that came with the driver. It will probably have instructions, though not necessarily a script.

Thanks JebusWankel.

I've tried following the instructions in the Modules directory of the driver source - but time after time at reboot I've found the boot sequence hang at "Initialising network" ](*,)

After that I never had the guts to try their script to run at boot. I'm sure there must be a way to have **step 4** kick in during boot because I know that works.

---

