---
title: "Wired connection with 12.04 and Dell 1545"
date: 2014-01-05
forum: Networking &amp; Wireless
---

### Post by Panawe on 2014-01-05
I know there's a fair bit of info on this problem and I think I'm part way to solving it but I still can't get a stable wired internet connection on a Dell 1545 laptop on which I've installed Ubuntu 12.04.

It is equipped with:-
Broadcom BCM4312 802.11b/g LP-PHY

Marvell 88E8040 PCI-E [11ab:4354] rev3

I've installed (I hope) the Marvell Kernel 2.6X Linux driver package and I can get a brief wired connection but it's no more than a few seconds before it stops. I can see a huge update waiting and I want to get the wireless adaptor working but until I get the wired connection going I'm stuck!

TIA

---

### Post by varunendra on 2014-01-06
> **Panawe said:**
> I can see a huge update waiting and I want to get the wireless adaptor working but until I get the wired connection going I'm stuck!

Try manually downloading the nonfree firmware package from here : [http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/raring/all/linux-firmware-nonfree/download)

Then copy it to your Ubuntu desktop and install by simply double-clicking, or via terminal -
```
sudo dpkg -i Desktop/linux-firmware-nonfree_1.14ubuntu1_all.deb
```

If we got either one working, troubleshooting the other one would become a lot easier.

---

### Post by Panawe on 2014-01-06
Hi, thanks for this.

Done that and package seemed to install but still no stable wired connection?

Just to clarify, here's the terminal printout for the installation...

   sudo dpkg -i linux-firmware-nonfree_1.14ubuntu1_all.deb  
 (Reading database ... 143187 files and directories currently installed.)  
 Preparing to replace linux-firmware-nonfree 1.14ubuntu1 (using linux-firmware-nonfree_1.14ubuntu1_all.deb) ...  
 Unpacking replacement linux-firmware-nonfree ...  
 Setting up linux-firmware-nonfree (1.14ubuntu1) ...  
 person@person-Inspiron-1545:~/Desktop$

---

### Post by Panawe on 2014-01-06
Been trying different things but still no stable wired connection.
Does this print from Terminal throw any light on the  problem?

   person@person-Inspiron-1545:~$ lsmod  | grep "brcmsmac\|b43\|ssb\|bcma\|wl"  
 b43                   364596  0  
 mac80211              541819  1 b43  
 cfg80211              453853  2 b43,mac80211  
 bcma                   39810  1 b43  
 ssb                    51554  1 b43  
 person@person-Inspiron-1545:~$ lspci -n | grep 14e4  
 0c:00.0 0280: 14e4:4315 (rev 01)  
 person@person-Inspiron-1545:~$ 

Don't honestly understand them :/

---

### Post by varunendra on 2014-01-06
> **Panawe said:**
> Done that and package seemed to install but still no stable wired connection?
Sorry I should have clarified that - it was meant to help the wifi. Is it (wireless) still not working?

Your second post simply shows that the correct drivers are loaded. Did you try connecting to a wireless network? Does it even scan available networks yet? Try -
```
sudo iwlist scan
```

If it fails to scan wireless networks, please post the output of -
```
dmesg | grep b43
```

Since this card is supposed to work with the correct firmware, and the firmware should have been installed with the nonfree package, I'm focusing only on the wireless for now.

---

### Post by Panawe on 2014-01-07
Thanks for your help.

I need to get the laptop working wirelessly eventually, I just thought the wired connection was essential as a first step.

Here's the Terminal printout:

   person@person-Inspiron-1545:~$ sudo iwlist scan  
 [sudo] password for person:  
 wlan0     Interface doesn't support scanning : Network is down  
 

 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 person@person-Inspiron-1545:~$ dmesg | grep b43  
 [   18.083036] b43-phy0: Broadcom 4312 WLAN found (core revision 15)  
 [   18.124219] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1  
 [   33.040619] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)  
 [   33.348375] b43-phy0: Radio hardware status changed to DISABLED  
 [   33.349807] b43-phy0: Radio turned on by software  
 [   33.349812] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.  
 
I guess that stuff about the RF-kill button is a clue?

Thanks.

---

### Post by varunendra on 2014-01-07
Yup, try the wireless switch or key-combination - whatever your laptop has to toggle the wifi on/off. If that doesn't seem to work, try -
```
rfkill unblock all
```

Then check -
```
rfkill list
```

If the wifi (apparently "phy0") still seems to be "Hard blocked", and the toggle switch doesn't work, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Panawe on 2014-01-07
Having pressed the button I get this:

   person@person-Inspiron-1545:~$ iwlist scan  
 wlan0     No scan results  
 

 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  


 person@person-Inspiron-1545:~$ dmesg | grep b43  
 [   18.083036] b43-phy0: Broadcom 4312 WLAN found (core revision 15)  
 [   18.124219] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1  
 [   33.040619] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)  
 [   33.348375] b43-phy0: Radio hardware status changed to DISABLED  
 [   33.349807] b43-phy0: Radio turned on by software  
 [   33.349812] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.  
 [ 1129.028288] b43-phy0: Radio hardware status changed to ENABLED  
 [ 1129.216292] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)  
 
It's trying to connect to the router wirelessly but not succeeding.

Information overload [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

   person@person-Inspiron-1545:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network                
        description: Network controller  
        product: BCM4312 802.11b/g LP-PHY  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:0c:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:17 memory:f69fc000-f69fffff  
   *-network  
        description: Ethernet interface  
        product: 88E8040 PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:09:00.0  
        logical name: eth0  
        version: 13  
        serial: 00:23:ae:1e:73:c8  
        capacity: 100Mbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2  driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)  
   *-network  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:24:2b:66:1c:3c  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=b43  driverversion=3.8.0-29-generic firmware=666.2 link=yes multicast=yes  wireless=IEEE 802.11bg  
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by varunendra on 2014-01-07
I'd prefer the wireless_script's output for an "information overload". :)

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Panawe on 2014-01-07
You mean like this?

```

   person@person-Inspiron-1545:~$ lshw -C network  
 WARNING: you should run this program as super-user.  
   *-network                
        description: Network controller  
        product: BCM4312 802.11b/g LP-PHY  
        vendor: Broadcom Corporation  
        physical id: 0  
        bus info: pci@0000:0c:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list  
        configuration: driver=b43-pci-bridge latency=0  
        resources: irq:17 memory:f69fc000-f69fffff  
   *-network  
        description: Ethernet interface  
        product: 88E8040 PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:09:00.0  
        logical name: eth0  
        version: 13  
        serial: 00:23:ae:1e:73:c8  
        capacity: 100Mbit/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 latency=0 link=no multicast=yes port=twisted pair  
        resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)  
   *-network  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:24:2b:66:1c:3c  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes driver=b43 driverversion=3.8.0-29-generic firmware=666.2 link=yes multicast=yes wireless=IEEE 802.11bg  
 WARNING: output may be incomplete or inaccurate, you should run this program as super-user.  
 
```

Is this the wireless script output?

---

### Post by varunendra on 2014-01-07
> **Panawe said:**
> You mean like this?
....
Is this the wireless script output?
Uh oh, looks like you missed this part of my earlier post -
> **varunendra said:**
> ..If the wifi (apparently "phy0") still seems to be "Hard blocked", and the toggle switch doesn't work, **please follow the _"Wireless Script" link in my signature_, download and run the script as per instructions there, and post back the report it generates.**

So it is a diagnostics script created and maintained by Forum member (a mod) Wild Man, which creates a detailed report about the overall wireless setup and related settings/configurations.

Please follow the "Wireless Script" link in my signature and the linked post should be easy enough to follow. :) Post back the report (wireless-info.txt file or its contents) that the script generates.

---

### Post by Panawe on 2014-01-07
Right, getting there slowly. How's this?

```


*************** info trace ***************

***** uname -a *****

Linux annie-Inspiron-1545 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 15:31:16 UTC 2013 i686 i686 i386 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

***** lspci *****

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
    Subsystem: Dell Device [1028:02aa]
    Kernel driver in use: sky2
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge

***** lsusb *****

Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

b43                   364596  0 
mac80211              541819  1 b43
cfg80211              453853  2 b43,mac80211
bcma                   39810  1 b43
ssb                    51554  1 b43

***** nm-tool *****

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     No scan results


***** resolv.conf *****


***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** modinfo *****

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     F6F97440A9DA6418F4C2856
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F7A1658A8CB1D58E3D347C1
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 

filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     14621F6EC014F731244437C
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 686 


***** udev rules *****

# PCI device 0x11ab:/sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[    1.380303] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    1.380323] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.380340] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.380357] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.380373] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.452292] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   15.985372] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   16.028218] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   28.164249] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   33.701297] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.706292] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

****************** done ******************


```

Many thanks for your patience.

---

### Post by varunendra on 2014-01-07
Everything in the script report looks normal, except that it still can't scan networks. Let's see if going more verbose can give us some hint.

But before that, try these quick shots first -

[indent]1) If you have access to the router/access-point, log into its management interface and see if it has "WMM" support under "QoS" (may have to refer to its user manual). If there is, make sure it (WMM support) is disabled.

2) If it supports N-channel, and it is enabled, try disabling it (set the router to b/g mode only).[/indent]

Both of these are known to cause problems sometimes, although those problem are connectivity related, not scanning failure. But if they couldn't help, they won't hurt either and are worth a shot.

One more thing that I'd like to try with the driver itself is the following trick -
```
sudo modprobe -rv b43
sudo modprobe -v b43 qos=0 btcoex=0
```
This will be a temporary change that will be lost at next boot. If it helps scanning/connecting, we can make it permanent.

If none of the above help, it's time for further investigation.., proceed as follows -

Please do a reboot, make sure the wifi is enabled, then do -
```
sudo iwlist scan
```

Let it try and fail.., then run these commands -
```
egrep 'net|wlan|b43|80211' /var/log/syslog > Desktop/syslog
egrep 'net|wlan|b43|80211' /var/log/kern.log > Desktop/kern.log
```

This will create two files "syslog" and "kern.log" on your desktop. Either attach these files, or better, upload their contents at [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) and post the pastebin link in your next post.

Also, let's see if the latest version of the sta driver is available from the repos, although it is less likely to help -
```
apt-cache show bcmwl* | grep Version
```

---

### Post by Panawe on 2014-01-07
Right oh. Well, I had a look at the router setup and the QoS class in "0-WMM best effort default". When I tried to change it to "1-WMM background" I got the message "Rule name cannot be blank" and I don't know what I'm doing so I left it as it was.

Then..

```

sudo modprobe -rv b43 
sudo modprobe -v b43 qos=0 btcoex=0
[/code)

Still couldn't connect wirelessly.

I have pasted the sys and kern logs into "pastebin" under the name Panawe - haven't done this before, are they available?

And finally...

[code]
   annie@annie-Inspiron-1545:~$ sudo iwlist scan  
 [sudo] password for annie:  
 wlan0     Interface doesn't support scanning : Network is down  
 

 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 annie@annie-Inspiron-1545:~$ 
 

 
```

Phew, I'll be amazed if I did all that correctly!

Thanks.

---

### Post by Panawe on 2014-01-07
Okay, thought I'd done something wrong. Are these available?

[http://pastebin.ubuntu.com/6709534/](http://pastebin.ubuntu.com/6709534/)

[http://pastebin.ubuntu.com/6709551/](http://pastebin.ubuntu.com/6709551/)

Latter is sys log.

---

### Post by Panawe on 2014-01-07
Stop what you're doing! I'm connected. It transpires that security aspects of the wireless login were wrong (WEP vs WPA). I'm sorry to have caused you all this trouble and I'm amazed at your patience but for the moment (heartfelt prayers) it looks like I'm sorted. Wirlessly anyway, don't know about wrired.

Thanks so much.

---

### Post by Panawe on 2014-01-07
Okay, not completely out of the woods yet.

Have downloaded and installed the enormous update, rebooted and now can't find my wireless connection in Network manager!

Help!

---

### Post by varunendra on 2014-01-08
Let's see the fresh report of the wireless_script then. :)

And please remove the [Solved] prefix, since we are still in the struggle period (which is surprising to me, because this card/driver shouldn't be so hard to troubleshoot).

---

### Post by Panawe on 2014-01-10
Ah, yes. What I did was install Synaptic Package manager and tick the bcmwl-kernel-source package which I had previously been unable to load without losing my (wireless) internet connection. Wireless now rock solid.

I still can't get the wired connection working but that's not important (unless there's a simple fix, otherwise I don't need it).

Many thanks for your help - I think we're solved now so I'll leave the thread as solved unless you have any further suggestions?

Thanks.

---

### Post by varunendra on 2014-01-10
Nope, no suggestions. Just a question -

May I see the current version of the bcmwl driver you are using? Yours is one of the rare posts where I've seen this card (BCM4312) working 'solid' with the sta driver, so I may include this version as an alternative to b43.

To see the package status and version -
```
dpkg -l | grep bcmwl
```

Thanks for the feedback. :)

---

### Post by Panawe on 2014-01-10
Here goes:

```

   person@person-Inspiron-1545:~$ dpkg -l | grep bcmwl  

 ii  bcmwl-kernel-source                         6.20.155.1+bdcom-0ubuntu0.0.2           Broadcom 802.11 Linux STA wireless driver source  
 person@person-Inspiron-1545:~$ 

```

Seems okay now though I did a lot of head-scratching.

Cheers.

---

### Post by varunendra on 2014-01-10
Awesome ! I had blacklisted this version in my mind.. Maybe that was ....0ubuntu0.0.**[COLOR="#FF0000"]1[/COLOR]** or even earlier. :P

Thanks for the confirmation. Hope it keeps working as nicely as it is currently. :)

---

### Post by Panawe on 2014-01-10
When I tried the update via Terminal I lost the wireless connection and the update froze. When I Used SPM I noticed the wireless connection dropped but immediately reconnected.

Glad to be of help :)

---

