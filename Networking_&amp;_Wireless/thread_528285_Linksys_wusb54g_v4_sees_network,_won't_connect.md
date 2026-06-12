---
title: "Linksys wusb54g v4 sees network, won't connect"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2007-08-17
I am using the Linksys WUSB54G v4 wireless adapter with Ubuntu Feisty Fawn. It picks up the wireless network in my apartment, but it has a weak signal strength (usually 60% or less).

When I go into System -> Administration -> Network -> Properties, I have the option either to enable wired networking (after which the "two glowing balls" icon appears) or disable it (after which I just get the "four blue bars" icon in the system tray). If I enable wired networking, the two glowing balls keep circling, never connecting to my wireless network. If I disable wired networking, I get a few blue bars, but it's still not connected.

I use the commans "sudo iwconfig rausb0" to find my wireless network, then "sudo dhclient rausb0" to try and connect to the wireless network. I used to be able to connect to my wireless network when my signal strength was above 60%. Now, I just get "no working leases persistent databases sleeping" after entering "sudo dhclient rausb0."

Where do I begin to fix this problem? School is starting soon...

---

### Post by Sp4cedOut on 2007-08-17
in System > Administration > Network in the properties tab, doesn't it list the wireless connection, with a check box?  I remember having to mess around with the settings quite a bit to get my wusb54g to work.  In the properties for the wireless connection, be sure the box to enable roaming mode is unchecked.

---

### Post by xjgnsdof on 2007-08-17
I'll try that. What do I select for "password type" (hexadecimal or ascii) and the other settings?

---

### Post by punkrokk on 2007-08-17
wep or wpa?

---

### Post by xjgnsdof on 2007-08-17
The security type is WPA-PSK. "DNS Servers" and "Search Domains" are both blank.

On a side note, when I input "sudo dhclient rausb0," the IP address 255.255.255.255 keeps coming up in the resultant output.

---

### Post by xjgnsdof on 2007-08-18
I have moved the laptop a few feet away from the wireless router, and I still can't get a strong enough signal (over 60% connectivity).

If the wireless router's IP address is 192.168.1.1 by default, and dhcp client sends on 255.255.255.255, is that the problem?

---

### Post by xjgnsdof on 2007-08-18
None of you knows how to fix this problem, so I'm buying an ethernet cable.

---

### Post by wieman01 on 2007-08-19
> **elgilicious said:**
> None of you knows how to fix this problem, so I'm buying an ethernet cable.
I have got a WUSB54G V4 as well. See the sticky for it... The problem is that this card uses a Ralink chipset and hence does not work the way other cards do. That is again because the driver (Serialmonkey) has a design slightly different from that of other drivers.

If you want to work around this problem, install "ndiswrapper" and use the Windows driver to get it working. That's what I did and I am fairly happy with it now. Replace the Linux driver. See the Sticky for more.

_**EDIT:**_
Here is the link:

[http://ubuntuforums.org/showthread.php?t=192588]("http://ubuntuforums.org/showthread.php?t=192588")

---

### Post by xjgnsdof on 2007-08-19
After inputting sudo make install in the extracted ndiswrapper folder, I get this:

```
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.200-16-generic/kernel/ubuntu/misc/ndiswrapper/bin/rm: cannot remove /lib/modules/2.6.200-16-generic/kernel/ubuntu/misc/ndiswrapper/': Is a directory
make:  *** [uninstall] Error 1'
```

What's going on?

---

### Post by xjgnsdof on 2007-08-19
Screw this. I'll save time and maintain peace of mind by buying a long ethernet cable and running it along the floor. I never move this laptop from its place, and it doesn't even have USB 2.0 inputs (only USB 1.1). This thread can be closed; nothing helped anyway.

---

### Post by wieman01 on 2007-08-20
> **elgilicious said:**
> Screw this. I'll save time and maintain peace of mind by buying a long ethernet cable and running it along the floor. I never move this laptop from its place, and it doesn't even have USB 2.0 inputs (only USB 1.1). This thread can be closed; nothing helped anyway.
I really think you ought to try a little harder. Perhaps the HOWTO I have given you wasn't the right one for you, but "ndiswrapper" is no rocket science. 

There is another one for "Broadcom" based cards:

[http://ubuntuforums.org/showthread.php?t=475963]("http://ubuntuforums.org/showthread.php?t=475963")

You don't have to compile "ndiswrapper" from scratch, it is in the repositories. So why don't you install it using Synaptics/Adept and continue from "Step 3" as described in the sticky thread?

I can help if you have troubles... I should be around.

---

