---
title: "Wireless connection issues with RT2500 device"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by EmperorSquirrels on 2007-04-21
I went out and bought a new wireless device that was claimed to work "out of the box" for Ubuntu. It even said "Linux support" on the box. But it doesn't work!
I have an ASUS WL-107g network card and it's supposed to use the RT2500 driver.

[http://linux-wless.passys.nl/query_part.php?brandname=Asus](http://linux-wless.passys.nl/query_part.php?brandname=Asus)

That is one of the links that I followed in my decision to buy the device. I'm stumped on this whole ordeal and I'd GREATLY appreciate any help on this matter.

Thanks.

---

### Post by EmperorSquirrels on 2007-04-21
Oh, and if it matters, I seem to have a connection strength, but no ability to connect to anything (or my own home network for that matter). Here's the output of iwconfig:

```
ra0       RT2500 Wireless  ESSID:"default"  
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=48/100  Signal level=-73 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Austin_KW on 2007-04-21
Which driver/version are you running.

For all ralink chipsets the best thing to do its to get latest legacy driver from serialmonkey.com
In a terminal
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)

Remove the old driver
sudo modeprove -r rt2500

Get tools to build the driver
sudo apt-get install build-essential linux-headers-`(uname -r)`
then extract and build the new driver  
tar -xvzf rt2500*.tar.gz
cd rt2500*/Module
make
sudo make install

You may need a reboot or just reinsert the card.

---

### Post by EmperorSquirrels on 2007-04-21
Even though I disabled the wireless network under System>Administration>Network, it says "FATAL: Module rt2500 is in use." What could be using it?

---

### Post by EmperorSquirrels on 2007-04-22
Is there any way I can find out what's using my rt2500 module? I removed ndisgtk and ndiswrapper, so I don't think they can be the culprit....

---

### Post by EmperorSquirrels on 2007-04-22
Okay nevermind I found out why it wasn't letting me remove it - I unplugged the wireless device and modprobe worked. I did exactly what you told me and everything seemed to go great, I plugged the thing back in and rebooted.... now my NetworkManager Applet has a wireless option, but I still cannot connect to default. iwconfig still yields the same sort of results, but I cannot establish a connection (NMA times out and reverts to the wired connection).

What now? :(

---

### Post by Austin_KW on 2007-04-22
These drivers do not work too well with network manager especially with WPA. What sort of encryptyion is on the network.

May have to remove network-manager.

---

### Post by AirRaven on 2007-04-22
[The issue's being discussed here as well](http://ubuntuforums.org/showthread.php?t=413594).

It works absolutely flawlessly in Breezy, Dapper, and Edgy- It's just the Feisty networking that appears to have broken support. 

Some people have had luck with Wicd, but I've not been able to get it to work.

---

### Post by Austin_KW on 2007-04-22
I think the problem is that the wext interface (iwconfig) provided by rt2500 driver is not compatible with the network-manager.
The solution seems to be (some combination of); Get the latest legacy driver, remove the network-manager, and configure the network using command line/interfaces file/third party utility.

---

### Post by EmperorSquirrels on 2007-04-22
Okay thanks. I think I'll try Dapper first, then if it still doesn't work I'll try removing the network manager, etc.

---

### Post by ssam on 2007-04-22
rt2500 support is not broken, its just that network manager does not know how to talk to it
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120)

you can still use it fine with the old networking tools

System -> Administration -> Networking

choose the rt2500 card
click properies.
disable roaming.
set your network name, and put in any WEP key you might need
for most network setups choose the DHCP configuration.

---

### Post by EmperorSquirrels on 2007-04-22
Okay, it works like a dream on Dapper. But I do want to eventually move up to Feisty. How would I remove the Network manager completely and make it so I can use my wireless adapter just like I can in Dapper?

---

### Post by ssam on 2007-04-23
you should not need to remove network-manager, just disable it by disabling roaming on that wireless card (see my post above)

if you really want to remove network-manager, then just find the package in synaptic and uninstall it. it will probably want to remove ubuntu-desktop, this is only a [/meta package]("https://help.ubuntu.com/community/MetaPackages") is it does not matter to much.

---

### Post by Austin_KW on 2007-04-23
So will disabling roaming stop network manager from trying to configure the rt2500. If I am using WPA, I really dont want the network manager or any of the other GUI tools trying to configure the wireless.

---

### Post by AirRaven on 2007-04-23
> **ssam said:**
> rt2500 support is not broken, its just that network manager does not know how to talk to it
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/37120)

you can still use it fine with the old networking tools

System -> Administration -> Networking

choose the rt2500 card
click properies.
disable roaming.
set your network name, and put in any WEP key you might need
for most network setups choose the DHCP configuration.

That's... Exactly what I did. 

Result? Identical problem.

---

### Post by EmperorSquirrels on 2007-04-23
Yes, I'm still having that problem in Feisty. I have a 128b hex password. Those exact same steps work in Dapper with no problem. It's just Feisty. I even tried disabling and removing NetworkManager Applet. It still didn't work.

---

### Post by Austin_KW on 2007-04-23
Make sure that you set your essid when the adapter is down ie. set your /etc/network/nterfaces to
iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 key "MyKeyInHex"
        pre-up iwconfig ra0 mode Managed
        pre-up ifconfig ra0 up
auto ra0

or from command line
sudo  ifconfig ra0 down
sudo iwconfig ra0 essid "MyRouterName"
sudo iwconfig ra0 key "MyKeyInHex"
sudo iwconfig ra0 mode Managed
sudo  ifconfig ra0 up
sudo dhclient ra0

---

### Post by EmperorSquirrels on 2007-04-23
Awesome thank you so much I've been trying to get this working since October! One more thing, though...  how do I wrap those commands up into a script that will run during startup automatically so I don't have to run all those commands every time I turn my computer on?

Thanks again! :)

---

### Post by Austin_KW on 2007-04-23
> **EmperorSquirrels said:**
> Awesome thank you so much I've been trying to get this working since October! One more thing, though...  how do I wrap those commands up into a script that will run during startup automatically so I don't have to run all those commands every time I turn my computer on?

Thanks again! :)

One of two ways
1. Commands can be added to /etc/rc.local (before the exit) which is run at the end of the boot sequence. You dont need sudo as rc.local is run as root.

2. The correct way is to modify /etc/network/interfaces as shown. The auto ra0 will bring the interface up at boot, and also run the 'preup' config command at boot and anytime 'ifup ra0' is done

---

### Post by EmperorSquirrels on 2007-04-23
I pasted those lines you said to put in the /etc/network/interfaces file and filled in my own information for the essid and the key, but it didn't work.

---

### Post by EmperorSquirrels on 2007-04-24
All right, I made an SH file with the commands in them and put "gksudo sh /location/script.sh" in as a boot script and it works. I guess I can live with entering my password an extra time during boot :) Especially in comparison with all the other troubles I've gone though. Thanks a lot.

---

### Post by Austin_KW on 2007-04-24
I did tell you that you could put the commands into /etc/rc.local and it would be run at the end of your boot sequence. Also that rc.local is run as root so no need for sudo and thus no password to enter.

---

### Post by gesquive on 2007-04-24
> **Austin_KW said:**
> Make sure that you set your essid when the adapter is down ie. set your /etc/network/nterfaces to
iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 key "MyKeyInHex"
        pre-up iwconfig ra0 mode Managed
        pre-up ifconfig ra0 up
auto ra0

or from command line
sudo  ifconfig ra0 down
sudo iwconfig ra0 essid "MyRouterName"
sudo iwconfig ra0 key "MyKeyInHex"
sudo iwconfig ra0 mode Managed
sudo  ifconfig ra0 up
sudo dhclient ra0

Thanks Austin_KW, finally, i have wireless internet again!

> **ssam said:**
> you should not need to remove network-manager, just disable it by disabling roaming on that wireless card (see my post above)

if you really want to remove network-manager, then just find the package in synaptic and uninstall it. it will probably want to remove ubuntu-desktop, this is only a [/meta package]("https://help.ubuntu.com/community/MetaPackages") is it does not matter to much.
You shouldn't just uninstall ubuntu-desktop, Here is a quick way of properly uninstalling network-manager (taken from the Wicd website) :
[LIST]
[*] Open the package manager and remove network-manager (this will remove ubuntu-desktop, but hold on)
[*] Press Apply, and network-manager (and ubuntu-desktop) will be removed.
[*] When the package list comes back up, click on network-manager and then press the Package menu at the top, and choose Lock version. Repeat with network-manager-gnome (even though they are not installed, this will still lock them as uninstalled)
[*] Install ubuntu-desktop (note that network-manager is not installed)
[/LIST]

---

### Post by zarathustra on 2007-04-25
> **Austin_KW said:**
> Make sure that you set your essid when the adapter is down ie. set your /etc/network/nterfaces to
iface ra0 inet dhcp
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "MyRouterName"
        pre-up iwconfig ra0 key "MyKeyInHex"
        pre-up iwconfig ra0 mode Managed
        pre-up ifconfig ra0 up
auto ra0

or from command line
sudo  ifconfig ra0 down
sudo iwconfig ra0 essid "MyRouterName"
sudo iwconfig ra0 key "MyKeyInHex"
sudo iwconfig ra0 mode Managed
sudo  ifconfig ra0 up
sudo dhclient ra0

Why in the pre-up do you have to bring the device up and down twice before setting the essid?

---

### Post by Austin_KW on 2007-04-25
> **zarathustra said:**
> Why in the pre-up do you have to bring the device up and down twice before setting the essid?

No Idea, I found this somewhere. But I have seen this in different forum posts for configuring the ralink chipsets going back a couple of years. Typically you see multiple settings of ssid, wpa-psk/wep key with the interface down and then up. 
Not sure it is necessary, or if it is people modifying their startup scripts until they work and then apply the old "if it ain't broke don't change it" rule. 
Another variant is scripts with sleep(1) between commands. It all seems a bit "voodoo" but if it works...


Also I remember reading that the ralink driver will not respond to some commands uptil the interface has been 'up' at least once, so maybe that is it.

---

### Post by erm67 on 2007-04-26
apt-get install rt2500 
will install the RaConfig2500 configuration utility for the driver, it searches for the wrong device so after the installation you will have to edit the config file 
sudo vi /etc/rt2x00.conf
and put in there a single line
ra0
save the file and start RaConfig2500 and you will be able to configure your card correctly and it will survive a reset.
Other distribution ships with the newest driver from cvs but it is highly unstable and crashes so better stick with the old reliable driver as in ubuntu feisty.

P.S. the utility is in universe not in main.

---

### Post by fraew on 2007-06-30
This works! 

i took the further steps of removing network-manager:
**sudo aptitude remove network-manager**

then add ra0 to my interfaces:
**sudo gedit /etc/network/interfaces**

[I]auto ra0
iface ra0 inet dhcp[/I]

i then restarted the device as so:
**sudo ifup ra0**

and it goes!, thanks very much, ive been trying to configure this damn card for the last 2 days

---

### Post by daller on 2007-06-30
My rt2500-based card will not modprobe...

daniel@daniel-desktop:~$ lspci | grep "RT2500"
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

Trying to modprobe it:

daniel@daniel-desktop:~$ sudo modprobe rt2500
FATAL: Module rt2500 not found.

I'm running Tribe 2!

Edit: and there nothing in ifconfig:

daniel@daniel-desktop:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:13:8F:E0:5D:ED
          inet addr:192.168.0.121  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fee0:5ded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:747194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:457632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1071244381 (1021.6 MB)  TX bytes:45537519 (43.4 MB)
          Interrupt:25 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1766 (1.7 KB)  TX bytes:1766 (1.7 KB)

---

### Post by Austin_KW on 2007-06-30
Maybe gusty has switched to the new beta drivers, You can download the legacy rt2500 driver from serialmonkey and build/install it

wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xvzf rt2500-cvs-daily.tar.gz
cd rt2500*/Module
make 
sudo make install

---

### Post by TravMan63 on 2007-07-06
> This works!

i took the further steps of removing network-manager:
sudo aptitude remove network-manager

then add ra0 to my interfaces:
sudo gedit /etc/network/interfaces

auto ra0
iface ra0 inet dhcp

i then restarted the device as so:
sudo ifup ra0

worked for me as well...

now I just need to re-enable wep and my essid....

<edit 9hrs later>
wep and essid work.  I was converting my wep key from binary and decimal to hex..... when it was already in HEX ...GRRR..

```

 ifconfig ra0 down
 ifconfig ra0 up
/etc/init.d/networking restart

```

<edit 12 hrs later>
wep works for encryption, but not for authentication.  I'm guessing the changes I applied to my modem (Moto SBG900) did not take effect until I rebooted the modem.
Rebooted the modem and could not connect until Authentication was changed to open system.
I can restrict users from logging on via MAC Access Control List.
<end edit #2>

---

