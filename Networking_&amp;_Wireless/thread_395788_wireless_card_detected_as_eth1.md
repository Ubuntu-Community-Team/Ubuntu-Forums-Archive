---
title: "wireless card detected as eth1?"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by khughitt on 2007-03-28
Hi,

I have an Intel 3945ABG in my laptop, and it works fine (now), however, NetworkManager does not detect any wireless cards, and only can see my ethernet card. When i run **iwconfig**
i get:

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"wireless"  Nickname:"wireless"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:40:96:44:81:DE   
          Bit Rate:2 Mb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/100  Signal level=-91 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5356   Missed beacon:0


```

I'm guessing that this is the reason why NetworkManager does not work properly. Does anyone have any ideas on how to get ubuntu to properly detect the network card?

Any help would be much appreciated,
Also sorry if this topic has come up before-- i tried searching for a solution but did not have any luck..

Thanks,

---

### Post by rjl5020 on 2007-03-28
Edit /etc/network/interfaces and comment out all lines pertaining to eth1 in it.

for example, if it says:

iface eth1
wireless-ssid wireless
auto eth1

comment all of those lines out by putting a # before the line. Reboot, and you should be okay.

---

### Post by YourDoom123 on 2007-03-28
yea, i have the same wireless card as you, and i've had the same problem. basically, the issue is that network manager downright sucks. so I wrote a script to connect properly for me. I'll post it here when i get home.

EDIT: oh, and make sure you do what rjl said... my script is useless otherwise.

---

### Post by Saicho on 2007-03-28
I can't wait for this script, I'm having the same problem =)

---

### Post by dbott67 on 2007-03-28
I had a similar problem when I installed Edgy.  In Dapper, my wifi (using ndiswrapper) was wlan0, but in Edgy it was eth1.

What I noticed was that my iftab file had a couple of entries similar to the following:
```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:xx arp 1
eth1 mac 00:16:ce:31:88:xx arp 1

```

If memory serves me, I just edited the iftab:
```
sudo gedit /etc/iftab
```
and changed** [COLOR=Red]eth1[/COLOR]** to [B][COLOR=Red]wlan0:
[/COLOR][/B]```
dbott@edgy:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:15:c5:0c:ad:xx arp 1
[COLOR=Red]wlan0 [/COLOR]mac 00:16:ce:31:88:xx arp 1

```

Can you post the output of your iftab file?

-Dave

---

### Post by Saicho on 2007-03-29
> **YourDoom123 said:**
> yea, i have the same wireless card as you, and i've had the same problem. basically, the issue is that network manager downright sucks. so I wrote a script to connect properly for me. I'll post it here when i get home.

EDIT: oh, and make sure you do what rjl said... my script is useless otherwise.

do you mind posting your script? I'm still having the problem :confused:

---

### Post by khughitt on 2007-03-29
cool! got it fixed- i did dbott67 suggested and edited the iftab file, changing the eth1 to wlan0 (to make sure i was changing the wireless and not the ethernet card, i went to system--> administration --> device manager, and found the mac address of the wireless card.

after rebooting NetworkManger worked perfectly!

Thanks for the advice guys :)

---

### Post by YourDoom123 on 2007-03-29
Alright, here it is, and sorry for making you guys wait so long.

```

#!/bin/bash
ifconfig eth1 down
iwconfig eth1 essid $1
ifconfig eth1 up
dhclient3 eth1

```

to use it, do the following:
```

sudo touch /usr/bin/fixWifi
sudo chmod +x /usr/bin/fixWifi
sudo gedit /usr/bin/fixWifi #paste in the above script, save, exit
sudo fixWifi <essid> #network name, etc. if you leave it blank, it connects to the nearest, strongest signal

```

---

