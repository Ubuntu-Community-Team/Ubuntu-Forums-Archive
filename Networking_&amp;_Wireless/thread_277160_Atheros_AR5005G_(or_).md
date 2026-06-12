---
title: "Atheros AR5005G (or )"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by karhulitos on 2006-10-14
Hello,

I have a problem with wlan. Computer is a new Acer Aspire 5044WLMi (Turion 64 ML-34, X200M, Atheros 5005 or 5211).
I've just installed Edgy from scratch and all updates came in.
On top of that I installed Network manager and ndiswrapper after that.

Windows driver's name is ar5211.inf and Ubuntu says
```
lspci
06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
```

Right after Edgy install
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

Right after ndiswrapper and ar5211.inf install iwconfig output is the same. No luck. Ndiswrapper's GUI says "hardware present: yes"

What can I do? (hope my only way out isn't reloading the Acer/WindowsXP rescue disk :()

System claims to be "2.6.17-10-generic".

best regards,
Timo

PS, yesterday I had Ubuntu 6.06 and iwconfig did list my wlan card but still it couldn't connect to any networks.

---

### Post by tturrisi on 2006-10-14
uninstall ndiswrapper
install linux-restricted-modules that match your kernel

atheros uses the madwifi drivers included in the restricted package

---

### Post by gnomer_ on 2006-10-14
I don't recommend the regular madwifi, I think he should use madwifi-ng. Lots more features, and more up to date.

---

### Post by karhulitos on 2006-10-14
OK, cheers. Me being rather new to Linux I did check Synaptic for "linux-restricted-modules-2.6.17-10-generic" and it says it's installed.

I did get the picture that Atheros should be a piece of cake for Ubuntu and madwifi. The fact that Synaptic says it's installed confused me.

But, I'll try to find information how to get "madwifi-ng" installed.

---

### Post by tturrisi on 2006-10-14
[How To madwifi_ng]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

---

### Post by karhulitos on 2006-10-14
Wasn't so straightforward (at least for me). I managed to follow instructions in [here]("http://ubuntuforums.org/showthread.php?t=105437") but ended up in this:
```
$ wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: No such device
```

and

```
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

I'm lost.. perhaps I try again.

---

### Post by karhulitos on 2006-10-14
> **tturrisi said:**
> [How To madwifi_ng]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

Thanks. Did all according to this and same result I have: ```
:/usr/src/madwifi-ng-r1751-20061014$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by karhulitos on 2006-10-14
If someone has Acer Aspire 504x and wlan is ok, pls tell me what should I do!
Help me stay in Ubuntu spirit!

There's the button to switch it off, could that cause my problems? (does not have any effect other than ```
[17182934.392000] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[17182934.392000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
```)

---

### Post by karhulitos on 2006-10-15
**My WLAN led is orange!**
Thank internet, thank Ubuntu, thank you all!

Scenario, Acer Aspire 504x WLMi and you want WLAN
1. do Ubuntu 6.10 (beta now, Edgy): Dapper needed kernel param. irqpoll noapic to start. 6.10 started without any propellers needed in my hat
2. the cool (stupid) WLAN button on this box needs some help: do [acer_acpi]("http://ubuntuforums.org/showthread.php?t=224350")
3. do madwifi-ng (may work with std Edgy madwifi drivers, didn't test): [How To madwifi_ng]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

Rok.

best regards,
Timo

---

### Post by karhulitos on 2006-10-15
Phuuh.. fix one break other.

Once again I can't see the obvious. I tried to search every possible corner but nothing found.

Problem is this:
- I got the wlan running here and I could see my neighbor's APs (and the orange led)
- at this point wlan was just fine after doing several reboots
- video was Mesa, I decided to give fglrx a shot. After few rounds I got direct rendering w/o freezes, etc, so it was ok
- a cold breeze went down my spine as I hadn't checked wlans for an hour or so. Jep, it was gone, iwconfig list was empty, no wlan0 or ath0 in ifconfig
- was thinking that the fglrx/restricted modules mess did this and I reinstalled madwifi-ng -> wlan was back up and I could see networks

After next reboot wlan was gone again. My wlan led is still lit so the acer_acpi appears to be running fine.
Doing echo "enabled: 0">/proc/acpi/acer/wireless / echo "enabled: 1">/proc/acpi/acer/wireless (stop/start wlan) does not have any effect on wlan0 visibility. Only reinstall of madwifi-ng helps.

Must be something very very small now I just can't see. WLAN disappears always after reboot.

Can anyone help me?

---

### Post by tturrisi on 2006-10-15
> **karhulitos said:**
> 

Must be something very very small now I just can't see. WLAN disappears always after reboot.

Can anyone help me?
let's see your /etc/network/interfaces file

---

### Post by karhulitos on 2006-10-16
I was also suspecting something's wrong there in interfaces file, that I gathered from other posts. I did not have 'ath0' at all there, so I was almost cheering to find someone suggesting to add that.

I added ath0 but it didn't have any effect for me. (commented part was just me connecting to windows to get some files here (which is an indication of me turning to a Ubuntu guy bit by bit :)))

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#       address 169.254.0.3
#       netmask 255.255.0.0
#       network 169.254.0.0
#       broadcast 169.254.0.255
#       gateway 169.254.0.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Thanks for helping me out here!

---

### Post by karhulitos on 2006-10-17
Anyone? Please help as I must be close. I can start Atheros on this box by reinstalling madwifi-ng everytime I want to connect..

Cheers!

---

### Post by karhulitos on 2006-10-17
Hmm, starting to look that Ubuntu and hardware just don't get along too well.

**after reboot**
dmesg | grep ath
[17179588.032000] ath_hal: module license 'Proprietary' taints kernel.
[17179588.032000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179588.064000] ath_rate_sample: 1.2 (svn r1751)
[17179588.236000] ath_pci: 0.9.4.5 (svn r1751)

dmesg | grep wifi
[17179588.340000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

**after reinstallation of madwifi-ng**
[17180072.288000] ath_pci: driver unloaded
[17180072.292000] ath_rate_sample: unloaded
[17180072.300000] ath_hal: driver unloaded
[17180121.092000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17180121.136000] ath_rate_sample: 1.2 (svn r1751)
[17180121.148000] ath_pci: 0.9.4.5 (svn r1751)
[17180133.024000] ath0: no IPv6 routers present

dmesg | grep wifi
[17180121.904000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17180121.904000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17180121.904000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17180121.904000] wifi0: mac 7.8 phy 4.5 radio 5.6
[17180121.904000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17180121.904000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17180121.904000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17180121.904000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17180121.904000] wifi0: Use hw queue 8 for CAB traffic
[17180121.904000] wifi0: Use hw queue 9 for beacons
[17180121.972000] wifi0: Atheros 5212: mem=0xd0200000, irq=169

What has wondered me all along is the fact that 

lspci | grep 06:05
06:05.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

but in above dmesg after madwifi-ng reinstall it says "wifi0: Atheros 5212" which I believe the chip is as the Windows driver also named like that.

I can do nothing no more..

r, Timo

---

### Post by tturrisi on 2006-10-18
suggestions:
uninstall ndiswrapper completely
check if have 2 madwifi versions installed
remove from /etc/network/interfaces:
auto wlan0
iface wlan0 inet dhcp

---

### Post by karhulitos on 2006-10-18
> **tturrisi said:**
> suggestions:
uninstall ndiswrapper completely
check if have 2 madwifi versions installed
remove from /etc/network/interfaces:
auto wlan0
iface wlan0 inet dhcp

Thanks for tips. I need a bit more help though..

1. uninstall ndiswrapper completely
- done (when you 1st time suggested that)
- except if "completely" is something else than Synaptics "uninst completely"
- how I can uninstall "completely"?

2. check if have 2 madwifi versions installed
- how can I do this?

3. remove wlan0 from /etc/network/interfaces:
- OK, will do that

Thank you!

regards, Timo

---

### Post by karhulitos on 2006-10-18
Gotten totally fed up with Acer, Atheros, wlan and a bit to Ubuntu too, I did this:


the previous steps to to get the chip running:
1. do Ubuntu 6.10 (beta now, Edgy): Dapper needed kernel param. irqpoll noapic to start. 6.10 started without any propellers needed in my hat
2. the cool (stupid) WLAN button on this box needs some help: do [acer_acpi]("http://ubuntuforums.org/showthread.php?t=224350")
3. do madwifi-ng (may work with std Edgy madwifi drivers, didn't test): [How To madwifi_ng]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo")

+ step 4 (from [http://rik.no-ip.com/~rik/?q=node/10](http://rik.no-ip.com/~rik/?q=node/10))

added Rik's lines to step 2's "/etc/init.d/acer_acpi_wireless_enable"

[edit] I needed to add a pause after acer_acpi wlan start as occasionally wlan didn't start properly

```
#!/bin/sh

case "$1" in

        start|"")

                modprobe acer_acpi
                chmod 777 /proc/acpi/acer/wireless
                echo "enabled: 1" >/proc/acpi/acer/wireless

		# to get around this ****
		sleep 10		
		rmmod ath_pci
		rmmod ath_rate_sample
		rmmod ath_hal
		rmmod wlan
		modprobe ath_pci
		ifconfig ath0 up
		# end of this ****

                ;;

        stop)

                echo "enabled: 0" >/proc/acpi/acer/wireless

                modprobe -r acer_acpi

                ;;

esac


```

Now I have wlan after reboot on Acer Aspire 5044WLMi and I can wait till this is completely fixed somewhere in Ubuntu/MadWifi.
Did not work after resuming from hibernation. Will run script manually then. 

Cheers.

Timo

---

### Post by lkcl on 2006-10-23
first thing you must do is locate acer_acpi, build and install it.
this will allow you to enable the wireless via ACPI.

if you do not do this, then no amount of trying to install madwifi-ng or even the ndiswrapper (which is unnecessary as madwifi-ng works fine) will do the trick.

see [http://tuxmobil.org/acer.html](http://tuxmobil.org/acer.html), search for the acer aspire 5024WLMi reports, or see my report (listed on tuxmobil.org)
which is also at [http://lkcl.net/reports/acer.5044WLMi.html](http://lkcl.net/reports/acer.5044WLMi.html)

in any of those reports you will see descriptions of what
you will need to do.

also there will be lots of advice on what else you will need to
do to get other hardware working well.

e.g. not installing the fglrx driver because it will make your
machine run like a dog.

---

### Post by lkcl on 2006-10-23
yes - there's something weird going on with acer_acpi.ko and the loading of the ath_pci.ko module.

the only way i found that i could get the wireless to work was
if i unloaded and reloaded the ath_hal.ko and ath_pci.ko modules _after_ acer_acpi.ko had been loaded and _after_ 'enable : 1' > /proc/acpi/acer/wireless had been carried out.

my guess is that the wireless cannot be properly recognised
[by the madwifi driver] until _after_ it has been enabled.

which kinda makes sense.

i haven't had time to track down whether there are any timing
related issues (by that i mean any delays needed between
enabling the wireless and loading ath_hal and ath_pci) because
the machine is now in the hands of its intended victim.

---

### Post by karhulitos on 2006-10-26
> **lkcl said:**
> 
e.g. not installing the fglrx driver because it will make your
machine run like a dog.

Thanks for the tips. I'll go through them soon.

I've got fglrx (the std one from restricted-modules) and I didn't notice any dogs around here.
HW accel says it's running so I thought I'm cool with ATI now. Except now that you said this box could run even faster, hmm..

Not being a native english speaker I take "running like a dog" means really really slow..? In that case my fglrx must be OK, this isn't slow enough to fit that description :)

---

### Post by anonymoususername on 2006-10-29
OK, sorry to bump an old thread, but I'm really stuck here. I have an Acer Aspire 5044WLMi laptop with the 64 bit version of Edgy and I've been following all the instructions in this thread. I can get as far as getting the wireless LED to light and the madwifi installed (although I have to reinstall it on reboot, but I'll worry about that later) and Ubuntu recognises my Wireless card, but when I scan for access points I get no results. No errors, just no results. Even if I enter what I think is the ESSID manually it still doesn't work, and yet it works on the same laptop using Windows. Any ideas?

---

### Post by anonymoususername on 2006-10-29
Anyone? I feel like I'm really close and I'm just gonna fail again. This is about the third thing I've tried. Also I've tried scanning on all 13 different channels. iwconfig says ath0 IEEE 802.11g, whereas the underside of my router says 802.11b, is this significant? My laptop claims to have 802.11 b/g wireless LAN, so if it needs changed, how would I go about it?

---

### Post by anonymoususername on 2006-10-29
Bump for impatience and lack of answer ](*,)

---

### Post by anonymoususername on 2006-10-29
Look, this is kind of my last resort, so if none of you can help can you at least link me to somewhere else I can ask? If I can't fix this I might end up having to go back to Windows, and I really don't want that.

---

### Post by karhulitos on 2006-11-03
I'm afraid I'm no help to you but I just write to tell you 'hang on in there'.

Somehow I got the feeling that Acer 5044 and Ubuntu isn't such a good match.
I was also thinking which Ubuntu I should install. I did i386 as some parts of 64 scared me off.

About WLAN.. I'm now happy although I still run the script in every boot.

Dunno if related but I remember uninstalling network-manager (if installed) and afterwards going to system -> Ylläpito (what was this menu in english?) -> networking. There I had my wlan listed but by default it said to me 'not in use'. Or actually the checkbox wasn't ticked. I hit properties, added essid, wep key in hex, checked 'take this conn in use' and basically that was it. The checkbox in the main network window might need another tick but perhaps it took this setting from the properties window. Don't know.

This I remember doing at some stage. But really can't confirm whether it's actually needed at all. Won't do it again as wlan runs now.

Damn I'd like to test Ubuntu 64 to see if it's any benefit compared to this i386 model..

Good luck!

---

