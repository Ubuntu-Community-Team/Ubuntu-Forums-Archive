---
title: "[SOLVED] sl-modem-daemon after Feisty Update"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by Goldpin on 2007-06-17
'm having trouble with my winmodem.

I just installed Feisty using the alternate CD and everything was fine. However, since I installed the first batch of updates I have MODEM problems. The upgrades included sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu1_i386.deb. When first installed it, worked fine, but after I shut the computer down, and turned it on again, and tried to connect to the internet the ppp dialler program said “connecting” and then fell over. The modem log said, "no carrier". I have tried editing the wvdial.conf file to add Carrier Check = no, but it doesn't work and Gnome ppp won't detect the modem. When I reinstall the sl-modem-daemon, it works fine, but I have to do this every time I shut down and turn on the computer. I checked the dependencies in Synaptic Package Manager. Results below.

Depends: Libasound2 (>1.0.12)
Depends: Libc6 (>=2.50ubuntu1)
Depends: debconf | debconf 2.0
Conflicts: sl-modem-modules

The /etc/default/sl-modem-daemon file reads as follows. I removed the spaces between lines to make the post shorter.

# NOTE: settings in /etc/defaults/slmodemd are used too
# set this to 1 to never run the daemon from the init script
# you can set it if you have an USB device, than the init script won't
# be started at boot (but when the USB device is plugged on)
DONTSTART=0
# This is the default configuration for the slmodem driver daemon
# running on Debian systems.
#
# Edit device node and country code here ...
#
# possible country codes are:
#
# USA
# GERMANY
# BELGIUM
# etc.
#
# use 'slmodemd --countrylist' to check out other countries
#
#
#SLMODEMD_DEVICE=slamr0
#SLMODEMD_COUNTRY=GERMANY
SLMODEMD_DEVICE=auto
SLMODEMD_COUNTRY=USA
# Additional options for slmodemd, see "slmodemd -h" output for details.
# Do NOT set country or device name here!
OPTS=""
# force the start of the daemon even if old type modules seem to be
# installed (set it to 1)
FORCESTART=0
# set this to not see any hints of the init script on startup
# BEQUIET=1
# set this to not create the /dev/modem symlink
# NOSYMLINK=1

I tried changing the SLMODEMD_DEVICE and SLMODEMD_COUNTRY to:
SLMODEMD_DEVICE = slamr0
SLMODEMD_COUNTRY = UK
without success.

I have downloaded a patch for the sl-modem-daemon but don't know how to install it (or if I even need to) - OK, I'm a dummy.

Should I run ungrab-winmodem? I have the file, but don't remember how to use (OK - same as above).

---

### Post by Matchless on 2007-06-17
Hi,
   I am going to try and help you, but as I have not tried the Smartlink modem yet on Feisty this may not work.
Go to [http://packages.debian.org/stable/misc/sl-modem-daemon](http://packages.debian.org/stable/misc/sl-modem-daemon) and download the latest sl-modem-daemon then go to [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) and download the latest drivers for Smartlink ([slmodem-2.9.11-20070505.tar.gz]("http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20070505.tar.gz") ) now compile the drivers for your kernel and then install the the daemon. You may also have to install ungrab-winmodem, but this may not be necessary anymore in the latest packages.
Reboot and you should be running.

---

### Post by Goldpin on 2007-06-21
Problem was solved by replacing sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu1_i386.deb with with sl-modem-daemon(2.9.9d+e-pre2-7etch2).  Don't know why this one works and the other doesn't but it does.

---

### Post by Matchless on 2007-06-21
Thanks, does that mean using the sl-modem-modules from the Feisty repos together with the latest sl-modem-daemon from the Debian site works in Feisty for Smartlink modems? Did you also install ungrab-winmodem?
Just confirming so that the other readers get the picture.

---

### Post by _duncan_ on 2007-06-25
Just to share my experience using smartlink and feisty:

1. Still need ungrab-winmodem. Compiling the driver without it will work the first time, but will cause problems after reboot.

2. The newer sl-modem-daemon package that came with feisty (2.9.10+2.9.9d+e-pre2-5ubuntu1) caused my system to hang up, requiring a hard reboot.

3. The older sl-modem-daemon package (2.9.10+2.9.9d+e-pre2-5build1) still works. I used synaptic package manager to pin/lock to this older version. Otherwise, feisty will keep on offering to update the sl-modem-daemon package to the newer version.

---

