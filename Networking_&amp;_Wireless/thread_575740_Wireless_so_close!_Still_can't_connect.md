---
title: "Wireless so close! Still can't connect"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by wildzer0 on 2007-10-14
I've been struggling the last couple of days getting a new laptop connected to a wireless network, and I've gotten pretty close. I can see the wireless networks in the default, but I can't connect. The network is using a shared ascii wep key, but when I try to connect it just stalls (I can connect from a windows laptop). 

Some more information that may be relevant: It's a gateway ML6720 laptop using the win98 8187b + ndiswrapper drivers. The wireless device appears to be functioning correctly, I'm not sure if my /etc/network/interfaces file is correct. It says the following:

auto lo
iface lo inet loopback

If anyone needs any more information to help diagnose the problem, just let me know.

---

### Post by kevdog on 2007-10-14
Just for debugging purposes try connecting manually to your network from the command line.  The instructions can be found in a post listed directly below in my signature. If something doesnt work, you will at least be provided some debugging statement on the command line that may help solve the problem.

---

### Post by wildzer0 on 2007-10-14
I followed your guide, trying both the normal way and the way with adding the additional character. No dice either way, and no error messages (just the "No DHCPOffers recieved" message for dhclient command.

By the way, I appreciate all the work you put into this forum! The last couple of days I've read about a million of your posts which have gotten me this far.

---

### Post by kevdog on 2007-10-14
What kind of signal strength and noise level are you getting in iwlist scan??  lshw -C network confirms you are using ndiswrapper as the driver?? What version of ndiswrapper are you using?

---

### Post by wildzer0 on 2007-10-14
What kind of signal strength and noise level are you getting in iwlist scan?? lshw -C network confirms you are using ndiswrapper as the driver?? What version of ndiswrapper are you using?

iwlist scan gets Quality: 65/100 Signal level: -54 dBm Noise level: -96 dBm

lshw -C network says that the drive is ndiswrapper+net8187b and ndiswrapper -v gets me:

utils version: '1.9', utils version needed by module '1.9'
module details:
filename: /lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version: 1.45
vermagic: 2.6.22-14-generic SMP mod_unload 586

---

### Post by wildzer0 on 2007-10-14
Don't mean to be impatient, but I have a big project due tomorrow and I need internet! Any additional advice would be extremely appreciated. It seems like everything is set up perfectly, and I can't find anything that gives me error messages - so this thing is totally baffling me.

---

### Post by kevdog on 2007-10-14
Look there is one other thing we could try, however I dont know why your setup isnt working. 

Two options
#1. Try the winxp drivers
#2. Use the native linux driver.

---

### Post by wildzer0 on 2007-10-14
I tried the winxp drivers, no go. I can't see the wireless network at all when I use that one. I couldn't find anything about native drivers, I see realtek makes a few linux drivers for other models, but not this one.  I don't know if it matters or not, but if I tail /var/log/messages while trying to connect, I get the following: 

Oct 14 19:41:52 ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Oct 14 19:42:01 ubuntu kernel: [  118.132000] NET: Registered protocol family 17
Oct 14 19:42:48 ubuntu dhcdbd: Unrequested down ?:3

---

### Post by kevdog on 2007-10-14
Use native drivers:

1. Edit blacklist file
gksu gedit /etc/modprobe.d/blacklist

Add the following:
blacklist ndiswrapper

Modify the following lines to:
#blacklist r8187
#blacklist r818x

2. Edit the /etc/modules file
Modify the following line to:
#ndiswrapper

3. Remove/Add the appropriate kernel modules
sudo rmmod ndiswrapper
sudo modprobe r8187
sudo modprobe r818x

4. Check lshw -C network to see if your device is now registered with the rtl8187 driver

5. Bring up the interface
sudo ifconfig <interface_name> up

6. See the link in my signture about connecting at the command line -- look for the section relating to the r8187 drivers

Let me know what happens.

---

### Post by wildzer0 on 2007-10-14
Uh oh, I probably should have mentioned this in the beginning but didn't think to. I'm using the Gutsy RC because feisty does not have drivers for the ML6720's video chipset so I couldn't get use x server. Gutsy does not seem to have these native drivers included.

---

### Post by kevdog on 2007-10-14
Hmm,

sudo updatedb
locate r8187

Does anything come up??

---

### Post by wildzer0 on 2007-10-15
locate r8187 returns nothing. I guess it's not included in Gutsy because of the bug, which is a shame because I read your post about how easy it is to work around.

---

### Post by wildzer0 on 2007-10-15
Bumpy bump. Hoping someone out there has an answer for this. I'd rather deal without internet than vista, but internet would be really really nice.

---

