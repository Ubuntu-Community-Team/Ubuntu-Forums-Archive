---
title: "I haven't the slightest what I'm doing..."
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by band-aid on 2006-12-30
I got a new laptop for christmas and have been happily enjoying it thus far. Today I finally got sick of the windows install that came on it and a short time later had edgy installed. I have been using ubuntu on my desktop for several months and everything is working great on it. I was trying to get my wireless connection set up when I realized that I haven't the slightest bit of knowledge when it comes to associating with a wireless network in linux. My wireless card is listed as eth0.

iwconfig

eth1

unassociated ESSID: "<my essid>"
Mode:Managed   Frequency=2.437 GHz   Access Point: Not-Associated
Bit Rate:0 kb/s   Tx-Power:16 dBm
REtry limit:15   RTS thr:off   Fragment thr:off
Power Management:off
Link Quality:0   Signal level:0   Noise level:0
Rx invalid nwid:0   Rx invalid crypt:241   Rx invalid frag:0
Tx excessive retries:0   Invalid misc:86   Missed beacon:0

Thanks for the help
Band-aid

---

### Post by bernied on 2006-12-30
Have you tried network manager - when it works it's superb. Look for it in your package manager.

---

### Post by band-aid on 2006-12-30
unless it came on the CD I am unable to access it on that computer.

I think my problem is deeper than I once thought. I have spend the past two hours trying to get ndiswrapper to work correctly with my ipw3945.

---

### Post by bernied on 2006-12-30
You do not need ndiswrapper - the output from iwconfig tells us that you already have access to your device. You just need to associate with your ESSID. Wait a sec, getting manual...

---

### Post by bernied on 2006-12-30
Manual page for iwconfig [here](http://www.die.net/doc/linux/man/man8/iwconfig.8.html).

So something like:
```
iwconfig eth1 essid <your essid>
ifconfig eth1 up
```
might just do it.

Then try network manager from the repositories

---

### Post by band-aid on 2006-12-30
no go on that. I think I may need to unblacklist the default driver that the ndiswrapper installation guide told me to blacklist.

OK I got the driver unblacklisted

---

### Post by nicknn on 2006-12-30
> **band-aid said:**
> no go on that. I think I may need to unblacklist the default driver that the ndiswrapper installation guide told me to blacklist.

OK I got the driver unblacklisted

Hi,
try this guide to network manager. I used it to get my ipw3945 on my dell working with edgy
[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
if you cant find the required packages, set up your repositries as described in
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by Silentvoice on 2006-12-31
No don't do that! "ifconfig <device name> up" merely brings up the device, it won't send any DHCP requests to the access point.

the first command is correct

sudo iwconfig <device name> essid <SSID>

but then what you want to do is 

dhclient


this associates the essid, and then sends a DHCP request to the DHCP server.

---

### Post by band-aid on 2006-12-31
dhclient fails to get a address from the router. I am not able to ping the router either.

---

### Post by doviende on 2006-12-31
i have the same card and i do the following to connect:

1) sudo iwlist eth1 scanning    (this tells me the settings i need for my AP)
2) sudo iwconfig eth1 essid mysid channel 6    (this sets the sid and the frequency for my network.  your channel might be something else)
3) sudo ifup eth1    (this tells it to bring up the interface using the method in /etc/network/interfaces, which is where it says to use dhcp)

the other way i've done it is by using the gnome network manager (aka "nm-applet").  You can just right-click it and choose connect to new wireless network.

I never used any ndiswrapper stuff.  just straight ipw3945 driver.

---

### Post by band-aid on 2006-12-31
I followed the above steps but it was unable to get an IP address from the router. I am going to try again tomorrow after a fresh install to get rid of the possibility that I borked something messing with ndiswrapper.

About the driver that you mentioned. Did you have to install that one separately or does it come preinstalled...

---

### Post by doviende on 2006-12-31
the ipw3945 driver comes preinstalled on edgy.  One more thing to watch out for:  if you have a wireless on/off switch, make sure the wireless card is on when you boot, otherwise the system won't be able to insert the firmware and your wireless won't work.  Once the card has been properly set up once, you can then turn it on and off with the physical switch successfully.

---

