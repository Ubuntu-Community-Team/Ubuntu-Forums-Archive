---
title: "[SOLVED] Wireless Card Suddenly Stopped Working -- has it died?"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by chombee on 2007-10-14
The laptop is a Dell Inspiron 510m running Dapper. The wireless card is an Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter, internal.

It was working fine when I setup Ubuntu on the laptop, back in the Breezy days. It has since been upgraded to dapper, and the card was still fine. Then all of a sudden the user brings the laptop to me and tells me the Internet has completely stopped working, and sure enough, it has.

The network monitor applet (not the new nm-applet, the old applet) is looking at the loopback interface, lo, and refuses to look at anything else. In Network settings the wireless card appears and can be activated, deactivated etc., but no networks show up in the list of networks. Even if I enter the network name manually it doesn't connect. I also tried running dhclient from the terminal and got nothing. Strangely enough when I booted a Feisty livecd I got exactly the same problem with the wireless card. Does this sound like the internal wireless card has actually died? Iwconfig gives weird output, all 0's and off's, which seems to suggest to me that the card is dead, but I don't know. I tried various commands to power it back up but got nowhere:
```

eth0 unassociated ESSID:"default" Nickname:"ipw2100"
Mode:Managed Channel=0 Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Power:off
Retry min limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

but I tried various commands to try and power-up the device with no luck:

sudo iwconfig eth0 power on
sudo iwconfig eth0 txpower on
-> SET failed on device eth0; Invalid argument.
sudo iwconfig eth0 txpower auto
-> SET failed on device eth0; Invalid argument.
etc.

```

Nothing seems to get anywhere.

Here are some more outputs:

lshw: [http://pastebin.com/f3ea10d7f](http://pastebin.com/f3ea10d7f)

iwconfig: [http://pastebin.com/f7cb8c0a9](http://pastebin.com/f7cb8c0a9)

sudo dhclient eth0: [http://pastebin.com/f24580559](http://pastebin.com/f24580559)

The laptop was definitely in range of a DHCP wireless network named "default" when I ran that command, because I'm able to connect to the network fine using ra0. ra0 is an external wireless card I've attached in order to make this bug report, it works fine, the problem internal card is apparently eth0.

The card should be compatible, from the looks of this page

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

using the ipw2100 driver, and I notice from the iwconfig output that it seems to be using that driver.

Oh, one more thing. When I first looked at the laptop the linux-restricted-modules package was marked as broken. I used Synaptic to fix it, then to install all the latest updates for dapper, then rebooted, before running the tests in my first post. I noticed that Synaptic installed new versions of linux-restricted-modules and the linux kernel.

Here's the output of dmesg after I booted the laptop and messed around with eth0 and ra0 for a while, doing the tests in my first post:

[http://pastebin.com/f5454db24](http://pastebin.com/f5454db24)

eth0 is the internal card that isn't working. ra0 is an external I've attached that works fine. I don't see eth0 anywhere in dmesg. Weird. Should dmesg print out all info since I booted the laptop?

Any help with this? I've looked through the wireless man files, the linux wireless lan howto, googled, asked on IRC, placed a question on launchpad, but haven't learned anything.

---

### Post by anubhavrocks on 2007-10-14
It seems like  you have switched  OFF the wi fi through the Wi FI OFF/ON key on the keyboard.Try enabling that.

---

### Post by chombee on 2007-10-14
Yep, that was it! :)

Fir the record, it wasn't me that turned it off, but the user I was helping. I didn't realise the laptop had this feature.

---

### Post by anubhavrocks on 2007-10-14
Can you mark the thread as SOLVED so that other's can benefit.

---

