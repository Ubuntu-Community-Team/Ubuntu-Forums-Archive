---
title: "Wireless PCI 64 bit Driver - Ndiswrapper expert needed"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by SebMKd on 2008-02-15
Here is my set up:
AMD64 Gusty - Wireless Card Rosewill RNX-G300E
[FONT="Courier New"]lspci:
Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
lspci -n:
11ab:1faa (rev 03)[/FONT]

I installed Ndiswrapper 1.50. Then installed a set of driver (mrv8335.inf) that I had used for this PCI Wifi card on another Gusty set-up and which worked flawlessly. However, the other set up was 32 bits. Therefore, when looking into dmesg I saw an error.

Looked for 64 bits XP drivers and found a set in Rosewill CD: Netmw126.inf

I uninstalled mrv8335.inf and installed the new one:
[FONT="Courier New"]sudo ndiswrapper -i netmw126.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo ndiswrapper -l
netmw126 : driver installed
device (11AB:1FAA) present[/FONT]

However, I still don't see Wlan0 interface!! Even after a restart. :confused:

What did I do wrong? What else can I try?

---

### Post by SebMKd on 2008-02-21
Well, without other alternative I've been trying to fix the problem myself.
In the end after multiple attempts I finally got what I wanted: ndiswrapper showed on dmesg and I got a Wlan0 interface working. Don't ask me exactly how I got here though !

However, here is my new issue: Ndiswrapper doesn't load at each boot!
I've tried adding "ndiswrapper" at the end of the module file with 'sudo gedit /etc/modules'.
It works once, but not twice!

What can I do?
Any Ndiswrapper experts around?????

Thanks

---

### Post by Uppsala9496 on 2008-03-20
Any details on how you got this working?
I have Gutsy 64bit going and can't get this wireless card working.  I've tried everything.

iwconfig shows:
lo        no wireless extensions.

eth0      no wireless extensions.

Device manager shows my card.

---

### Post by SebMKd on 2008-03-21
This WiFi card has been so easy to install on Ubuntu 32 bits that I thought it would be the same on 64Bits.
I still have one issue with entering my password at every re-start, however, it works now just fine.

Here is what I did:

STEP 1: CLEAN SYSTEM

- Get rid of old drivers (replace "[COLOR="Blue"]OLDDRIVER[/COLOR]" by the driver name):
[FONT="Courier New"]sudo modprobe –r ndiswrapper
sudo rmmod ndiswrapper
sudo ndiswrapper -e [COLOR="Blue"]OLDDRIVER[/COLOR][/FONT] (or –r [COLOR="Blue"]OLDDRIVER[/COLOR])

- Disactivate restricted drivers:
System -> Administration -> Restricted Drivers Manager

- Remove old ndiswrapper:
[FONT="Courier New"]sudo apt-get remove ndiswrapper-utils
sudo rm –r /etc/ndiswrapper/
sudo rm –r /etc/modprobe.d/ndiswrapper[/FONT]

- back list BCM43xx driver:
[FONT="Courier New"]sudo -s[/FONT]
[FONT="Courier New"]echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist[/FONT]
[FONT="Courier New"]exit[/FONT]

STEP 2: GET NEW PACKAGES
(Not necessary I think. But I've done it anyway)

[FONT="Courier New"]sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build[/FONT]

STEP 3: INSTALL LATEST NDISWRAPPER
(Eventually, it would be better to look in Synaptic, make sure you get the latest. I've got the one below and since then did regular updates)

[FONT="Courier New"]sudo apt-get install ndiswrapper-utils-1.9[/FONT]

[COLOR="Red"]REBOOT NOW[/COLOR]

STEP 4: INSTALL DRIVERS
(netmw126.inf driver, on Rosewill CD or website, for WinXP64 works for me. Copy all files - sys, inf, ...- to your temp driver directory)

[FONT="Courier New"]cd [COLOR="Blue"]YOUR-DRIVER-DIRECTORY[/COLOR]
sudo ndiswrapper -i netmw126.inf
sudo ndiswrapper -l[/FONT]

=> You should see a message that says driver present, hardware detected.

[FONT="Courier New"]sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper –m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant[/FONT]

[COLOR="Red"]REBOOT NOW[/COLOR]

Test with '[FONT="Courier New"]dmesg[/FONT]' which shows Ndiswrapper and Wlan0. '[FONT="Courier New"]lsmod[/FONT]' also shows Ndiswrapper. Otherwise redo '[FONT="Courier New"]modprobe ndiswrapper[/FONT]'.

This worked for me. However, I have to enter my password every time, because I have the following error: [FONT="Courier New"]nm-applet needs access to default keyring, but it is locked[/FONT].
This [[COLOR="Blue"]_thread_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1") seems to offer the right solution. However, for some reason, my passwords are not compatible and I can't even log-in X if I follow this method. I'm still looking for a solution to fix this little inconvenience.

Good luck. And let me know how it goes.

---

### Post by CypherSystem on 2008-06-05
How exactly do you do this in 32bit??

I have the same card and it would be Very Helpful

---

### Post by CypherSystem on 2008-06-05
Never Mind, Thanks Much, I was able to figure it out :) Thanks Again!!!!

---

