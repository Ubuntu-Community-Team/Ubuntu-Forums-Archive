---
title: "acer w ar5006eg cant connect/wireles disappears"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by sid708 on 2007-12-18
hi.
my problem is:
wifi cant connect.

acer aspire 3680 series
ar5006eg
driver installed

iwconfig
lo         no wireless extension
eth0    no wireless extension
wlan0  IEEE 802.11g  ESSID:off/any
           Mode:Managed Frequency:2.412 GHz  Access Point: Not-Associated
           Bit Rate: 54 Mb/s
           Encryption Key:off
           Power Management:off
           Link Quality:0 Signal level:0 Noise level:0
           RX invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
           Tx excessive retries:0 Invalid misc:0 Missed beacon:0

ifconfig
wlan   Link encap:Ethernet HWaddr 00:19:7E:28:82:DB
          UP BROADCAST MULTICAST     MTU:1500    METRIC:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collision:0 txqueuelen:1000
          RX bytes:0 (0.0 b )  TX bytes:0 (0.0 b )
          interrupt:17 Memory 54100000-54110000

i really dont know what to do now..
if i login as root and run iwconfig or ifconfig then wireless appears at connections but cant even find networks.. if i restart then it disappears.. 
please help.. i dont want vista back.. :(

---

### Post by grokwik on 2007-12-19
I had the same probme until yesterday ;)
The only difference was that it was with an atheros ar5007eg.

I solved that with a patched version of madwifi that I found on the madwifi' trac [ [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679) ]. In the "change history" there's a post [ 12/16/07 03:05:03 by mrenzmann] that gives the patched 0.9.3.3 madwifi, you just have to compile and install it.

Just carefully check the requirements at the beginning of the ticket to be sure...

```
wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
tar -xvzf [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

```Then go to the jjust created directory and type :
```
make
```And then (when the build is done)
```
make install
```...
Hope that helps

---

### Post by foppeh on 2007-12-22
What if I get these kind of errors:
```
root@foppe-laptop:/home/foppe/madwifi-ng-r2756+ar5007# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/foppe/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  HOSTCC  /home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory

[...]

make[3]: *** [/home/foppe/madwifi-ng-r2756+ar5007/ath_hal/uudecode] Error 1
make[2]: *** [/home/foppe/madwifi-ng-r2756+ar5007/ath_hal] Error 2
make[1]: *** [_module_/home/foppe/madwifi-ng-r2756+ar5007] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Fout 2
```
It's a fresh installed Gutsy 32 bit with the patched Madwifi 0.9.3.3 + ar5007 (patch)

---

### Post by grokwik on 2007-12-26
I guess you don't have the needed libraries to build.
You have to install gcc (I don't remember exactly the packages needed)

---

### Post by foppeh on 2007-12-26
Thanks for your reply.
I found out already but forgot to post the solution to this topic. Needed is the C++ compiler and in Ubuntu that you search for G++ in the repositories.
I hope it helps others.

---

### Post by sweetcancer on 2007-12-26
Got the ar5006eg card on my acer aspire 7520g working under ubuntu 7.10 by doing this:

download the winxp-32bit driver for ar5007eg, not ar5006eg, from here:[http://www.atheros.cz/](http://www.atheros.cz/)

then install the .inf file using ndiswrapper.

then the acer_acpi. add the reposirtory to your sources.list and add the key as told here: [http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

then sudo apt-get update and then go to synaptic, search for acer. You should find acer_acpi and acerwificontroller. Install these packages.

After that you can add the acer wifi controller applet to your gnome-panel (add to panel->acer wifi controller applet)

then go to synaptic again and install wlassistant. after that, restart your computer. After rebooting, make sure your wifi card is turned on (the applet you added to your panel should be in colours, it's black and white when turned off) Then open the "Run application" window by pressing alt+f2, there you write gksu wlassistant. your network should be showing in the wireless assistant window. Click it, and it will connect.

I hope this was some help to someone out there :)

---

