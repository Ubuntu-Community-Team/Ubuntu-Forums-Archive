---
title: "Intel Pro 3945 ABG"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Gnodab on 2008-05-26
HP Pavilion dv6000 specifically dv6875se (special edition)

lspci excerpt
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1f:3c:14:5d:05
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g


Problem(s):
Can't connect to my router.

Doing a 'sudo iwlist wlan0 scan' will sometimes display 'no scan result', other times it shows my router, and once I it listed one of my neighbor's router.

NetworkManager is configured to connect to my router with wpa2.
nm-applet lists my router with 50-60% signal when it is listed.

The wireless toggle switch stays red.  Turning the switch from on, to off, to back on, will not allow to see any scan results until rebooted.

Another hp dv6000 laptop with atheros card works fine with ndiswrapper and NetworkManager, so the router and location is fine.

I've tried many fixes posted on the forums and elsewhere.
Such as enabling the hardy backport.
different versions of /etc/modprobe.d/iwl3950
wireless patch from intellinuxwireless.org
wicd
various other tips and patches

One of the fixes I didn't try was the ipw3950 driver because I couldn't find complete instructions.  The instructions I did fine were contradictory and mostly for previous kernel versions.

I have since reformatted and installed hardy and updated. (preserving my /home if that has any relevance)

So now that my system is restored to default 8.04 setup, any ideas on how to get my wireless working (and possibly the wireless toggle switch & led)?

---

### Post by chili555 on 2008-05-26
I would certainly reinstall *linux-backports-modules-hardy-generic.* After doing that, please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```Does your wireless now perform and, especially, scan as expected? If so, please apply the fix here: [http://ubuntuforums.org/showthread.php?t=808516](http://ubuntuforums.org/showthread.php?t=808516)

---

### Post by Gnodab on 2008-05-26
Done.

The wireless toggle led is now blue on boot up.
turning the wireless switch from on to off turns the led to red as expected
turning the toggle from off to on then doing 'sudo ifconfig wlan0 up' turns the led back to blue
which allows me to get results from 'sudo iwlist wlan0 scan' again...


Other than that, its the same.

'sudo iwlist wlan0 scan' and nm-applet still show my router, but it still doesn't connect.

One other thing I thought I'd point out:

When nm-applet tries to connect to wireless, it shows two gray orbs with the blue swirl and stays that way until it gives up.

When it comes to my wired connection, the orbs turn green during different stages of connecting.

Unsure what the orbs represent, but maybe it'll give you an idea of what stage of connecting it fails at.

---

### Post by chili555 on 2008-05-26
If you reboot without the wire connected, does the wireless connect? Have you double-checked your encryption details, WEP, WPA, WPA2, etc.?

Network Manager will not allow you to connect wirelessly if you are hooked up to the ethernet. [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by Gnodab on 2008-05-26
Didn't work.

Also, I noticed that the echo command in the linked post left the double quotes in the file /etc/modprobe.d/iwl3945

So, I edited the quotes out, but still no luck.

I also tried the following in /etc/modprobe.d/iwl3945, but no success.
```

alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 

```

I've switched back to the original without quotes for the mean time.

Thanks for the help.  Any other ideas?

---

### Post by Gnodab on 2008-05-27
I was looking at my router settings and logs and noticed that my laptop had been assigned a dhcp lease though my laptop never finished connecting.

I've gone through all the settings and steps I took, but I have yet to replicate it.

Update: nevermind, read the wrong mac address.  It was a dhcp lease for my wired connection...

---

### Post by Gnodab on 2008-05-30
don't remember doing it, but at some point, I enabled mac filtering on my router...

wireless works out of the box, though the led doesn't

the replies above fix that though.

---

