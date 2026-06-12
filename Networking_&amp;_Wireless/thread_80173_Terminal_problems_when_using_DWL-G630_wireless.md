---
title: "Terminal problems when using DWL-G630 wireless"
date: 2005-10-21
forum: Networking &amp; Wireless
---

### Post by bull8042 on 2005-10-21
I am trying to use ndiswrapper with a DWL -G630 ver.a wireless card. I installed the XP drivers, but the card seems to hose my system when I activate it.
Left-clicking the network icon brings up the connection properties window, but the only available choices to view are "eth0" and "lo". If I type in "wlan0", it then shows the signal strength meter, but the other choices go away. If I try to configure the wireless card in "Network Settings", it takes minutes for it to complete it's configuration.
The part that concerns me is that when the card is activated, any keyboard input in a terminal is significantly delayed or doesn't appear. If I deactivate the wireless connection, the terminal behaves properly. In either case, my CPU usage is about 9%.
Hardware: Dell 9100, 3.2Ghz CPU, 1Gb ram
Anyone have any ideas?
Thanks in advance...
Bull

---

### Post by firecat53 on 2005-10-26
I also am having trouble with the Madwifi drivers and DWL-G630. It worked fine under Hoary when I compiled madwifi (not the stock drivers) from source. I think there may be an issue with 2.6.12, but I'm not sure. When I get a chance and there's a 2.6.13 available (is there yet??) I'll try again. I also haven't tried ndiswrapper either. 

Scott

---

### Post by carlosqueso on 2005-10-26
I feel your pain...same crap...let's send an army of penguins to take over d-link's headquarters!

---

### Post by carlosqueso on 2005-10-27
bump for the three of us

---

### Post by carlosqueso on 2005-11-29
I don't know if anyone here is still looking about this...but what chipset does your card have?

---

### Post by firecat53 on 2005-12-01
Sorry guys! I forgot I had posted to this thread!! I've got my DWL-G630 (rev C) working happily with Madwifi and WPA. I used a slightly older version of the drivers from their website. I tried the madwifi-ng, but I think it's still in pretty heavy development and takes some extra steps to get working easily. 
Remove the linux-restricted-modules if you don't need anything else there. Otherwise, you can go in and delete the old modules(ath_pci.ko, ath_hal.ko, wlan.ko, etc) in /lib/modules/2.6.12-x86/madwifi (maybe in a little different spot....sorry I can't remember exactly where it was)

1. Install gcc-3.4 (and other build-essential things if you don't have them already. Lots of threads about compiling stuff). You have to use 3.4 with this kernel and not 4.0. You can add 

```
CC=gcc-3.4
export CC

``` to your ~/.bashrc to make that the default compiler.
2. Download source (requires Subversion installed):
```
svn checkout http://svn.madwifi.org/branches/madwifi-old madwifi-old
```
3. ./configure
4. make
5. sudo make install
6. It's been awhile now, but I think I did a ```
sudo depmod -a
``` before the modprobe ath_pci. You might have to move the modules into /lib/modules/2.6.12-x86/kernel/net/folder structure per the madwifi readme if that doesn't work.
7. sudo modprobe ath_pci
8. Insert card and pray the green light comes on!

Good luck. Let me know if I can help more.

Scott

---

### Post by firecat53 on 2005-12-01
One more important tidbit.....if you have any other PCMCIA cards plugged in, try unplugging them first!! That drove me crazy for a week before I took out my hidden ethernet adapter and it all worked.....<sigh>

Scott

---

