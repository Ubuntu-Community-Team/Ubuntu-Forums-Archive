---
title: "Why?!  Why?!  Why?!  Wireless!"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by dodle on 2008-09-03
I've seen the same problem all over this forum, but I haven't found an answer for it.  I guess it's just hardware compatibility issues.  I had been trying to get a wireless card working that I got out of a Dell computer that uses the BCM4306 chipset.  I gave up on that and reinstalled the card that came with my laptop:  Ralink RT2560F, which if I used with ndiswrapper I could see my network but I couldn't connect to it.  Then my network would disappear, and I could't see it again until after a reboot.  So I decided to try my Sabrent USB 802.11g card.  I install the driver with ndisgtk and everything works perfectly.  Can see the network, can connect to it.  But, I need my USB card for another pc.  Why am I having such isssues?

```
laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

   [COLOR="Red"]This is the Ralink card[/COLOR]

wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

   [COLOR="Red"]This is the Sabrent USB Card)[/COLOR]

wlan2     IEEE 802.11g  ESSID:"Antum"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:4A:5E:80   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by falcon61102 on 2008-09-03
Well, if you want to try to reinstall the BCM4306 card, I'll try to help you out with that one.

---

### Post by dodle on 2008-09-03
I reinstalled it, but I'm also reinstalling Wubi.  But I have to wait until Wubi finishes reinstalling.

---

### Post by falcon61102 on 2008-09-03
Alright, that may end up being easier in the long run because you'll have a fresh start.  Did you check out this page when you first went at it:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If you did, don't dispair, there are some easier methods than what's given there so it's not hopeless yet.

---

### Post by dodle on 2008-09-03
I've tried the link you gave me and it still is not working.  My system keeps freezing during the "sudo rmmod" commands in the "Hardy But Fix" section.

---

### Post by falcon61102 on 2008-09-03
At which module is it freezing at?  

What you can do to disable the unneeded modules is add them to the blacklist and then reboot.  Once you restart, those modules won't be loaded and you won't have to remove them.  So if you can determine which module it is freezing on, add that to the blacklist here:
```
gksudo gedit /etc/modprobe.d/blacklist
```

---

### Post by dodle on 2008-09-03
I followed the guide here: [http://ubuntuforums.org/showthread.php?t=201902&highlight=blacklist+b43]("http://ubuntuforums.org/showthread.php?t=201902&highlight=blacklist+b43").  I can now see see my wireless network, but I still can't connect to.  Plus, after a couple of times trying to connect, the network disappears.```
@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 03
       serial: 00:90:96:b5:4d:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,11/02/2005, 4.10.4 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:27:26:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=64 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

```

---

### Post by falcon61102 on 2008-09-03
Are your access points secured?

---

### Post by dodle on 2008-09-03
> **falcon61102 said:**
> Are your access points secured?

You mean is my network password protected?  Yes, with WPA, and I can connect to it if I use my USB network card.

---

### Post by falcon61102 on 2008-09-03
Ok, that is more than likely the issue here.  By what you've posted, it appears that your drivers for your BCM card are properly installed so it just seems that the card is having trouble with your wireless security.

Alright, try this.  You ndiswrapper should be properly installed and the first command is just to make sure it's loaded.  If you get a warning stating that it's already loaded, that's fine, just continue with the other commands.
```
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

EDIT: There may be one more step you need to do before your Network Manager will recognize the access points:
```
sudo /etc/init.d/dbus restart
```

Post back any errors or results.

Taken from:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

