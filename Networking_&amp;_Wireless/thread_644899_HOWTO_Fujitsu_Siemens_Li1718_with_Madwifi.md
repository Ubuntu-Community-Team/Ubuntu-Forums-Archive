---
title: "HOWTO: Fujitsu Siemens Li1718 with Madwifi"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by darrell on 2007-12-19
First of all, I should acknowledge the work of damagedspline and others: [http://code.google.com/p/fscamiloa16xx/](http://code.google.com/p/fscamiloa16xx/) and on these and other forums. Many thanks, you got me going with my laptop. Also, I hope it is in order to post this in a new thread, but I want it to stand out, especially as it is not distribution specific, and should work with little adaptation for users of other linux distributions.

Owners of the above laptop have two problems to overcome before getting the wireless LAN to work: an Atheros chip as yet unsupported in Madwifi, and a wireless on/off button which must be made to work.

There are now patched sources out there for the two necessary kernel modules which make this approach possible. Again, thanks to the patchers/maintainers. There is no longer any need to install the Windows driver via ndiswrapper.

I have tested the below with a fresh install of gutsy, but the basic procedure should work, give or take the names/locations of the various files, on most distributions (not just Ubuntu). It is however, quite specific to the hardware - the acerhk module and the patched madwifi will only work on 32 bit machines. It works on a Li1718 machine, and maybe on some similar ones, but I have no way of testing. Maybe others can report.

On with the HOWTO:

1. Make sure your system is up to date, and includes the necessary tools to compile the new kernel modules:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```

2. Get the patched source:
```
wget http://www.cakey.de/acerhk/archives/acerhk-0.5.35.tgz
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
```

3. Build the new Madwifi modules, to enable support for the Atheros AR5007EG card:
```
tar xfvz madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
sudo make install

```

4. Build the new acerhk module, needed to enable the wireless button on the machine:
```
cd ..
tar xfvz acerhk-0.5.35.tgz
cd acerhk-0.5.35
make
sudo make install
```

5. Create a file containing instructions which the system will carry out when the acerhk module is loaded - see comments in the file:
```
sudo gedit /etc/modprobe.d/amilo_special_keys.modprobe
```
and paste the following into the file, save and exit
```
# set up kernel module acerhk to enable Fujitsu Siemens Amilo Li1718 special keys
# and enable wireless when the module is inserted.
# NOTE: to have the wireless hardware disabled until you press the wireless key on the laptop,
# simply replace "echo 1" with "echo 0" in the command below. 

install acerhk /sbin/modprobe --ignore-install acerhk force_series=6805 autowlan=1; echo 1 > /proc/driver/acerhk/wirelessled
```

6. Remove the acerhk module which is shipped with Ubuntu:
```
sudo rm  /lib/modules/2.6.22-14-generic/ubuntu/misc/acerhk.ko
```

7. Rebuild the module dependencies database 
```
sudo depmod -a
```

8. Tell the system to load the acerhk module at boot time - it won't otherwise, as it's not actually an Acer laptop!
```
sudo gedit /etc/modules
```
add on a new line at the end of  this file, then save and exit:
```
acerhk
```

9. restart your machine and you should have a working wifi card.

---

### Post by daydream on 2008-01-11
Many thanks for this guide. It's just perfect! And it works on Amilo li 2727 as well. I finally have my atheros wireless card working. I now have to figure out how to add security to it. My internet connection is only working when I switch off firewall... :(((

---

### Post by ltltnm on 2008-02-17
Thank you for this guide. It works perfectly on my Amilo Li1718. The only problem is that every time the system is updated with a new kernel version, I need to re-perform the steps. Is there a way to make the changes stable?

      L.

---

### Post by darrell on 2008-02-22
> **ltltnm said:**
> Thank you for this guide. It works perfectly on my Amilo Li1718. The only problem is that every time the system is updated with a new kernel version, I need to re-perform the steps. Is there a way to make the changes stable?

      L.

What we're doing here is taking non-ubuntu source code for two kernel modules and compiling the modules to work with the specific kernel installed on our machines at the time of the compilation. This is the kind of nitty-gritty work which is done by the ubuntu developers for hardware which is officially supported, and every time they release a new kernel, they will release matching kernel modules if necessary.

Because we have non-supported hardware, we have to do this ourselves. So the short answer is "No" :(

I just make sure that I have my wired network cable handy before I update the kernel - then I can come here and follow my own instructions!

Beware a future version of Ubuntu if it uses kernel 2.6.24, as the patched madwifi we're using has been reported not to work with this kernel (see [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) ). 

From the same source, Official support for this wireless card is expected in madwifi at some point, and hopefully from there it will make it into the Ubuntu madwifi package without too much delay. No-one will put the current solution in an official release, as it won't work with 64 bit machines.

As far as the acerhk fix, I'm not sure this will ever make it into any distribution package release, as this is again 32 bit machine only, and probably affects a pretty small number of people.

Darrell

---

### Post by expertoweb on 2008-03-12
Thanks for all the info. I run gOS that is a variation of Ubuntu with kernel 2.6.22-14 on an Amilo li1718. No changes made on these instructions and it works like a charm. However I could not make it work under PCLinuxOS with a kernel 2.6.22-15. One of the modules didn't insert well. Any help?

---

### Post by moma on 2008-03-20
Many thanks for the guide.

These changes are required for Ubuntu 8.04: 

**Step 4. Build the new acerhk module, needed to enable the wireless button on the machine:**on 
On Hardy Heron the acerhk-0.5.35 requires a minor change in the Makefile, otherwise the compilation fails.  Open the Makefile and change _the first ocurrence_ of word "CFLAGS" to "EXTRA_CFLAGS" around the line number 17, like this.   
Change
```
CFLAGS+=-c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe
```
to 
```
EXTRA_CFLAGS+=-c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe
```

I created a patch for it. You can simply do 
$ [COLOR="SeaGreen"]cd acerhk-0.5.35[/COLOR]

# Get and apply the patch
$ [COLOR="SeaGreen"]wget [http://www.edbl.no/tmp/acerhk.Makefile.patch](http://www.edbl.no/tmp/acerhk.Makefile.patch)[/COLOR]
$ [COLOR="SeaGreen"]patch -p0 < acerhk.Makefile.patch[/COLOR]

$ [COLOR="SeaGreen"]make[/COLOR]
$ [COLOR="SeaGreen"]sudo make install[/COLOR]
-------------

**Step 6. Remove the acerhk module which is shipped with Ubuntu.**  The kernel name has changed since Ubuntu 7.10.  Now you should run this command
$ [COLOR="SeaGreen"]sudo rm  /lib/modules/$(uname -r)/ubuntu/misc/acerhk.ko[/COLOR]

-------------
Rest of the Instructions are the same for Ubuntu 7.10 and 8.04. AFAIK !

---

### Post by johndbottomley on 2008-05-21
Perfect - Thanks no problems at all.:)

---

### Post by qscomputing on 2008-06-01
Doesn't work for me at all. I've got acerhk working before on both Gutsy and Hardy (but not using these instructions) - but now I've just reinstalled Hardy and I can't seem to get acerhk (or my wireless) to work with any method at all!

ED. After reinstalling Hardy yet again, it works with a fresh install. Thanks!

---

### Post by Schwack on 2008-06-02
I've just got it working on 8.04, Hardy Heron for my Amilo 1718 but had to do a couple of extra steps:

```
sudo modprobe ath_rate_sample
sudo modprobe ath_pci
sudo modprobe ath_wlan
sudo modprobe ath_hal
```

And I checked that the modules were loaded with:
```
lsmod | grep ath
```

Then connected to the wireless network using the Network Manager.

Thanks to darrell and moma for the info!

---

### Post by jumbo701 on 2008-06-08
> **daydream said:**
> Many thanks for this guide. It's just perfect! And it works on Amilo li 2727 as well. I finally have my atheros wireless card working. I now have to figure out how to add security to it. My internet connection is only working when I switch off firewall... :(((

I have Amilo 2727 also, but I don't get my wlan working.  I follow these instructions, but I don't get it working. I have tried many times. I have 8.04 LTS in my Amilo. Can anyone please help me??? Nothing happens Fn+F1. Network manager doesn't find wlan. Wlan works with USB wlan-stick, but I need it with my another laptop.

---

### Post by o_portista17 on 2008-07-05
I've tried a lot of diferent ways, but i can't get it to work :(

Some help please...? 

Thanks

---

