---
title: "Troubles getting the WG111 working"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by stenci on 2007-02-18
I'm a newbie, I just installed Ubuntu from a CD, and I don't have the network access yet.
I found [here ]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111")the step-by-step description, but I keep failing.
Here some questions (no internet yet, so I'm posting from another computer, so I can't copy&paste, so I will shorten some outputs):

1) [Here ]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")it says: > test for plug and play using iwconfig to determine if you need ndiswrapper"
iwconfig returns:
> [FONT="Courier New"]eth2   IEEE 802.11b  ESSID: off/any
         Mode:Auto  Channel=1  Access Point:Invalid
         Sensitivity=0/200
         Link Quality:0  Signal level:0 ....[/FONT]
only if the device is connected to the USB port, this part is missing if I unplug it.
So I'm assuming the result of this test is: no, I don't need ndiswrapper.

2) So I skipped the part related to ndiswrapper. Then it says:
> Assuming your wireless network runs in managed mode and you need only an ESSID (no WPA or WEP), add the the following to /etc/network/interfaces 

auto wlan0
iface wlan0 inet dhcp
        hostname <hostname>
        wireless_mode managed
        wireless-essid <essid>
I have no idea what "managed", "ESSID", "WPA", "WEP" and "hostname" mean, so I got stuck.

3) Looking at other examples/ports I found something different, I guessed that ESSID is the name of my wireless network (the text that I see in Windows when I refresh the network list) and I added this:
[FONT="Courier New"]> auto wlan0
iface wlan0 inet dhcp
        wireless-essid <NetworkName>
        wireless-key <NetworkPassword>[/FONT]But it kept failing.

4) Then I tried to install ndiswrapper (downloading the file on this computer, burning a CD, copying on the Ubuntu computer), but it didn't work because I get a bunch of error because something is missing. It looks like I miss the standard headers for the compiler (stdio.h, etc.).
Do I need ndiswrapper and the C files, and do I need to download them on this computer and copy them on the other?

Thanks,
Stefano

---

### Post by phossal on 2007-03-11
Use ndiswrapper. ;)

---

