---
title: "B43 driver = extremely slow internet"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by dracule on 2008-09-11
I have had this laptop for about 2 years, and have always used linux on it. 

When I moved into my new dormroom, i have "low" signal strength in Windows. 

In windows everything is fine, everything is fast, everything is great. 

the problem is that the internet in Linux is agonizingly slow. It is nearly sub-dialup speeds. Opening a page in youtube takes around 30 seconds to load (not including the video). 

I am extremely sad because I love linux and want to use it but the internet is so slow i cant use it. 

If I move a little closer to the router my internet speeds up to a point where it is about normal. 


is there ANYTHING I can do?

---

### Post by Ayuthia on 2008-09-12
> **dracule said:**
> I have had this laptop for about 2 years, and have always used linux on it. 

When I moved into my new dormroom, i have "low" signal strength in Windows. 

In windows everything is fine, everything is fast, everything is great. 

the problem is that the internet in Linux is agonizingly slow. It is nearly sub-dialup speeds. Opening a page in youtube takes around 30 seconds to load (not including the video). 

I am extremely sad because I love linux and want to use it but the internet is so slow i cant use it. 

If I move a little closer to the router my internet speeds up to a point where it is about normal. 


is there ANYTHING I can do?

You can always try ndiswrapper.  If you have a 4311, 4312, 4322, or 4328 card, you can also try installing the wl driver: 
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

If you are not sure about which card you have, go to the Terminal and type:
```
lspci -nn
```
Look for something that looks like 14e4:4311.

---

### Post by Crafty Kisses on 2008-09-12
I'd like to see the results of:
```
iwconfig
```

---

### Post by dracule on 2008-09-14
> **Codename said:**
> I'd like to see the results of:
```
iwconfig
```

When I am in another room where reception is really good:
```

wlan0     IEEE 802.11g  ESSID:"*****"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=80/100  Signal level=-53 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

when i am in my room and the internet is extemely slow:
```

wlan0     IEEE 802.11g  ESSID:"*****"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=63/100  Signal level=-69 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ndiswrapper looks pretty complicated to install. especially since i do not have any ethernet

---

### Post by deviations on 2008-09-14
I'm also getting extremely slow internet via BCM4311. I installed ndiswrapper and my speeds are still the same. 40 kb/s with wireless in Ubuntu and 700 kb/s with ethernet in Ubuntu or wireless in Windows. 

Here's the iwconfig:

```

wlan1     IEEE 802.11g  ESSID:"NETGEAR80211b"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:B5:1B:47:20   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=88/100  Signal level=-40 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Crafty Kisses on 2008-09-14
From what I've read and some research I've done, you can get it working decently with Dapper, Feisty and Gutsy, but I'm not too sure about Hardy, but try this in Hardy and see if you guys have any luck.

1. Install **build-essential** from Synaptic (for compiling ndiswrapper)

2. Download latest stable version of **ndiswrapper** from [http://sourceforge.net/projects/ndiswrapper/](http://sourceforge.net/projects/ndiswrapper/)

3. Compile the **ndiswrapper**

4. Blacklist the bcm43xx module:
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

5. In order to get 'iwlist scanning' to display results, you need to edit your **/etc/network/interfaces** file to contain the appropriate settings the AP:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid MYSSID
wireless-key s:mysecretwepkey

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

Then you need to install **network-manager-gnome** it seems to  cure a lot of problems. The card should now be recognized as wlan0 and the network manager handles all the 
settings (WEP, scanning, etc.). 

Remember **any kernel updates ** require the ndiswrapper to be recompiled.

My own method, might work, but I'm not really sure. Give it a shot and let me know.

Install the following package:
```
sudo apt-get install ndisgtk
```
From there, open **ndisgtk** then it will ask you for the .inf file, which means you need to download the Windows XP driver for the card, and you can get the drivers right [**here**]("http://ftp.us.dell.com/network/R115321.EXE"). After you have the drivers unzip them, then do the following:
```
sudo ndiswrapper -i drivername.inf
```
Once you have the **.inf** file you can install it using **ndisgtk** and let's see if that gets it up and going a little faster.

---

