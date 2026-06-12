---
title: "Unable to detect my wireless network"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by dhar23 on 2008-12-22
I'm am the newest of newbies to Ubuntu. I'm running 8.04 and cannot get online via my wireless interface for the life of me. It appears that Ubuntu recognizes my network card, and I've gone over the System - Preferences -  "Network Settings" and "Wireless Network" options. I feel like I've got the correct info entered in those, but I still can't detect my wireless network. 

Until I can get online w/ any regularity, I can't really dig in to the basics of using apps like the "Terminal" window. If someone could please help me w/ this wireless issue, i'd really appreciate it.

---

### Post by RomeReactor on 2008-12-22
Hi. Make sure the router doesn't have any encryption (or if it does have encryption, that you have set up the correct key and network name in your wireless configuration in Ubuntu); to make things easier also make sure the router set to broadcast the SSID (network name).

---

### Post by dhar23 on 2008-12-22
I've had no trouble w/ my old XP machine detecting the wireless network I'm trying to access. Also, this is my company's wireless network, and I know their intention is for anyone nearby to be able to access it. 

I hate sounding so helpless in this situation, but can you maybe point out where in Ubuntu (System - Preferences - ???) I'd go if I was connecting to a wireless network for the first time? I've been through the "Help" features a few times w/ no success. Also, this machine was previously connected to a wired network. Could that old configuration interfere w/ me trying to find a wireless network? 

Thanks for the help.

---

### Post by RomeReactor on 2008-12-22
> **dhar23 said:**
> I've had no trouble w/ my old XP machine detecting the wireless network I'm trying to access. Also, this is my company's wireless network, and I know their intention is for anyone nearby to be able to access it.
So that probably means it's an unencrypted connection. Try right-clicking in Network Manager (the icon next to the volume applet in the top panel) to manage the wireless connection.
 
You can try this from the terminal (Application->Accessories->Terminal):

```
cat /etc/network/interfaces
```
Look for your wireless card's designation there: it could be wlan0, eth1, ath0. Normally eth0 is the ethernet port. Once you know your wireless card's designation, run this:
```
iwlist CARD scan
```
just replace CARD with your wireless card, for example:
```
iwlist wlan0 scan
```
and post the output.

> Also, this machine was previously connected to a wired network. Could that old configuration interfere w/ me trying to find a wireless network?
I don't think that should be a problem.

---

### Post by dhar23 on 2008-12-22
Thanks for your reply. here's what I get in the Terminal window when i run "cat /etc/network/interfaces" - 

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#     script grep
#     map eth0

# The primary network interface (conrtrolled by NetworkManager)
# auto eth0
#iface eth0 inet dhcp

iface eth0 inet dhcp


I'm not sure how to run the second command you suggested "iwlist CARD scan", because I'm not sure what you meant when you typed 

"just replace CARD with your wireless card, for example:".

How do I find that? Also, assuming I accomplish that, how and
where do i post the output? 

i appreciate your patience. this computer was given to me yesterday preloaded and w/ no tech info. Thanks.

---

### Post by james_xxx on 2008-12-22
You might try opening a terminal and entering:

```
iwconfig
```

That should list the available wireless adapters. What you are looking for will be the listing that seems to have the most information following it. The ID may be something like 'wlan0' or 'wlan1', etc. (There are instances where wireless winds up being listed as a wired connection, using 'eth1', instead. This may be the case if your adapter has a Broadcom chipset. In that case it will only show up upon entering 'ifconfig', instead of 'iwconfig'.)

To scan for networks from the command line, enter the command that was already suggested, but you need to add 'sudo' to the beginning.

```
sudo ifconfig <ID for your card> up && sudo iwlist <ID for your card> scan
```

Additionally, you can run 'lspci' in a terminal to list all of your PCI devices. Somewhere on the list returned by that command, you will likely find your wireless adapter, and discover what chipset it is using. (Use 'lsusb', if you are using a USB adapter.)

---

### Post by RomeReactor on 2008-12-22
It looks like your wireless card is not being detected; otherwise, you should have seen **wlan0** or some other interface besides **eth0**, which appears to be your ethernet port, among the results.

Is this a laptop or a desktop computer? Is the wireless card inside the machine, or connected via USB? Please run these commands:
```
lspci -nn
```
and:
```
lsusb
```
and post the output of both. To post them, press the number sign (#) in the message box buttons and please paste the results in between the CODE tags.

---

### Post by dhar23 on 2008-12-22
I have a laptop w/ an internal card.

When I run "sudo iwconfig" I get- 

IEEE 802.llabgn  ESSID ""
Mode: Managed Frequency: 2.412 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry m,in limit: 7  RTS thr: off  Fragment thr= 2352 B
Ectryption: off
Power Management: off
Link Quality:0  Signal level:0  Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

When I run "lspci -nn", it shows that I have an Intel 82801I Mobile PCI bridge. 

Also, I'm in Admin mode, but it seems I'm locked out of doing anything in the KDE Control Center under the Network Interfaces tab. Don't know why that is.

I'm unable to launch "Wireless Assistant". The error message states that there's an unknown encoding of a file there. 

I've got roaming enabled in my Network Settings. 

I have "autodetect" enabled in KDE.

In "Network Tools" my network device is listed as a Loopback interface. If i try switching it to Wireless interface, it will revert to Loopback when I reopen the window.

---

### Post by james_xxx on 2008-12-22
You stated that upon entering 'iwconfig' you got this result: 

> IEEE 802.llabgn ESSID ""
Mode: Managed Frequency: 2.412 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry m,in limit: 7 RTS thr: off Fragment thr= 2352 B
Ectryption: off
Power Management: off
Link Quality:0 Signal level:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Note: You do not need to use 'sudo' with 'iwconfig'.

Next to this information you posted (to the left) there was an ID listed for that card. That is what you are looking for. Let us know what that ID is.

---

### Post by dhar23 on 2008-12-22
"wlan0" was listed to the left of that.

---

### Post by james_xxx on 2008-12-22
OK, ignoring all of the GUI tools for wireless at the moment, what do you see when you enter:

```
sudo ifconfig wlan0 up && sudo iwlist wlan0 scan
```

Hopefully you will see any available wireless networks listed.

What kind of encryption are you using? (Sorry if you have already stated this.)

---

