---
title: "ifup ignores encryption settings"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by mbratch on 2008-10-03
Hi --

I have Ubuntu 8.04 and a wireless USB device based upon RTL8187B.

I got this set up to work fairly smoothly using ndiswrapper except one key point: ifup, during initialization of the system, ignores the encryption settings in /etc/network/interfaces. I can't for the life of me figure out why.

So I currently have to boot my system up and bring up both the wired network, and the wireless network. The networking in general is happy (due to the wired working), and I can manually use iwconfig to set the encryption on the wireless. Then I can ifdown the wired net, and the wireless network works.

If I disconnect the wired network, bring up the system with just the wirless, none of the networking is enabled due to the encryption not being set by ifup using the /etc/network/interfaces settings. If I then manually set encryption with iwconfig, it makes the settings but networking isn't operational due to some other dependencies (there are probably other services that need restarting?).

I tried setting up an init script that would call iwconfig to set encryption during start-up. Tried it in various places (after boot-up was practically done, in rc.local; also tried a script right after the networking script runs). None of this worked. It always came up with encryption off. So it ignored my iwconfig settings or reset them during initialization (?).

My settings in /etc/network/interfaces looks like this (x's have my actual data):

```

iface wlan0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway xxx.xxx.xxx.xxx
wireless-key xxxx-xxxx-xx open
wireless-essid xxxxxx

auto wlan0

```

I can't figure this out. Any ideas?? The GUI wireless setup didn't put encryption type in the interfaces file. Is it implied? And I had to manually add the 'open' part. Weird. The tool seems to do a partial job (?).

Thanks.

---

### Post by mbratch on 2008-10-03
Ooompah

---

### Post by mbratch on 2008-10-12
Well, I finally got this *almost* working. To get it to work at all, I had to put a script in /etc/network/if-pre-up.d that looks like this:

/sbin/iwconfig wlan0 essid <My_Access_Point>
/sbin/iwconfig wlan0 key <My_WEP_Code> open
/sbin/iwconfig wlan0 channel <My_Channel>
/sbin/iwconfig wlan0 mode Managed

The system still ignores settings in the "interfaces" file, but seems to do the scripts under /etc/network OK.

But now the oddest thing is happening. Although I have the eth0 (wired lan) set up for manual configuration (not auto-loading), it must be plugged in or the computer won't boot with networking working.

In other words, if I reboot the PC, wireless networking will not work at all if the wired network cable isn't connected. iwconfig, ifconfig, and iwlist all show output that looks normal. But I can't ping anything on the network, nor the access point/router itself. If I just connect up the network cable and reboot, the wireless comes up on its own and all works fine (and the output of these tools looks the same as in the non-working case). And like I said, the wired network isn't ON in this case, the cable just has to be connected for the wireless to come up. Once up, I can disconnect the cable and the wireless works fine until the next reboot.

Can someone give me a hint as to what the heck is going on?

Thanks.
:confused:

---

### Post by mbratch on 2008-10-15
Wow. Seems nobody here really understands how this networking stuff works in Ubuntu, eh?

---

