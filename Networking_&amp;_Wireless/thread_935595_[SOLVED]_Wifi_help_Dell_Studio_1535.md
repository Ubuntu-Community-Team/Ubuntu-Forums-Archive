---
title: "[SOLVED] Wifi help Dell Studio 1535"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by AirWreck on 2008-10-01
Okay I've been clawing my way up the learning curve of Kubuntu for the last few weeks but I threw myself some curveballs.  New Studio 1535 with the 1397 wlan (BCM 4312) has me in fits trying to get wifi.  Unfortunately, I cannot directly connect this machine to net so have to transfer everything on a stick until the wireless is up and running.

I've tried various threads, wikis, etc.  I still have no real idea what I'm doing but some of it is starting to make sense.  I tried the bcmwl5 and 6 drivers with ndiswrapper.  No joy, sounds like its because they're Vista drivers.  Ndiswrapper shows as installed but there was an error during synaptic install because I have something funky going on with ntscorefonts (installed from aptoncd and hence why I want to get on net and fix).

This thread [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=857532&page=5]("http://ubuntuforums.org/showthread.php?t=857532&page=5")[/COLOR] seems like it has the answer but its a long and winding path.  I'm currently stuck in the Broadcom readme for their linux driver.  I'm a total noob but not afraid to wreak total havoc = dangerous;)

When I try the below commands, all I get is "no such file or directory".  I checked my lines, I've tried some permutations and I am root.

[COLOR="Blue"]On the target machine, and cd'ed to the directory that contains the Makefile

4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`[/COLOR]

After two days and no joy, I'm just about to chuck it all and go back to the dreaded Vista side of the partitions.  With Dell putting Ubu on the Studios off the shelf, I'm hoping there is some love here.  It sounds like folks are figuring out ways either with ndiswrapper and a combo of drivers or by installing the 64bit version.

If someone could help me by spelling it out, step by step, line by line, baby beginner style I would be much obliged and regain some kubu stoke.  Thanks!

Don't know if its important and I can't remember the command right now but you do it at end of driver install to test whether it worked (I think).  When entered, it showed that the driver worked but then next lines gave an error for ndiswrapper as something like "no driver" and next line was the same error for ndiswrapper.tar.

lspci gives this:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


lshw -C network gives this:

  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:71:40:3e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s

---

### Post by AirWreck on 2008-10-01
Not trying to do the impatient bump (in fact I've had it and am calling it a night:), but just saw another post that indicated that 8.04.1 supported Broadcom wireless.  I am running 8.04.1 and could "see" the wireless network I want to connect to initially.  But I could not get internet.  I didn't try a ping and went right into all the ndis stuff.  I'd be willing to do a reinstall at this point if I just missed something dumb at the beginning.  I seem to be further from the resolution than when I started...

---

### Post by Ayuthia on 2008-10-01
Your card should have worked with 8.04.1.  I have seen that some have been having problems with getting it to connect with encrypted routers.  Are you using WEP/WPA?  If so, you might try turning off the encryption first and see if you can connect.  

The previous post had something in blue.  I am guessing that the blue portion was the part that did not work.  If that is the case, I would not try installing it because it is the same driver as what comes with Ubuntu.

---

### Post by AirWreck on 2008-10-02
Thanks for the reply Ayuthia.  The blue part was the of the linux driver ReadMe from Broadcom on installing the driver.  But you seem to confirm that I bungled things further with all of this ndiswrapper stuff.

Might all just be nooB operator error.  I guess thats the biggest problem with k/ubuntu and linux in general.  There is so much info out there and updates come so fast that you can be fixing something thats already fixed.  Still, it does appear once you get a lay of the land, its a better place to be than Redmond.

Eric

---

### Post by AirWreck on 2008-10-02
Okay sorry I remain just another nooB with just another wireless problem.  Wouldn't be a big deal but this is currently the only way I can get on net as I am on a ship alongside the dock for a few weeks.

I did the reinstall of 8.04.1 and still no joy.  I have /home off in its own part and remounted it as part of the install and maybe that prevented a clean slate?  As I said, before I started all this a few days ago, I could see the wireless network with great strength in Knetwork but wasn't getting on net in browsers.  Now Knetwork is only showing a wired connection option.

Before I muck up this fresh install with random, shotgun commands, I'll consult the pro's here :)

Knetwork is only showing eth0 but no ip addresses.  Wireless is switched to on and while the Bluetooth indicating light is on, the wireless is not.  Originally I had wireless indication a few days ago.

Wireless network in unsecured, unencrypted.

Thanks for any help getting this nooB out of the woods.

---

### Post by Ayuthia on 2008-10-02
Can you look at System->Administration->Hardware Drivers and make sure that b43 is not enabled and wl is enabled?  The b43 driver does not work with your card but the wl should.

---

### Post by AirWreck on 2008-10-02
Ayuthia,

I'm in Kubuntu but System->Hardware Drivers Manager indicates wl enabled but not in use.  When I did the original install about a week ago, it gave an error to the effect that it was using a proprietary driver and certain things wouldn't be supported.

Thanks for the help!

---

### Post by Bucky Ball on 2008-10-02
Maybe untick it and then tick it back on again.

---

### Post by AirWreck on 2008-10-02
Bucky, I unticked, acknowledged the "driver necessary" error, closed and reopened the manager and then reticked = no luck.  FYI - I did just confirm again that I can get wifi access over on the Vista side.

Is it time for me to wade back into the dreaded ndiswrapper territory again or was this Hardy distro supposed to make that a thing of the past?

---

### Post by Bucky Ball on 2008-10-02
In a terminal, copy and paste this:
[B]
nano /etc/modprobe.d/blacklist[/B]

Make sure the section below looks like this:

```
# replaced by b43 and ssb.
blacklist bcm43xx
```

If it doesn't, change it and try the 'wl' driver again.

---

### Post by Ayuthia on 2008-10-02
After you verify the information that BuckyBall suggested, please try the following (will only work for this session):
```
sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
sudo modprobe wl
sudo ifconfig wlan0 up
sudo ifconfig eth1 up
sudo iwlist scan
```
This will remove any possible wireless driver conflicts, then it will load the wl driver, try to bring it up (one of the ifconfig commands will fail because it does not exist), and then scan for wireless.

If this works, then we just need to make some updates to your configuration.

---

### Post by AirWreck on 2008-10-02
Ayuthia,

As per Bucky, I confirmed that my system shows the below for the nano command:

# replaced by b43 and ssb.
blacklist bcm43xx

I executed your commands but got an error before the ifconfig commands as per below paste from terminal:

Note:  this is a clean 8.04.1 install that hasn't connected to net nor any packages installed from my saved aptoncd configuration.  Don't know if its important to discussion but ndiswrapper is not installed.

airwreck@airwreck-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper bcm43xx wl
[sudo] password for airwreck:
airwreck@airwreck-laptop:~$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.24-19-generic/volatile/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
airwreck@airwreck-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
airwreck@airwreck-laptop:~$ sud ifconfig eth1 up
bash: sud: command not found
airwreck@airwreck-laptop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
airwreck@airwreck-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by AirWreck on 2008-10-02
Whoa!  I just tried dmesg and its longer than War & Peace.  I can paste it if you need it, but the top line of wl entries says, "module license 'unspecified' taints kernel."  Then there are a bunch of "wl:  unknown symbol" type messages.  Tainted kernels don't sound good but I know less than zero so maybe its a good thing?  I can paste out the dmesg results but if you need it to trouble shoot, maybe you could tell me how to paste into an embedded scrolling window for housekeeping sake?

Thanks a lot for the help.  If nothing else, I'm learning more about commands and where things are filed in Kubuntu :)

---

### Post by Ayuthia on 2008-10-02
> **AirWreck said:**
> Whoa!  I just tried dmesg and its longer than War & Peace.  I can paste it if you need it, but the top line of wl entries says, "module license 'unspecified' taints kernel."  Then there are a bunch of "wl:  unknown symbol" type messages.  Tainted kernels don't sound good but I know less than zero so maybe its a good thing?  I can paste out the dmesg results but if you need it to trouble shoot, maybe you could tell me how to paste into an embedded scrolling window for housekeeping sake?

Thanks a lot for the help.  If nothing else, I'm learning more about commands and where things are filed in Kubuntu :)

The tainted kernel message is ok.  It shows up because you are using a propietary driver instead of an open source.  However, the unknown symbol message appears to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/243930)

If you have a working connection in Ubuntu, it looks like the fix is in the hardy-proposed repositories.  However, that means that you will be using a test kernel version instead of an officially released version.  If you want to try that, you can go to this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by AirWreck on 2008-10-02
Ayuthia,

Hey thanks for all the help, I found some of your other posts and it looks like you're the good samaritan for the wifi lost :)

I'll keep playing around and it sounds like something is in the pipeline to fix it.  I thought I was being smart buying a similar machine that Dell is offering with Ubuntu off the shelf.  Oh well, I've still got net access on "the company" machine.  Just can't seem to get Kubu decked out 100% on my machine using only an aptoncd that I made from an install on an older "test" laptop a few weeks ago before I came to work.  Seems like no matter what I do, the install of the ntscorefonts doesn't totally complete so everything else gets grumpy.  But that is another post for another day!

Thanks again.

---

### Post by AirWreck on 2008-10-03
Ayuthia...

....apparently I am a total idiot.  I thought something was weird that I was able to originally see the WAP but not connect.  I did see a similar post yesterday where they could see the WAP but not get on net and their dmesg also showed all the errors.  But for grins, I just installed all of my aptoncd packages from my old Inspiron install and I guess it did a kernel update as part of that.  I had seen a post that said to maybe try using wicd vice knetworkmanager.  But after the reboot, I have internet and Knetworkmanager looks to be all good as well.  

Sorry for the full on nooB wild goose chase but perhaps this will help with trouble shooting.  Let me know if I can post any commands that will give you more info.  FYI - I just did another dmesg and wl is only one line, the "taints kernel" line with none of the other "symbol" erros below it.

For the record this was a Broadcom BCM4312 on a Dell Studio 1535, Kubuntu installed from 8.04.1 disk and then updated with aptoncd packages from previous install.

Thanks again for all your help.

---

### Post by Bucky Ball on 2008-10-03
Nice work ...
Don't forget to mark this as solved as it will be a helpful fix for others. :)

---

### Post by AirWreck on 2008-10-03
It gets worse...I just figured out why I originally could see the WAP but could not connect to net.  I was using Guarddog on my clunker Inspiron laptop when I first starting testing the Kubuntu waters a few weeks ago.  I was able to surf just fine on that machine with a wired connectin but I just activated Guarddog on the new machine and -poof- no net.  DOH!  I still can't get protocols in G'dog right to get on net but when I say "turn off firewall," net comes right back on.  Complete nooB operator error but might as well come clean in case I will help someone else out of the woods ](*,)

---

