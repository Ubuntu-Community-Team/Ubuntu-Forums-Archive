---
title: "How I got my Belkin BCM4306 Wireless Desktop card working with ndiswrapper and WPA"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by UrbenLegend on 2006-09-04
After massive Googling and searching on several Linux forums, I have finally set up my Belkin 54G Desktop Card based on the Broadcom 4306 chipset using ndiswrapper and WPA encryption. I'd like to share my way of doing it just to save others with a similar setup from frustration.

My WPA setup was a bit unorthodox since I couldn't find the '/var/run/wpa_supplicant', the '/etc/wpa_supplicant.conf', and the '/etc/default/wpasupplicant' config files. Right, so here is my way of setting up my wireless and hopefully this will be of use.

1.) Install the ndiswrapper-utils and wpa_supplicant packages from the cd.

2.) Here I noticed that my wireless card was listed as eth0, which felt odd to me, so I changed the entry in my '/etc/iftab' file from 'eth0 *macaddress* arp 1' to 'wlan0 *macaddress* arp 1'. My wireless card correctly showed up as wlan0 in Network Settings.

3.) Now I installed the driver that came with my Belkin cd into ndiswrapper using the lines:
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

```
I then edited my '/etc/modules' file and appended ndiswrapper to the end of the file and closed it.

4.) I realized that the ndiswrapper driver was not being used, but instead bcm43xx was being used. A quick look at the output of 'lshw' told me that (scroll through the output of 'lshw' and search for your card. It should say under 'driver' which driver is being used). Not wanting to deal with bcm43xx and fw-cutter, I blacklisted it by creating a file in '/etc/modprobe.d' called 'blacklist-bcm43xx'. In this file I typed 'blacklist bcm43xx' and I closed the file. The file doesn't necessarily have to be named 'blacklist-bcm43xx'. It just has to begin with 'blacklist'. If you want you can append to the 'blacklist' file already there, but I don't recommend this because I don't want to tamper with original settings if I don't have too and would simply like to be able to delete a file if something goes wrong. After this I rebooted my machine.

5.) The ndiswrapper driver loaded up but my system hanged all of a sudden. On another computer I found out that I had a revision 3 version of my card and that it had problems with the 'bcmwl5.inf' driver. But just when I was about to dispair, I found out that by removing 'NetworkType|0' from my '/etc/ndiswrapper/bcmwl5/14E4:4320:1799:7000.5.conf' file, the system didn't hang. I then booted up ubuntu from the live cd, mounted my ubuntu install, and changed the file from there and everything proceeded normally.

At this point I was able to use my wireless without encryption or with WEP encryption. If this doesn't work, you've probably done something wrong.

Now for the odd part: wpa_supplicant.
Having been unsuccessful in finding the configuration files mentioned above for wpa_supplicant and noticing that wpa_supplicant didn't load up on boot, I took the following measures.

6.) I launched Network Settings and configured my card by clicking Properties. Here, enter your ssid and choose either dhcp or static ip (configured appropriately), but leave the password BLANK.

7.) There was no /etc/wpa_supplicant.conf in which to store my WPA pre shared keys, so I simply created one and put the output of 'wpa_passphrase *ssid* *key*' into the file and closed it.

8.) I tested wpa out by typing
```
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -w
```
This seemed to allow me to connect to my router. If it doesn't work for you, try deactivating and activating your card in the network settings. I also decided to create a '/etc/default/wpasupplicant' file with the contents:
```
ENABLED=1
OPTIONS="-iwlan0 -c/etc/wpa_supplicant.conf -Dndiswrapper -w"

```
but I doubt this made any difference in the grand scheme of things.

9.) However wpa_supplicant didn't startup automatically on reboot. Seeing this I edited my '/etc/rc.local' script, a script that executes right after boot, and added:
```
wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -D ndiswrapper -w -B
```
Note the -B appended at the end. This makes wpa_supplicant run in the background. Also there is no need for sudo since the script is launched by superuser.

10.) This did it, my internet connection was working right after boot and connected and disconnected automatically when the router was turned on and off. However I noticed that my hostname in my dhcp client list was listed as null. I edited my '/etc/dhcp3/dhclient.conf' file, uncommented the line that said 'send host-name "*some hostname*";' and changed it to whatever I liked.


Hope this helps some people here and if anyone would like to point something wrong with these instructions feel free to do so! I think these instructions should also work with any other chips in the bcm43xx series, although I might be wrong.

---

### Post by Mazza558 on 2006-09-05
Sounds like the right way to do it, I'll have a go, thanks :)

---

### Post by UrbenLegend on 2006-09-06
By the way I meant Network Settings in the Administration menu instead of the Network Manager Applet. I've edited my post above to reflect that. I don't think Network Manager works with it.

---

### Post by wakaimono on 2006-09-09
These directions helped me get the card working, however I am having trouble with the WEP ker being remembered. Do you think I missed something in your steps?

---

### Post by jglen490 on 2007-01-15
Urbenlegend  --

Thanks a bunch for your post.  I used it to get my Buffalo PCMCIA card going; it uses the Broadcom 4318 chip, but the principles are the same.  I think the key was blacklisting the bcm43xx driver loaaddded by the kernel.  I was about to throw the Buffalo card out the window.  Thanks again!!

---

