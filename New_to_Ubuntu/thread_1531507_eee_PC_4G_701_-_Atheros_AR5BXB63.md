---
title: "eee PC 4G 701 - Atheros AR5BXB63"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by simontaylor on 2010-07-15
Dear Ubunteans,

I have recently - yesterday - plunged a dysfunctional ASUS eee PC (2007) into Ubuntu land: 10.04, netbook edition. A vast improvement on Xandros, aesthetically, however, the technical problem which prompted the change in OS remains: Atheros AR5BXB63 - the Wi-Fi side of things remains inoperative. I have the weee notebook installing backports at the moment via ether cable. But after three days of trial and 100% error, I am not holding out any great hope that this will solve my connectivity problem. 

If you have any suggestions, I would appreciate your input.

Thank you,

Simon Taylor

---

### Post by 3rdalbum on 2010-07-15
System > Administration > Software Sources. Make sure that the first four checkboxes are ticked, so Ubuntu knows where to get its software from.

System > Administration > Synaptic Package Manager. Click Reload. When that's done, close Synaptic and go to System > Administration > Hardware Drivers and you might be offered a driver for download.

I did believe that the card should be supported out-of-the-box. Also check that the wireless is physically switched on, on the computer. If the card can connect to the AP but does not find any websites, then try the procedure on my website: [http://www.chrislees.info/ubuntu/opendns.shtml](http://www.chrislees.info/ubuntu/opendns.shtml)

---

### Post by simontaylor on 2010-07-15
Thanks 3rdalbum,

I've been through some of the threads relating to the onboard Atheros card and have already tried a scan for proprietary drivers with no luck.

This appears to be the most promising option, however the URL seems to be invalid.

> sudo apt-get install build-essential linux-headers-generic
wget [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz)
tar zxvf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801/

Which is to say, I got as far as the linux-headers-generic and no further.

If anyone can correct the URL ...

in the meantime I'm following the suggestions here 

[http://ubuntuforums.org/showthread.php?t=1123014](http://ubuntuforums.org/showthread.php?t=1123014)

... here goes...

no ... Now the wifi will not even find the wireless network!

Please help,

Best,

Simon

---

### Post by simontaylor on 2010-07-15
I think I've found an XP 32 bit driver for AR5001, which appears to be the right model.Asus returned absolutely nothing for the card in the way of drivers or information.

I believe there are two ways to use an XP driver? Wine or through ndiswrapper? is that right?

---

### Post by simontaylor on 2010-07-15
using lspci -v | less

I get: > 01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Subsystem: Device 1a3b:1026
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ath5k
Kernel modules: ath5k

so some movement ... however the driver I found is 32 bit.

I have read there can be a keyring clash with Wifi ????

still looking.

---

### Post by bumanie on 2010-07-15
That card apparently has the 5007EG chipset - instructions [here]("http://http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html") should help - I got the AR242x chipset going in the past by following method 2. Good luck.

---

### Post by simontaylor on 2010-07-15
thanks bumanie,

your hyperlink doesn't appear to be working...

best

---

### Post by bumanie on 2010-07-15
I'll find it again - it's not working for me either! hang on. I'll post the entire url for you.

---

### Post by bumanie on 2010-07-15
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

The url is rather long - it's instructions from intrepid ibex, hope the method still works in 10.04

** Just tried the link - it works

---

### Post by simontaylor on 2010-07-15
also found this from the good doctor:

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

I don't quite understand the deb note. Hopefully it becomes clear as I work through.

In the meantime, I must deliver those greenbeans to be roasted into ... coffee!

Thanks bumanie,

will check out on return.

best,

Simon

---

### Post by simontaylor on 2010-07-16
No joy. Neither your solution, bumanie, nor Dr. Kurian's worked. Perhaps a clash with keyring? which is playing up to an annoying extent.

I now get:

> 01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Subsystem: Device 1a3b:1026
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at fbef0000 (64-bit, non-prefetchable) [size=64K]
Capabilities: <access denied>
Kernel driver in use: ath_pci
Kernel modules: ath_pci, ath5k

Still seeking help.

Thank you,

Simon Taylor

---

### Post by bumanie on 2010-07-16
That is saying that your atheros card is a 5001 chipset - mine works out of the box on the present kernel - lspci gives the same chipset number. Could you post the output of > sudo lshw -C network and > rfkill list
PS: I have to go to work soon, will check back if time permits, depending on workload, but there are many others who will be able to help you - be patient, that card should work.

---

### Post by simontaylor on 2010-07-16
curious:

sudo lshw -C network gives following:

> *-network
description: Ethernet interface
product: L2 100 Mbit Ethernet Adapter
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:03:00.0
logical name:eth0
serial: 00:1e:8c:ec:8e:bb
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernect physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no multicast=yes port=twisted pair
resources: irq:27 memory:fbfc0000-fbffffff memory:fbfa0000-fbfbffff(prefetchable)
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:01:00.0
logical name: wifi0
version: 01
serial: 00:15:af:81:7c:3b
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath_pci latency=0 multicast=yes wireless=IEEE 802.11g
resources: irq:18 memory:fbef0000-fbefffff

rfkill list gives following:

> 0: eeepc-wlan: Wireless LAN
Soft blocked: no
Hard blocked: no

---

### Post by bumanie on 2010-07-16
Hello Simon,
I think I can see the problem - not sure how to fix it, unfortunately for you.
*-network
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:01:00.0
[COLOR="Red"]logical name: wifi0[/COLOR]
version: 01
[COLOR="Black"]the logical name should wlan0[/COLOR]. At least mine is, as are others according to documentation I have read. Unfortunately I am not a networking guru, just sort of know the basics. Sorry I can't be of more help.

This page may help as may the one below.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Try this page too

[http://www.ubuntugeek.com/how-to-get-ath5k-working-on-jaunty-with-compat-wireless-and-a-self-compiled-kernel.html#more-1424](http://www.ubuntugeek.com/how-to-get-ath5k-working-on-jaunty-with-compat-wireless-and-a-self-compiled-kernel.html#more-1424)

Here is my sudo lshw -C network : not sure it will help
*-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:70:db:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-999-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:91300000-9130ffff

---

### Post by simontaylor on 2010-07-16
Hi bumanie,

thanks for the advice. I'm having another shot at installing, then following the steps here:

[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

if no joy either there or troubleshooting on that basis... because the ath5k driver seems to be the go but just won't ... go ... I might try an alternative distro. Aurora is taking my fancy... or Leeenux... Sheer pig-headedness while there are distros out there known to work OOTB with this little machine to pursue the 10.04 netbook remix option. Or is it?

Fresh installation underway.

Best,

Simon

---

### Post by simontaylor on 2010-07-17
trialing leenux 4.01 extended and, surprise, surprise, no wireless connectivity. Scans OK. But no connection.

Best.

---

### Post by simontaylor on 2010-07-17
... in fact: lshw -C network gives the same error-line as bumanie remarked on for netbook remix 10.04. Possibly to do with the fact that leenux 4.01 based on 10.04?

---

### Post by bumanie on 2010-07-17
Hi Simon,

I'm really not sure why you have trouble getting the ath5k driver - I'll do a bit of research and get back to you if I can find anything that may help re the ath5k. I have had no trouble re ath5k since 8.10 version.

---

### Post by bumanie on 2010-07-17
Seems to be a common problem with lucid and the present kernel(s) - I read a bug report in launchpad that suggested using a mainline ppa kernel - for this person the problem was fixed. If you don't mind trying an unreleased, thus 'unofficial ubuntu kernel' - [go here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/") and download the linux-image generic, you should not need the headers. I run a mainline kernel for a different reason - it works fine so far (been using about 6 weeks). Might be worth a shot as nothing else has helped so far. The linux-image is a .deb, so you just need to double click to install it.

---

### Post by hackerseraph on 2010-07-17
did you say you were using the netbook remix version of ubuntu? when i first got my eee 1000ha i had so many issues with the wifi, I created a work around script, unfortunately i cant find it anywhere in on my secondary partition, but if you use netbook remix, your wifi should work. try booting it live for kicks and see. I really can't back track my work around also because i upgraded my wifi card to an intel N card.

---

### Post by simontaylor on 2010-07-17
thanks bumanie,

while my incredibly slow broadband downloads another distro to try for that elusive ootb connectivity ... I'm downloading backports for 10.04 netbook remix and hoping. 

Back to netbook remix - since leeenux was this anyway + annoying cartoon characters. When my unbelievably slow ether cable (btw - the eee seems to see the wired network only sometimes....!? and has to be rebooted and then fail to find wireless before it will see wired --- as if there's a clash between the ether and wireless components???) has finished doing the backports and I've run some more tests and checks I'll check out the kernel you've suggested. I have nothing to lose... except my patience ... and then sanity.

Running various sorts of lists and checks ath5k is loaded as driver but fails to connect - or is disconnected. I know I connected in the old OS - Xandros - before I installed the remix... but I wonder if there's some sort of override ... not necessarily of the time-out variety as included in rfkill ... again could be a clash somewhere???

thanks hackerseraph,

a reliable workaround is indeed in order. I'm planning to take this little machine around the world and need it to have no problems with connectivity.

Best,
Simon

---

### Post by michaelzap on 2010-07-17
I have the same netbook, and I've had the best results with Eeebuntu (especially the latest version - 4 - which is based on Debian despite the name) and Crunchbang. I have run vanilla Ubuntu on it as well, but not since Jaunty. I've actually never had the wifi not work out of the box, so you might just want to try Eeebuntu and be done with it. This is a low-powered but hardy little gizmo. It actually gets the best wifi reception of any of our laptops. BackTrack 3 runs perfectly on it also, if you'd like to do a little testing while you travel around the world.

---

### Post by simontaylor on 2010-07-17
hi michaelzap,

I'm downloading eeebuntu 3 base version and hoping this will provide the essentials - a connection. Will try this next. Still 4 hours remaining! 

Are upgrades fully supported through Aurora project for eeebuntu? --- there is there at least an aesthetic appeal. ... I read through eee pc user forums that eeebuntu 4 required some tweaking so was loath to go there directly so am taking the roundabout way via 3. .... IF it does get me online, of course!

Best

---

### Post by michaelzap on 2010-07-17
> **simontaylor said:**
> hi michaelzap,

I'm downloading eeebuntu 3 base version and hoping this will provide the essentials - a connection. Will try this next. Still 4 hours remaining! 

Are upgrades fully supported through Aurora project for eeebuntu? --- there is there at least an aesthetic appeal. ... I read through eee pc user forums that eeebuntu 4 required some tweaking so was loath to go there directly so am taking the roundabout way via 3. .... IF it does get me online, of course!

Best

I used Eeebuntu 3 for a while on my Eee PC and it was a fine distro for general use. If there was any tweaking needed to install Eeebuntu 4, it must not have been very much because I don't even remember doing it. Either should work fine for you. Version 3 is based on Ubuntu Jaunty, so if you're more comfortable with Ubuntu then that's probably a good choice for you.

You should be able to run all of the regular updates except for the distro upgrade, but to be honest I rarely bothered to update my Eee PC (since it's not my main PC and I try out new distros on it a lot).

CrunchBang is the distro that has performed the best for me on this machine, but not everyone likes OpenBox (and if you're used to Gnome, it can seem extremely bare-bones).

---

### Post by simontaylor on 2010-07-17
cool, thanks michaelzap.

looking forward to finding something that does the biz.

best

---

### Post by simontaylor on 2010-07-18
eeebuntu 3.0 base works out of the box. 

Brilliant!

Connected via my eee PC 4G 701.

Still completely bemused about the 'problem' of a Wifi with a working driver that could not connect in netbook 10.04. But hopefully in the clear now with this distro.

Thanks bumanie for bearing with me and looking for options & michaelzap for confirming eeebuntu as a working option.

Best,

Simon Taylor

---

