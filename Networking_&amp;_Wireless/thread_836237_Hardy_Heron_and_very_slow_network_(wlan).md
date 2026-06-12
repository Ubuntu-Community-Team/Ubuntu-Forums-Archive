---
title: "Hardy Heron and very slow network (wlan)"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by ttry72 on 2008-06-21
Dear All

After the upgrade session from feisty to Hardy, my network became very slow. Typically speed was approx 100-110 kbit/sec with Gutsy but now it's only about 20 kbit/second with Hardy. What has happened? According to some theards I read that this is quite typical incident in this case (Hardy).

Do you have any issues like this with Hardy Heron and have you solved this kind of case? Please help me if you know some tricks how to increase the speed of hardy.

My configuration is following:

description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wmaster0
       version: 01
       serial: 00:08:a1:8a:91:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.164.1.136 latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g

---

### Post by Eldis on 2008-08-20
Did you solve this ? I'm have very low speeds in my local lan arround 100 kb\s. Would expect to see something arround 500-800 kb\s. The really weird thing is I can download at the full rate of my adsl just the computers on my LAN using wlan cards are terrible slow communicating with each other.

---

### Post by stephsphynx on 2008-08-22
Same for me on the RT2500.  Since the upgrade to Hardy yesterday I now get 30 Kb/s on my wireless network (even between local machines).  I would also expect 500-800 Kb/s at least.  Wired works fine.

I'm thinking of downgrading :)

Any ideas?

---

### Post by stephsphynx on 2008-08-23
It works for me now!  Here's my solution, I can't guarantee that it'll work for you, so give it a shot at your own peril ;)

**Temporary solution:**
In the terminal, type "sudo iwconfig wlan0 rate 54M".  This should speed things up immediately, you don't have to do anything else.  You have to type this after every boot.

**Permanent solution:**
1. Get your network running:
Using the graphical user interface, get your internet connection working, even if it does poorly.  This generates the file you'll need in step 3.

2. Uninstall Network Manager:
In Synaptic Package Manager, search for "network manager".  In the list of results, tick "network-manager" ("mark for removal") and don't forget to click "apply" before you quit Synaptic.  FYI it will automatically also uninstall "network-manager-gnome".

3. Edit your internet settings file:
Edit your "interfaces" file which stores your internet connection settings.  In the terminal, type "sudo nano /etc/network/interfaces".  Add this line at the end: "up iwconfig wlan0 rate 54M" (as shown in the temporary solution).  Press "Ctrl+X", then "y", then "Enter" to save it.

At the end it should look something like this:

```

  auto wlan0
  iface wlan0 inet static
        address 192.168.1.11
        netmask 255.255.255.0
        gateway 192.168.1.1
        wpa-psk ***
        wpa-driver wext
        wpa-key-mgmt WPA-PSK
        wpa-proto WPA
        wpa-ssid ***
        up iwconfig wlan0 rate 54M
```

Some parts of this file might be different for you depending on whether you use WPA or WEP, and the "***" are individual to your network, so don't just copy and paste it all ;)

4. Load these settings automatically at bootup:
After I did step 3, the card wasn't associating it to the access point.  So I had to edit the script that's run at the very end of the bootup process to tell it to load "my new" settings from step 3.  To do this, in the terminal type "sudo nano /etc/rc.local".  Add the two lines "ifdown wlan0" and "ifup wlan0" before the "exit 0".  Press "Ctrl+X", then "y", then "Enter" to save it.

This is what it should look like:

```

  ifdown wlan0
  ifup wlan0

  exit 0
```

5. Reboot.
Or type "sudo ifdown wlan0" and then "sudo ifup wlan0".

P.s. check out this thread in Launchpad: _[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515/)_ where I found the temporary solution.  

Thanks to _[felimwhiteley]("http://ubuntuforums.org/member.php?u=177129")_ who walked me through this!

Good luck!

---

