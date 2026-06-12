---
title: "[SOLVED] How can I load the rt2870 module at startup?"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by KIAaze on 2008-06-15
I have a Medion MD8833 with an RAlink WLAN card and managed to get it working by using the "rt2870" driver from here:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

However, currently, I always have to run:
```
/sbin/insmod rt2870sta.ko
```
from the os/linux directory of the extracted tarball.

Then I have to play around with network manager a bit until it sees all available networks and connect to the one I want.

I tried following the instructions of the Readme file:
> MORE INFORMATION

=================================================================================

If you want for rt2870 driver to auto-load at boot time:

A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.

   

B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      

   edit( or add the line) in /etc/modules.conf:

       alias ra0 rt2870sta

   

C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  

   DEVICE='ra0'

   ONBOOT='yes'     





NOTE:

   if you use dhcp, add this line too .

    BOOTPROTO='dhcp'



*D) To ease the Default Gateway setting, 

    add the line

    GATEWAY=x.x.x.x   

    in /etc/sysconfig/network

=======================================================================


But it still doesn't work at boot. :(

edit:
Ok, the module loads at boot now.
I just had to run "make install" too, which was not indicated in the Readme.

However, I still always have to play around with network manager as follows:
Manual configuration->Unlock
->Wireless connection properties->Uncheck roaming mode, put in something, click Ok.
Wait
->Wireless connection properties->Recheck roaming mode and click Ok
Wait
And then it works.

---

### Post by kevdog on 2008-06-16
Can you post your /etc/network/interfaces file?

---

### Post by KIAaze on 2008-06-16
No, unfortunately I can't since I'm not at my cousin's place anymore. (I was setting up Ubuntu Studio on his PC)

However, I solved the problem using this method:
[http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/](http://icebreaker.wordpress.com/2007/11/03/wireless-ubuntu-710-love/)
The PC is now online after boot. :)

_From what I remember and based on the linked method_, the /etc/network/interfaces file looked like this:
```
iface ra0 inet dhcp
wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-psk <your long wpa key>
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid <your essid>

auto ra0

```
This was after applying the method I linked too of course.
There was no gateway I think and instead of wlan0, it was ra0.

If you know a better solution, please let me know. I'll try it next time I visit him.

I now have mainly three problems left:

[LIST]

[*]The network manager applet is gone, so it's more difficult to change wifi networks if this is ever necessary.

[*]I installed Ubuntu Studio over Ubuntu using the ubuntustudio .debs. This caused the installation of the linux-image-2.6.24-18-rt kernel, with which the rt2870 driver doesn't work anymore. :(
The compilation+installation on the RT kernel works, but the loading with insmod doesn't. I got some error message about an unknown symbol.

[*]Ubuntu Studio doesn't put mounted devices on the desktop anymore... (small problem, but it still bothered me since there is no unmount applet to make up for it).

[/LIST]

So for now, I configured the menu.lst so that it offers Vista and the Ubuntu Studio generic kernel as first choices.
That way he can boot into Ubuntu with a working internet connection, which is essential for a newbie.

---

