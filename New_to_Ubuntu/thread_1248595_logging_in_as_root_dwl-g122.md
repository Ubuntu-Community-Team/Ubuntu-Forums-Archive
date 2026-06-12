---
title: "logging in as root dwl-g122"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by fields2grand on 2009-08-24
My only purpose for installing linux was so I wouldn't have to boot live to Backtrack.  I have a dwl-g122  ver. B that worked great in Backtrack Live.  Never had to configure drivers or anything.  I've spent a good portion of over 24 hours of work time trying to figure out how to load the ralink drivers for my Dlink usb and I still don't have it.  From what I understand I need to modify the kernel and compile drivers. I got it to work w/ ndiswrapper but I need monitor mode capabilities.   I've followed readme after readme and half the time I can't do what it asks because of root priveleges which I was sure I was logged in as.  I can't extract files in certain folders becaues i'm not the "root".  I've posted on this forum under wireless networking and have had no luck getting a response.  My question is this.  Is there a linux program, redhat or whatever that I can install and actually have my Dlink USB card work without having to compile and modify kernels and bend over backwards?  Thank you for your time and replies.

---

### Post by decoherence on 2009-08-24
Hi there! I assume you're using Ubuntu. If so, that's why you aren't having any luck as a 'root' user. The root user is disabled on Ubuntu. Instead preface your commands with "sudo" or, if you want a complete root console, run "sudo -i" and type your commands as if you were root.

It is useful to know what version of Ubuntu you're running, as well as what howtos you've followed. I've got a working DLink USB key (not sure if it's exactly the same, but like yours it uses the ralink driver) and I didn't have to do anything in particular to get it working, so it's difficult to say why yours isn't working without knowing what state it's in now.

Output from these commands might help, along with links to any howtos you've followed.

```
sudo lshw -C network -sanitize > ~/lshwOutput.txt
```

you'll find the file lshwOutput.txt in your home directory. Open it up and paste the contents here.

for the next command, start with the USB key unplugged and run
```

sudo udevadm monitor > ~/udevOutput.txt
```

plug the key in, wait a few seconds (give it 15, to be safe) press CTRL C then, using the GUI, open the file udevOutput.txt (should be in your home directory) and paste the contents here.

---

### Post by snowpine on 2009-08-24
Hi fields2grand, welcome to the forums!

Logging in as root is not recommended in Ubuntu. (In fact, we are not allowed to discuss it on these forums.)

The recommended way to gain root privileges is by using the 'sudo' and 'gksu' commands. You can type 'sudo -i' if you want a root terminal.

Read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

(edit: too slow!!!)

---

### Post by fields2grand on 2009-08-24
Decoherance, thank you for your reply.

I am using the latest Ubuntu install 9.04.

Here are the results of your queries.  Again thank you.

*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: [REMOVED]
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[1251143957.949750] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4 (usb)
KERNEL[1251143957.950114] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0 (usb)
UDEV  [1251143957.951794] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4 (usb)
UDEV  [1251143957.964076] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0 (usb)
KERNEL[1251143958.008104] change   /devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
UDEV  [1251143958.008972] change   /devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0 (power_supply)
KERNEL[1251143958.060338] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/ieee80211/phy2 (ieee80211)
UDEV  [1251143958.061324] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/ieee80211/phy2 (ieee80211)
KERNEL[1251143958.062124] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wmaster1 (net)
KERNEL[1251143958.063980] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan1 (net)
KERNEL[1251143958.066725] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/leds/rt2500usb-phy2:radi (leds)
KERNEL[1251143958.066760] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/usb_endpoint/usbdev1.3_ep81 (usb_endpoint)
KERNEL[1251143958.066788] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/usb_endpoint/usbdev1.3_ep01 (usb_endpoint)
KERNEL[1251143958.066816] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/usb_endpoint/usbdev1.3_ep00 (usb_endpoint)
UDEV  [1251143958.069505] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/usb_endpoint/usbdev1.3_ep81 (usb_endpoint)
UDEV  [1251143958.071603] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/usb_endpoint/usbdev1.3_ep01 (usb_endpoint)
UDEV  [1251143958.073701] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wmaster1 (net)
UDEV  [1251143958.075806] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/usb_endpoint/usbdev1.3_ep00 (usb_endpoint)
UDEV  [1251143958.078876] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/leds/rt2500usb-phy2:radi (leds)
UDEV  [1251143958.085487] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/net/wlan1 (net)
KERNEL[1251143962.005087] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/rfkill/rfkill2 (rfkill)
UDEV  [1251143962.008716] add      /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/rfkill/rfkill2 (rfkill)


What I understand is I have to download ralink drivers ra2500 and install them in some way.  I'm at a loss.  I've installed ndiswrapper and installed the winxp drivers and got the item to work but those drivers won't allow me to use the ralink drivers and put the device in monitor mode.

Edit:  I would also like to mention that the dlink g-122 has the "link" light on.  If that means anything.  I'm pretty sure I've messed up the system enough so I did a fresh install so all the information posted is on a fresh install and with my internal card disabled.  Being a fresh install I can't help but notice the mention of rt2500usb in the text.  I've haven't downloaded these drivers being a fresh install.  I'm not sure what that means.    Thank again.

Edit2:  Wlan1 is the interface id of the dlink usb card.  When I pull up an iwconfig both wlan0 (internal) and wlan1 (dlink) show they are connected to my essid.  when I turn off the internal card and then pull up an iwconfig, neither devices show they are connected to my essid.  For whatever that's worth.

---

### Post by t0p on 2009-08-24
Any particular reason why you installed Ubuntu and not Backtrack?  I don't know which version of Backtrack you were using, but I use Backtrack 4 pre-final (live) and you get an installation script on the desktop.  As you could get monitor mode fine when running Backtrack in a live session, I would assume you'll be able to do the same if you install it.

Backtrack is based on Ubuntu nowadays, but you get all sorts of drivers, extra software etc in your default Backtrack install.  Remember, Backtrack is a specialized security distro whereas Ubuntu is a general use OS.

---

### Post by fields2grand on 2009-08-24
Probly a good call.

---

### Post by decoherence on 2009-08-25
agreed: simplest is to use what works. but i'm curious to know why your d-link adapter doesn't work and mine does. The computer that I use it on is running the development version, so maybe it's a fix there. As far as I'm concerned, you shouldn't have to install extra drivers.... there are ralink drivers are in the kernel now (that's the rt2500usb you saw) and while they were dodgy at first, 9.04 should be ok.

The output from udev tells us that your d-link is indeed getting assigned wlan1. That means the driver is probably not the problem.

Do you know if Backtrack uses NetworkManager, by any chance? If not, I'd say that's the likely culprit. If you want to stick with regular Ubuntu, I suggest you install the wicd package. It will automatically replace NetworkManager.

Or just go with Backtrack.

---

### Post by fields2grand on 2009-09-19
Decoherance.  I took your advice and installed Wicd over the regular network manager and am happy to say that I am now able to put my dwl-g122 device in monitor mode.  It still shows up as wlan1 but that doesn't seem to effect it's performance in any way.  I do an "airmon-ng start wlan1" and pulls it up showing it in monitor mode with the correct ralink drivers.  Thank you for your help.

---

