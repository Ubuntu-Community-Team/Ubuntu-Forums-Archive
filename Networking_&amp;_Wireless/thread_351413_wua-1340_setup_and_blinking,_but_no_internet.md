---
title: "wua-1340 setup and blinking, but no internet"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by mb1243 on 2007-02-01
wow can ubuntu be anymore of a pain to setup wireless, I went through a tutorial to set up my d-link wua-1340 wireless adapter and the card is blinking and stops blinking when I bring the service down, but it cant ping anything or make any connections to websites. I've changed my nameserver but still not luck, i dont know what else to do next, ive configured the interfaces file like its suppose to be but nothing seems to work, it is driving me crazy

---

### Post by Floppyjoe on 2007-02-01
Can you connect to your router or scan for Access points?

---

### Post by mb1243 on 2007-02-01
says 
connect: Network is unreachable

when i try and ping my router address

---

### Post by Floppyjoe on 2007-02-01
> **mb1243 said:**
> says 
connect: Network is unreachable

when i try and ping my router address
What is your wireless cards designation? eg. Wlan0
What happens when you open a terminal and enter:
```
sudo iwlist wlan0 scan
```

---

### Post by mb1243 on 2007-02-01
the designation is rausb0 and it scans fine

Cell 01 - Address: 00:13;46;1E:01:18
ESSID: "BiggetyBalla"
Mode:Managed
Channel:6
Encryption key:on
Bit Rate:0 kb/s

thats my wireless router

---

### Post by Floppyjoe on 2007-02-01
So are you using Wep or Wpa encryption? Are you using a portable or desktop computer?If you are using a portable you may want to set up Network-Manager. If not then you will need to set up your network interfaces file with the right parameters(eg. Essid MODE Password etc.)

 It's usually best to try to get your wireless working with no encryption to start off with and then add it when you get it working.If you are using WPA you need to install WPA Supplicant. 

Your driver may not be the right one for your wireless card. In that case you may need to build a driver for your card. You might also try using ndiswrapper with your windows drivers that came with the card.

---

### Post by mb1243 on 2007-02-01
yes im using wep and it is for a desktop, I have configured the interfaces file correctly, and installed a modified native linux driver following this tutorial [http://www.ubuntuforums.org/showthread.php?t=270756&highlight=wua-1340](http://www.ubuntuforums.org/showthread.php?t=270756&highlight=wua-1340)
i used triplewithcheese's tutorial and it got the damn thing blinking but thats it
before that i installed ndiswrapper and installed my .inf driver but that did absolutely nothing so i uninstalled the driver and ndiswrapper.

---

### Post by Floppyjoe on 2007-02-02
I looked at that tutorial and it seems difficult. What do you get when you issue:
```
sudo dhclient rausb0
```

---

### Post by mb1243 on 2007-02-02
Listening on LPF/rausb0/00:15:e9:85:32:3d
Sending on LPF/rausb0/00:15:e9:85:32:3d
Sending on Socket/fallback
DHCPDISCOVER on rausb0 to 255.255.255.255 port 67 interval 5

 and that keeps going with different intervals until i stop it

do i need to change this 00:15:e9:85:32:3d somewhere, cause thats not my devices id i know that

---

### Post by Floppyjoe on 2007-02-02
That seems odd that it would use a different ID then the device your are using. I don't know how to change that because it has not happened to me before.If you have the password set properly in the interfaces file one would think you would be able to connect. Can you display your /etc/network /interfaces file?
```
sudo gedit /etc/network/interfaces
```
I did read about a program called MACCHANGER that you can download to change Mac addresses.I don't know if that would help though.

---

### Post by mb1243 on 2007-02-02
auto lo
iface lo inet loopback

auto rausb0
iface rausb0 inet dhcp
wireless-essid BiggetyBalla
wireless-key *****

i got everything else commented out

---

### Post by Floppyjoe on 2007-02-02
try adding 
```
wireless-mode managed
```

---

### Post by mb1243 on 2007-02-02
nope same thing, i appreciate u responding and trying to help me though

---

### Post by Floppyjoe on 2007-02-02
How about:
```
wireless-mode master
```

---

### Post by mb1243 on 2007-02-02
same

---

### Post by Floppyjoe on 2007-02-02
When you added:
```
wireless-mode managed
```

did you reboot the computer?
maybe try that.

---

### Post by mb1243 on 2007-02-02
i rebooted, and i also restarted the device

---

### Post by Floppyjoe on 2007-02-02
I hate to tell you this but I'm running out of Ideas. Perhaps someone more knowledgeable on this forum has something to add?Anyone?

---

### Post by mb1243 on 2007-02-02
bump

---

### Post by superyounan1 on 2007-02-28
I'm having the same exact problem - followed countless tutorials and read many pages about this, ndiswrapper simply isnt working, and the native driver gets me to the same place (card lights, blinks, can scan but not connect) except my MAC address seems to be in order.

Please someone, help

They should call it "linux for saints", not humans, its such a pain in the neck to get your devices working right

---

### Post by Floppyjoe on 2007-02-28
This guy says he got his working here:
[http://www.ubuntuforums.org/showpost.php?p=1920111&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1920111&postcount=4)

---

