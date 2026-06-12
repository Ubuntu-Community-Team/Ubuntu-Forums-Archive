---
title: "HP laptop wi-fi works every other boot (16.04LTS RTL8188EE)"
date: 2017-01-21
forum: Networking &amp; Wireless
---

### Post by justincase2 on 2017-01-21
This is a very consistent problem to recreate.  Every odd-numbered reboot or restart results in a working wi-fi connection, failing for even numbers.

HP Laptop 15-g018dx with fresh Ubuntu desktop install and upgrades/updates.

Version:
    ```
$ lsb_release -a
    No LSB modules are available.
    Distributor ID:    Ubuntu
    Description:    Ubuntu 16.04.1 LTS
    Release:    16.04
    Codename:    xenial
```

Adapter:
    ```
$ lspci -vvnn | grep Network
    03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company RTL8188EE Wireless Network Adapter [103c:197d]
```

NetworkManager status when it's working:
    ```
$ sudo service NetworkManager status
    NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2017-01-19 18:39:51 PST; 7min ago
     Main PID: 940 (NetworkManager)
     CGroup: /system.slice/NetworkManager.service
     &#9500;&#9472; 940 /usr/sbin/NetworkManager --no-daemon
     &#9500;&#9472;1142 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-wlo1.pid -lf /var/lib/NetworkManager/dhclient-ead33c49-08dd-4240-ae63-1edec65394f6-wlo1.lease -cf /var/lib/NetworkManager/dhclient-wlo1.conf wlo1
     &#9492;&#9472;1154 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
    dhclient[1318]: XMT: Info-Request on wlo1, interval 940ms.
    dhclient[1318]: RCV: Reply message on wlo1 from fe80::a62b:8cff:fed2:ab22.
    NetworkManager[940]: <info>  nameserver '2001:578:3f::30'
    NetworkManager[940]: <info>  nameserver '2001:578:3f:1::30'
    NetworkManager[940]: <info>  dhcp6 (wlo1): state changed unknown -> bound
    NetworkManager[940]: <info>  dhcp6 (wlo1): client pid 1318 exited with status 0
    NetworkManager[940]: <info>  dhcp6 (wlo1): state changed bound -> done
    NetworkManager[940]: <info>  WiFi hardware radio set enabled
    NetworkManager[940]: <info>  WWAN hardware radio set enabled
    NetworkManager[940]: <info>  manager: startup complete
```

NetworkManager status when it's not working:
    ```
$ sudo service NetworkManager status
    NetworkManager.service - Network Manager
     Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2017-01-19 18:49:12 PST; 1min 6s ago
     Main PID: 917 (NetworkManager)
     CGroup: /system.slice/NetworkManager.service
     &#9492;&#9472;917 /usr/sbin/NetworkManager --no-daemon
    NetworkManager[917]: <warn>  failed to enumerate oFono devices: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
    NetworkManager[917]: <info>  ModemManager available in the bus
    NetworkManager[917]: <info>  supplicant: wpa_supplicant running
    NetworkManager[917]: <info>  device (wlo1): supplicant interface state: init -> starting
    NetworkManager[917]: <info>  device (wlo1): supplicant interface state: starting -> ready
    NetworkManager[917]: <info>  device (wlo1): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
    NetworkManager[917]: <info>  device (wlo1): supplicant interface state: ready -> inactive
    NetworkManager[917]: <info>  manager: startup complete
    NetworkManager[917]: <info>  WiFi hardware radio set enabled
    NetworkManager[917]: <info>  WWAN hardware radio set enabled
```

And finally, Syslog when good (and common lines when bad are marked with an asterisk below:
```
* kernel: rtl8188ee 0000:03:00.0 wlo1: renamed from wlan0
    * NetworkManager: <info>  devices added (path: /sys/devices/pci0000:00/0000:00:02.4/0000:03:00.0/net/wlo1, iface: wlo1)
    * NetworkManager: <info>  device added (path: /sys/devices/pci0000:00/0000:00:02.4/0000:03:00.0/net/wlo1, iface: wlo1): no ifupdown configuration found.
    * NetworkManager: <info>  (wlo1): using nl80211 for WiFi device control
    * NetworkManager: <info>  device (wlo1): driver supports Access Point (AP) mode
    * NetworkManager: <info>  manager: (wlo1): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/2)
    * NetworkManager: <info>  device (wlo1): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
    * kernel: IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
    * kernel: IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
    * NetworkManager: <info>  device (wlo1): supplicant interface state: init -> starting
    * NetworkManager: <info>  device (wlo1): supplicant interface state: starting -> ready
    * NetworkManager: <info>  device (wlo1): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
    * kernel: IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
    * NetworkManager: <info>  device (wlo1): supplicant interface state: ready -> inactive
    NetworkManager: <info>  device (wlo1): Activation: starting connection 'My-Wi-Fi' (ead33c49-08dd-4240-ae63-1edec65394f6)
    NetworkManager: <info>  device (wlo1): state change: disconnected -> prepare (reason 'none') [30 40 0]
    NetworkManager: <info>  device (wlo1): state change: prepare -> config (reason 'none') [40 50 0]
    NetworkManager: <info>  device (wlo1): Activation: (wifi) access point 'My-Wi-Fi' has security, but secrets are required.
    NetworkManager: <info>  device (wlo1): state change: config -> need-auth (reason 'none') [50 60 0]
    NetworkManager: <info>  device (wlo1): state change: need-auth -> prepare (reason 'none') [60 40 0]
    NetworkManager: <info>  device (wlo1): state change: prepare -> config (reason 'none') [40 50 0]
    NetworkManager: <info>  device (wlo1): Activation: (wifi) connection 'My-Wi-Fi' has security, and secrets exist.  No new secrets needed.
    NetworkManager: <info>  sup-iface[0x248fa10,wlo1]: config: set interface ap_scan to 1
    wpa_supplicant: wlo1: SME: Trying to authenticate with a4:2b:8c:d2:ab:23 (SSID='My-Wi-Fi' freq=2462 MHz)
    kernel: wlo1: authenticate with a4:2b:8c:d2:ab:23
    NetworkManager: <info>  device (wlo1): supplicant interface state: inactive -> authenticating
    wpa_supplicant: wlo1: Trying to associate with a4:2b:8c:d2:ab:23 (SSID='My-Wi-Fi' freq=2462 MHz)
    kernel: wlo1: send auth to a4:2b:8c:d2:ab:23 (try 1/3)
    kernel: wlo1: authenticated
```

On those boots when it's not working, doing a `sudo /etc/init.d/network-manager stop` and then `...start` does not fix things.

When it's bad, no wi-fi zones show up in the panel app.  It thinks both networking and wi-fi are enabled in that panel.  Toggling the keyboard wi-fi doesn't help.

I won't add to this the analysis of good->suspend->re-awaken since this post is already so long.

Any thoughts?  I considered dropping a link into maybe /etc/rc6.d perhaps but I'm a bit of a noob to attempt that myself.

---

### Post by wildmanne39 on 2017-01-21
Does this command restart the wifi
```
sudo systemctl restart NetworkManager.service
```

---

### Post by justincase2 on 2017-01-21
Nice try... and no, it doesn't.  I think I'm going to try to compile the RTL8192 driver from the Realtek site manually and then modprobe it into existence.  I'll let you know if that works out.  I tried the PPA already which is mentioned in [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek) but that didn't include an ARM64 package unfortunately.

UPDATE:

I'm back from that field trip with nothing positive to report from the experience.  I built and modprobe'd from [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver) but it didn't seem to be placing the drivers into the correct folder /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/**realtek**/whatever..., attempting to manually place them where they belonged threw an error about UEFI protection (worked around), then dmesg was throwing an error about a duplicate exported function, attempted to fix that... and decided to bail.  Put things back the way they were and confirm that I'm back at square one.

---

### Post by wildmanne39 on 2017-01-21
Pretty sure it is the network manager bug but you should run the wireless script that is in my ssignature when it will connect and when it will not and post the results for both.

---

### Post by justincase2 on 2017-01-22
> **wildmanne39 said:**
> Pretty sure it is the network manager bug but you should run the wireless script that is in my ssignature when it will connect and when it will not and post the results for both.

Please find attached the zipped version of when an odd boot results in everything working.  And then I have attached the same for an even boot when it doesn't.

Repeating my earlier assertion that running ```
sudo systemctl NetworkManager.service
``` does not fix anything, does not result in Internet connectivity, nor wi-fi zones showing up in the panel.  The only thing that works is exactly **one** reboot.

I am noting that the compatible hardware list suggests that for this adapter, it must be recompiled from source or brought in from the indicated PPA.  I've mentioned above that the PPA does not have an ARM64 package so that fails.  The just-patch-the-kernel option is a little problematic for beginners, for what it's worth.

---

### Post by justincase2 on 2017-01-22
Analyzing the output from your script it looks like the apartment complex here is fond of Netgear-branded wi-fi routers and as a result, it's Channel-11 heavy at the moment.

There are eleven channels in the U.S. but honestly, only three are usable without bandwidth-spillover from the neighboring channels:  1, 6 & 11.  Looks like Netgear out-of-box wants to be 11 so there are five routers in my apartment complex with that.  There appear to be about four on channel 6 and only one was on channel 1.

As a result of this I've moved my Netgear wi-fi router to use channel 1.  Although I'll get less contention with my neighbors this hasn't resulted in a fix.  It still exactly works every other boot on Ubuntu 16.04 LTS.

Of course, it works always on all other computers/devices that I have here.  iPads x 3, MacBook, iPhone, Windows 10 laptop, Android smartphones x 2, Microsoft Phone, Raspberry Pi 3 x 5, etc.

---

### Post by jeremy31 on 2017-01-22
You have some strange results there.  First use ```
sudo -H gedit /etc/modules
```
Delete rtl8192ce, save, and exit gedit.
Then check ```
ls /lib/firmware/rtlwifi | grep rtl8188efw.bin
```
That command should return rtl8188efw.bin if the file is present, if not
```
sudo apt-get install --reinstall linux-firmware
```
Reboot

---

### Post by justincase2 on 2017-01-22
Interestingly enough, I saw the missing .bin file and had just chased it down in somebody's github repository (Larry) and had manually placed it into a newly-created /lib/firmware/rtlwifi folder but that hadn't fixed it.

Following your advice:  check, check but still running the last line anyway (check).

Still no improvement.  I'll run the script again but the girlfriend's getting a little angry that I've been at this for five hours straight.

---

### Post by justincase2 on 2017-01-22
Here's then the latest good/bad version of the wi-fi script.  Can't say that I see anything different from the last failure.

I did temporarily add an /etc/mobprobe.d/rtl8192ce.conf with the option to turn on debug but wasn't exactly sure which log would receive that.  I deleted that, for what it's worth.  The .bin file absence from earlier was revealed in the dmesg log but that appears to be fixed now.  And yet, the behavior is exactly the same.

---

### Post by justincase2 on 2017-01-22
Continuing to troubleshoot:

1. Moving within 6' of the wi-fi router produces no difference
2. Shutting down (rather than rebooting/restarting) actually works 100% of the time!
3. Disabling SSID broadcast on the router doesn't change things (same behavior on reboot and shutting down and powering on works 100% of the time)

So... is this a problem with the /etc/rc6.d setup...?  I note here the difference between the links in the 0 and 6 modes for shutting down and for rebooting.  There's honestly not a lot of difference and yet 0 works 100% of the time and 6 works every other time.  (Things that make you say "hmmm....")

6: K01alsa-utils => alsa-utils [Sound drivers, methinks]
6: K01bluetooth => bluetooth [Note that no bluetooth adapters show up under Settings]
6: K01cups-browsed => cups-browsed [Sounds like Apple printers with the Bonjour protocol so probably nothing]
0 & 6: K01irqbalance
0 & 6: K01kerneloops
0 & 6: K01lightdm
0 & 6: K01plymouth
0 & 6: K01resolvconf
0 & 6: K01speech-dispatcher
0 & 6: K01thermald
0 & 6: K01unattended-upgrades
0 & 6: K01urandom
0 & 6: K01uuidd
0 & 6: K02avahi-daemon
0 & 6: K03sendsigs
0 & 6: K04rsyslog
0 & 6: K05hwclock
0 & 6: K05umountnfs
0 & 6: K06networking
0 & 6: K07umountfs
0 & 6: K08umountroot
0: K09halt => halt
6: K09reboot => reboot

The only real difference appears to be the very last step.  The wifi adapter would completely lose all power in mode 0 and wouldn't necessarily in mode 6.

---

### Post by justincase2 on 2017-01-22
Individually toggled from the defaults the options ips, fwlps and msi in /etc/modprobe.d/rtl8188e.conf to no effect.  I turned on swlps and off fwlps, no effect.

Disabled IPv6 support in BIOS, no effect.

---

