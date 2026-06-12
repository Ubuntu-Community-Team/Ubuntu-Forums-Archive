---
title: "Repeated 'authentication required' for wifi"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by vghaisas on 2014-05-21
I recently upgraded to 14.04 and over the last few days, I'm having frustrating problems while connecting to my home wifi network, one I've been connecting to without a problem (with earlier Ubuntu versions) for over a year. Windows computers and Android devices have no trouble connecting either.


The problem is that whenever I connect to the network and enter the _correct password_, it tries connecting for a little while, and simply gives the the 'Authentication required' dialog box again.


I have a Lenovo Z400 laptop (wifi works perfectly on Windows 8 on the same machine, by the way), and a Linksys EA4500 router.


The 'wireless' page in the router configuration looks like this (SSID and passphrase removed): [http://imgur.com/0PWHRpo](http://imgur.com/0PWHRpo).

```

sudo lshw -class network

``` 

```

    *-network
           description: Ethernet interface
           product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           vendor: Realtek Semiconductor Co., Ltd.
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: eth0
           version: 05
           serial: 20:89:84:f1:32:3c
           size: 10Mbit/s
           capacity: 100Mbit/s
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
           resources: irq:42 ioport:2000(size=256) memory:d3404000-d3404fff memory:d3400000-d3403fff
      *-network
           description: Wireless interface
           product: Centrino Wireless-N 2230
           vendor: Intel Corporation
           physical id: 0
           bus info: pci@0000:03:00.0
           logical name: wlan0
           version: c4
           serial: 68:17:29:be:21:2f
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=18.168.6.1 ip=192.168.1.149 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
           resources: irq:46 memory:d3500000-d3501fff

```

```

sudo lsusb

```

```

    Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
    Bus 001 Device 003: ID 8087:07da Intel Corp. 
    Bus 001 Device 005: ID 046d:c077 Logitech, Inc. 
    Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
    Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
    Bus 003 Device 002: ID 13d3:5170 IMC Networks 
    Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

also, during while trying to connect, ```
dmesg | grep wlan0
``` tells me I've been "deauthenticated from <address> (Reason: 2)".


I've also tried [deleting all my saved networks, reboting and then reconnecting]("http://(http://askubuntu.com/questions/180126/wireless-network-found-cant-connect-repeated-requests-for-authentication"), which sometimes works, and sometimes doesn't.


Can someone please tell me why this is happening, and what I can do to fix it?

---

### Post by squakie on 2014-05-22
I'm offering a suggestion that has worked for me.  It seems network manager somehow remembers even a failed attempt at connection - keeping the bad password.  I would:

- click on the network manager icon on the top bar
- click on edit connections
- if the network you are trying to connect to shows then delete it

Now try to connect again, being sure you have the exact password/passphrase - exact spelling, case, etc..

That's what I've had to do in the past - don't know if it will work for you or not.   Also - be sure you have the proper type - WEP/WPA/WPA2-TKIP, etc..

---

### Post by Harsh_Parikh on 2014-05-22
You can know the real password and anything related to your network with the help of your gateway......To do this first open terminal>type nm-tool>write down the last second option which is gateway>then go to browser>type gateway in address bar>and admin and password and you will be brought to your router's actual connection.....

---

### Post by vghaisas on 2014-05-22
@squakie, no, that can't be it. I've tried every possible combination of 'delete and re add' connections, including rebooting between deleting and re-adding, and every single time I'm completely sure I've been typing the right password (I entered the same one on several other devices during testing).

---

### Post by vghaisas on 2014-05-22
@Harsh_Parikh, I've used the router's administration several times - both from this laptop and other devices - to make configuration changes. The screenshot of my router's configuration that I posted in my question is from there. The password is correct.

---

### Post by Harsh_Parikh on 2014-05-22
Then,you should try it using LAN cable.....and then re-configured your all network settings and then try to connect wirelessly.......

---

### Post by squakie on 2014-05-22
your router is showing mixed mode - this has caused problems for others in the past.  Try setting it to a given value.

---

### Post by varunendra on 2014-05-22
Can you please try changing the security mode for 2.4 GHz band in the router to "WPA2 personal" only? Additionally (if required) also try setting the channel width to 20 MHz, not 20/40 auto mode. Reboot the router after saving the changes. (yeah I understand these same settings might have been working earlier, but they can be problematic at times, and what I suggested often helps).

If this doesn't make any difference, please post back a detailed report generated by 'wireless_script', following instructions in this post (while keeping the router settings same as suggested above) : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by vghaisas on 2014-05-22
Thank you, gentlemen. Changing to Wireless-g and WPA-2 Personal *seems* to have solved the problem. If it stays so in the next few days, I shall mark this thread as solved. :)

---

