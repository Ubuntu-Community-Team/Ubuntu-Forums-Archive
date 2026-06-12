---
title: "Wireless- Connection Problem"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by Kinetic1001101 on 2009-10-12
If anyone can help it would be great... I am running ubuntu 9.04 and after I downloaded a bunch of packages after a new install, the wireless doesn't work anymore. It did work until I did this package update. I am a newbie and really want to stick with Linux. I just need to learn how to manage these adaptability problems better.:P

Thanks in advance!

---

### Post by ConXtionS on 2009-10-12
Hi Bro

Im not smart... but lets start with... do you have a network icon and if so what is it telling you?

---

### Post by Kinetic1001101 on 2009-10-13
yeah it's there...but its just has that little X over it...

---

### Post by beastrace91 on 2009-10-13
Have you tried rebooting? I know network manager can be fickle at times.

If it is still broken after that - try getting a wired connection and making sure all your updates are installed (if it stopped half way due to power loss or cancelling it can mess things up) To update once you are connected to the net go to System->Administration->Update Manager

~Jeff

---

### Post by ConXtionS on 2009-10-13
Yeah... you see all his beans... thats how you find SMART DUDES


Do what the man said

---

### Post by Kinetic1001101 on 2009-10-13
Yeah i rebooted a few times since... I am going to try and connect direct now that i have the cord in reach.  The update seemed to work and finish properly, I will still try to update again... thanks bro.

BRB

---

### Post by superdav42 on 2009-10-13
Do you know what kind of wireless card you have? 
I am guessing there was a kernel update. When you boot up the computer it will let you select which kernel to load if you select the previous kernel does your wireless work?

---

### Post by Kinetic1001101 on 2009-10-13
OK... I hooked it up to a wired connection and did the install over again and it still doesn't recognize my wireless... thanks again!   anything else I should do?

---

### Post by Kinetic1001101 on 2009-10-13
Atheros

---

### Post by Kinetic1001101 on 2009-10-13
The wireless worked rite after the install of 9.04 and then when I updated it stopped....or at least I think it stopped after the update...almost positive.    

No...it does'nt give many any option to boot into a different kernel

thanks

---

### Post by beastrace91 on 2009-10-13
> **Kinetic1001101 said:**
> 
No...it does'nt give many any option to boot into a different kernel

Are you sure it doesn't? If you really have all the updates installed correctly it should have added a new kernel. Any idea what Atheros chip it is?

~Jeff

---

### Post by Kinetic1001101 on 2009-10-13
the little light in the front of the laptop on the wireless switch doesn't even light up like it usually does....I am assuming that it isn't reading my wireless card....am I right?

thanks

---

### Post by Kinetic1001101 on 2009-10-13
Boot options....    you talkin about when I first start it up in the shell screen?   Do I need to hit any f keys to get the optoin?

How do I find the wireless card info?

thanks

---

### Post by anewguy on 2009-10-13
Please post back the output of the following:

lspci

lsusb (some laptops actually have the wireless adapter going through internal USB)

That way we can see exactly what chipset your adapter is using and hopefully get you going with the right driver.

Dave :)

---

### Post by beastrace91 on 2009-10-13
> **Kinetic1001101 said:**
> Boot options....    you talkin about when I first start it up in the shell screen?   Do I need to hit any f keys to get the optoin?

When your computer is turning on you should see a black screen with the words "grub" that gives you a two count to press escape and get a menu of kernel's to choose from - if you get this select the older (lower number) kernel from the list and see if the Wifi works then.

~Jeff

---

### Post by Kinetic1001101 on 2009-10-13
Will do... I have to connect it back to the wired connection..
'

BRB


thanks

---

### Post by Kinetic1001101 on 2009-10-13
okay    so here is the output from the lspci command...


lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Kinetic1001101 on 2009-10-13
K... I will try that now...


Thanks again...

BRB

---

### Post by anewguy on 2009-10-13
Just follow the information in this link (don't worry if the computer isn't the same as yours):

[http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu]("http://ubuntumanual.org/posts/185/install-atheros-ar242x-802-11abg-wireless-driver-in-ubuntu")

if you have any questions, just post back.

Dave :)

---

### Post by Kinetic1001101 on 2009-10-13
okay.... everything went pretty well until this point or the make command

here is the output....


stall@stall:~$  cd ~
stall@stall:~$      mkdir madwifi
stall@stall:~$ cd madwifi
stall@stall:~/madwifi$ svn co [https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6)
svn: OPTIONS of 'https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6': Could not resolve hostname `svn.madwifi-project.org': Host not found ([https://svn.madwifi-project.org](https://svn.madwifi-project.org))
stall@stall:~/madwifi$ cd madwifi-hal-0.10.5.6
bash: cd: madwifi-hal-0.10.5.6: No such file or directory
stall@stall:~/madwifi$ make
make: *** No targets specified and no makefile found.  Stop.
stall@stall:~/madwifi$ sudo make install
make: *** No rule to make target `install'.  Stop.
stall@stall:~/madwifi$

---

### Post by Kinetic1001101 on 2009-10-13
Do I have to put something after the make command?

Please help!

thanks

---

### Post by anewguy on 2009-10-13
I'm installing svn right now so I can try everything down to the make (I don't want to install on my system).  I'll get back to you shortly.

Dave :)

---

### Post by anewguy on 2009-10-13
It appears it had a problem trying to get the driver source via the svc command - notice how the htpps failed.  That's why make wouldn't work.  I installed svn (I only have dialup, so sorry it took a while) and then did a copy/paste of the svn command (since it is a scrolling text window, be sure to get all the text) from that link to the terminal window.  Mine came up with a warning about the certificate hostname not matching, and I did a temporary accept at which point the svn started processing.  That's further than you actually got, so you may want to try again.

Let me know what happens this time.

Dave :)

EDIT:  Thought I should add that the svn "checks out" the version of the source specified and copies all the of files/folders down to your PC.  Since your svn failed on the https, it never downloaded any source or the makefiles, etc., so you couldn't do anything.  If the svn is working you will know as it downloads many files.

---

### Post by anewguy on 2009-10-13
If you're still on let me know, otherwise I plan to log off for the night shortly.

dave :)

---

### Post by fixerman on 2009-10-13
> **Kinetic1001101 said:**
> If anyone can help it would be great... I am running ubuntu 9.04 and after I downloaded a bunch of packages after a new install, the wireless doesn't work anymore. It did work until I did this package update. I am a newbie and really want to stick with Linux. I just need to learn how to manage these adaptability problems better.:P

Thanks in advance!

Is your wireless actually switched on? There is a switch on the keyboard usually. Just a thought.:)

---

### Post by superdav42 on 2009-10-13
> **Kinetic1001101 said:**
> project.org/madwifi/branches/madwifi-hal-0.10.5.6': Could not resolve hostname `svn.madwifi-project.org': Host not found ([https://svn.madwifi-project.org](https://svn.madwifi-project.org))

Sounds like you were not actually connected to the internet when you ran this command. You have to connect your ethernet so you can pull the driver code from this site. 

and if you do it with http instead of https you will not get the certificate warning. No need for this to be encrypted anyway.

---

### Post by lavinog on 2009-10-13
after turnning the wireless switch on post the output of
```
dmesg|tail -n 20
```

---

### Post by Kinetic1001101 on 2009-10-13
I just logged on...I am at school so I will be on for a while.. then when I get home and in front of my linux computer I will make sure I copied all of the line you mentioned. Thanks so much for all of your help. I will be back on later and if your around cool... if not then I will check in tomorrow.

Thanks

---

### Post by Kinetic1001101 on 2009-10-13
Yeah its switched on

thanks

---

### Post by Kinetic1001101 on 2009-10-13
The wireless switch is switched on that is....still have the problem though

---

### Post by Kinetic1001101 on 2009-10-13
Any other thought anyone has??

Thanks

---

### Post by lavinog on 2009-10-13
what did dmesg say?

---

### Post by Kinetic1001101 on 2009-10-13
stall@stall:~/madwifi$ dmseg|tail - 20
==> standard input <==
bash: dmseg: command not found
tail: cannot open `20' for reading: No such file or directory
stall@stall:~/madwifi$

---

### Post by Kinetic1001101 on 2009-10-13
Sorry I entered it wrong and with the wired connection...  Here is the output after doing the correct syntax and with only wireless switched on:

stall@stall:~/madwifi$ dmesg|tail -n 20
[ 2102.892121] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[ 2102.893064] ata1.00: configured for UDMA/100
[ 2102.909131] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[ 2102.909152] sd 0:0:0:0: [sda] Write Protect is off
[ 2102.909154] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2102.909186] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2103.407695] pci 0000:00:02.0: setting latency timer to 64
[ 2103.410211] PM: Image restored successfully.
[ 2103.473582] Restarting tasks ... done.
[ 2103.476582] PM: Basic memory bitmaps freed
[ 2104.236935] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 2104.822925] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input10
[ 2104.860160] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[ 2121.866291] sky2 eth0: enabling interface
[ 2121.867108] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2482.961072] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2782.775431] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[ 2782.776300] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2793.180074] eth0: no IPv6 routers present
[ 2952.049985] sky2 eth0: Link is down.
stall@stall:~/madwifi$

What is the dmesg|tail -n 20    command mean anyway, just curious, if you have the time.

thanks a bunch!

---

### Post by anewguy on 2009-10-13
You did hard wire and then re-run all of the svn (someone else already mentioned it, and I just assumed, but you do need to be connected to the net for the svn to work), make and make install, right?  If not, do that.  If you already did, were there any error messages besides a couple of warnings from gcc?

Dave :)

---

### Post by Kinetic1001101 on 2009-10-13
Im here the install went through but no wireless

---

### Post by Kinetic1001101 on 2009-10-13
When I got to the point were I had to put ath_pci   after the   sudo command, i forgot and a file about rebooting came up...  well I went back into it and did it with the ath_pci after the sudo command and then restarted the computer, then tried to connect wirelessly and still no connection.

thanks again for weathering through this with me and everyones help.

---

### Post by Kinetic1001101 on 2009-10-14
okay so I tried to do the whole thing over again and I'm at this point:

stall@stall:~$ sudo apt-get install build-essential subversion
[sudo] password for stall: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stall@stall:~$ cd ~
stall@stall:~$      mkdir madwifi
mkdir: cannot create directory `madwifi': File exists
stall@stall:~$ cd madwifi
stall@stall:~/madwifi$ svn co [https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6)
Error validating server certificate for 'https://svn.madwifi-project.org:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
 - The certificate hostname does not match.
Certificate information:
 - Hostname: [www.westell.com](www.westell.com)
 - Valid: from Thu, 24 Feb 2005 22:05:13 GMT until Sun, 22 Feb 2015 22:05:13 GMT
 - Issuer: Westell Technologies Inc., Aurora, Illinois, US
 - Fingerprint: 8c:fe:62:95:c9:34:db:b7:27:5f:63:bd:4d:5b:5d:1f:1d:d9:93:c6
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: OPTIONS of 'https://svn.madwifi-project.org/madwifi/branches/madwifi-hal-0.10.5.6': Could not read status line: Secure connection truncated ([https://svn.madwifi-project.org](https://svn.madwifi-project.org))
stall@stall:~/madwifi$

---

### Post by Kinetic1001101 on 2009-10-14
okay and i did this next...

stall@stall:~/madwifi$ cd madwifi-hal-0.10.5.6
stall@stall:~/madwifi/madwifi-hal-0.10.5.6$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/stall/madwifi/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
        make -C $d || exit 1; \
    done
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools'
stall@stall:~/madwifi/madwifi-hal-0.10.5.6$

---

### Post by Kinetic1001101 on 2009-10-14
then this...

stall@stall:~/madwifi/madwifi-hal-0.10.5.6$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/stall/madwifi/madwifi-hal-0.10.5.6 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.28-15-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
install -m 0644 ath_pci.ko //lib/modules/2.6.28-15-generic/net
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath'
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_hal'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
install -m 0644 ath_hal.ko //lib/modules/2.6.28-15-generic/net
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_hal'
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
        make -C $i install || exit 1; \
    done
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/amrr'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
install -m 0644 ath_rate_amrr.ko //lib/modules/2.6.28-15-generic/net
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/amrr'
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/onoe'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
install -m 0644 ath_rate_onoe.ko //lib/modules/2.6.28-15-generic/net
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/onoe'
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/sample'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
install -m 0644 ath_rate_sample.ko //lib/modules/2.6.28-15-generic/net
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/sample'
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/minstrel'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
install -m 0644 ath_rate_minstrel.ko //lib/modules/2.6.28-15-generic/net
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate/minstrel'
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/ath_rate'
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/net80211'
test -d //lib/modules/2.6.28-15-generic/net || mkdir -p //lib/modules/2.6.28-15-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
        f=`basename $i .o`; \
        install -m 0644  $f.ko //lib/modules/2.6.28-15-generic/net; \
    done
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/net80211'
(export KMODPATH=/lib/modules/2.6.28-15-generic/net; /sbin/depmod -ae 2.6.28-15-generic)
make -C ./tools all || exit 1
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
        make -C $d || exit 1; \
    done
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools'
make -C ./tools install || exit 1
make[1]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools'
for d in ath_info; do \
        make -C $d || exit 1; \
    done
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig wpakey; do \
        install $i /usr/local/bin/$i; \
        strip /usr/local/bin/$i; \
    done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
for d in ath_info; do \
        make -C $d install || exit 1; \
    done
make[2]: Entering directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
install -d /usr/local/bin
install -m 755 ath_info /usr/local/bin
install -d /usr/local/share/man/man8
install -m 644 ath_info.8 /usr/local/share/man/man8
make[2]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools/ath_info'
make[1]: Leaving directory `/home/stall/madwifi/madwifi-hal-0.10.5.6/tools'
stall@stall:~/madwifi/madwifi-hal-0.10.5.6$ 

Then I did this line...

stall@stall:~/madwifi/madwifi-hal-0.10.5.6$ sudo gedit /etc/modules ath_pci

And it brought up a file in a text editor screen titled modules (/etc) - gedit... that stated...

"# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc


Does that mean I need to do something at startup, cause last time I just restarted and tryied connecting wireless and nothing still.

---

### Post by Kinetic1001101 on 2009-10-14
Okay...   GOOD NEWS...  the wireless is working now.

I think since I did what you told me to do, but did it over and the correct way that time it worked for me.   Thank you so much for your help.  Thanks to everyone for your quick replies...  I am a Linux / ubuntu fan for life.   the support in here is so great.

thanks a bunch!

---

### Post by Kinetic1001101 on 2009-10-14
Okay...   GOOD NEWS...  the wireless is working now.

I think since I did what you told me to do, but did it over and the correct way that time it worked for me.   Thank you so much for your help.

---

### Post by lavinog on 2009-10-14
> **Kinetic1001101 said:**
> 
What is the dmesg|tail -n 20    command mean anyway, just curious, if you have the time.

thanks a bunch!

glad you got it working.

dmesg will display messages from the kernel.  When something is not working it is a great place to start.  The kernel should report status changes such as the wireless enabling or disabling, or if it won't turn on, it should give some reason why.

| is a pipe. **program1 | program2** means take the output of program1 and input it into program2.

tail -n 20 means only show the last 20 lines...this is used sometimes reduce the amount of info that comes out.  dmesg will output every message from boot.
Sometimes it is handy to post all of dmesg, but if you do, make sure you use code blocks: [noparse]```

```[/noparse]

---

### Post by anewguy on 2009-10-14
Glad it's working for you!

Dave :)

---

### Post by superdav42 on 2009-10-14
I glad to hear you got this working. In future it might be easier to have people download the snapshot tarballs from here:
[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/") 
Instead of messing with svn.

---

