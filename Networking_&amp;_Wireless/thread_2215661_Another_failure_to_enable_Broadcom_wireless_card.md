---
title: "Another failure to enable Broadcom wireless card"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by john184 on 2014-04-07
Hi,

I'm new to Ubuntu, spent all day trying to get this working, now I think I could use some help, please.
I have a Dell Latitude D600, dual-booting XP and Xubuntu 12.04. I discovered it's got a Broadcom BCM4309 wireless card [14e4:4324] (rev03).

I started tying to use Settings > Additional Drivers, but this crashed my machine with a Kernel BUG at include/net/cfg802.11.h:2209! invalid opcode:0000 [#1]smp
Next I went to the documentation and found instructions to install first the b43 driver and then separately the b43 legacy driver (my card was listed for both). I configured the network settings. But no joy.
Next I found documentation with instructions for a ndiswrapper install. I blacklisted the previous drivers, then downloaded a new one from Dell, installed and loaded using ndisgtk. Still no joy.
Then I found the sticky at the top of this forum, uninstalled what I had inc. a purge of the bcmwl-kernel-source, reverted the blacklisting and installed linux-firmware-nonfree. Still no joy.
I've eliminated the issue some users of this laptop had with trouble discovering the Fn F2 key turns the wifi on and off.

I hope I'm not being stupid.
thanks for any help.
John

---

### Post by chili555 on 2014-04-07
Pretty handy sticky, eh??

Let's see where you are so far. Please run and post:```
lsmod | grep -e b43 -e wl -e ndis
dmesg | grep b43
```Thanks.

---

### Post by john184 on 2014-04-07
Hi Chili, thanks for taking the bait.

john@john-Latitude-D600:~$ lsmod | grep -e b43 -e wl -e ndis
ndiswrapper           192304  0 
john@john-Latitude-D600:~$ dmesg | grep b43
john@john-Latitude-D600:~$

---

### Post by chili555 on 2014-04-07
Please do:```
sudo apt-get purge ndiswrapper*
```Now we check for other blacklists:```
ls /etc/modprobe.d
```If you find any ndiswrapper or ndiswrapper.conf, remove it:```
sudo rm /etc/modprobe.d/ndis_whatever_you_found
```Now do:```
gksudo gedit  /etc/modprobe.d/blacklist.conf
```Is b43 or ssb listed in there? If so, remove it. Proofread, save and close gedit. Now do:```
sudo modprobe b43
```Is your wireless working now?

---

### Post by john184 on 2014-04-07
john@john-Latitude-D600:~$ sudo -get purge ndiswrapper*
sudo: unknown group: et
sudo: unable to initialise policy plug-in
john@john-Latitude-D600:~$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         dkms.conf
blacklist.conf           blacklist-oss.conf           ndiswrapper.conf
blacklist-firewire.conf  blacklist-rare-network.conf  vmwgfx-fbdev.conf
john@john-Latitude-D600:~$ sudo rm /etc/modprobe.d/ndis_ndiswrapper.conf
[sudo] password for john: 
rm: cannot remove `/etc/modprobe.d/ndis_ndiswrapper.conf': No such file or directory
john@john-Latitude-D600:~$

---

### Post by ajgreeny on 2014-04-07
Not **sudo -get purge ndiswrapper*** but **sudo [COLOR=#ff0000]apt[/COLOR]-get purge ndiswrapper***.  You missed the **apt** from command.

---

### Post by chili555 on 2014-04-07
> john@john-Latitude-D600:~$ sudo -get purge ndiswrapper*
sudo: unknown group: et
sudo: unable to initialise policy plug-inI actually said:> sudo [COLOR="#FF0000"]apt[/COLOR]-get purge ndiswrapper*Also:> john@john-Latitude-D600:~$ ls /etc/modprobe.d
alsa-base.conf blacklist-framebuffer.conf blacklist-watchdog.conf
blacklist-ath_pci.conf blacklist-modem.conf dkms.conf
blacklist.conf blacklist-oss.conf [COLOR="#FF0000"]ndiswrapper.conf[/COLOR]
blacklist-firewire.conf blacklist-rare-network.conf vmwgfx-fbdev.confSo what you needed to remove is exactly that:```
sudo rm /etc/modprobe.d/ndiswrapper.conf
```When you get errors, unknowns and not-founds, that is often an indication that a typo was made and you should retrace your steps.

It is not, however, completely impossible that *I* made the typo!

---

### Post by john184 on 2014-04-07
sorry about that. too much speed, concentrating now.

purge ndiswrapper - done,uninstall completed, including fakeroot dkms
remove ndiswrapper.conf - done
blacklist.conf - only mention is "# replaced by b43 and ssb. blacklist bcm43xx", so I've left that.
sudo modprobe b43 - done
no sign of wifi. I'm not missing something stupid am I - the wireless network settings are in place, so I'm expecting something like a wireless icon or a notification of joining, right?

---

### Post by chili555 on 2014-04-07
Please try a reboot.

---

### Post by john184 on 2014-04-08
I've rebooted. still no joy

---

### Post by john184 on 2014-04-08
OK, it's now working. I am once again joyful.
Issue was user confusion - previously I'd tried to setup the network under Network Connections > Wireless > Add, and it just wasn't connecting. 
Now I tried "Connect to Hidden Wireless Network", and it picked it up fine (maybe because the network is non-broadcasting?)
Thanks very much for your help Chili!

---

### Post by chili555 on 2014-04-08
Glad it's working. Have fun!

---

