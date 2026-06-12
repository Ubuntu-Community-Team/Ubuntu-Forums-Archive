---
title: "wireless connection problems &amp; now lost lan connection &amp; network manager wont work"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Rainbowserpant on 2009-09-04
I have installed ubuntu 9.04 as a dual boot with xp and ubuntu on their own hardrives.

I originally had problems connecting via lan or wireless with 'Network Manager'and followed advice to use 'Wicd Network Manager'.

With 'Wicd' I was able to connect to the internet via lan ethernet cable with no problems but I could still not connect to my wireless network although it does show up in 'Wicd'. I have enabled manual connection settings in wicd to connect to my network to use static ip addresses for my computers on my network which works fine with the lan connection.

I followed more advice which suggested using ndiswrapper but I could not make any real sense of what to to using the link I was provided. I then did a google search 'how to use ndiswrapper ubuntu' and followed the instructions at 
[COLOR="Red"]"https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Load the new driver module".[/COLOR]

After following these configuration instructions below I immediatly lost my lan connection and wicd network manager will not open anymore.

[COLOR="red"]3.1. Disable Free Drivers
Firstly, all releases since Ubuntu 6.06 have the open source bcm43xx driver, which was replaced in 8.04 by b43 and b43legacy, see WifiDocs/Driver/bcm43xx. If this driver doesn't work for you, then you should disable it, because it will conflict with ndiswrapper. To disable it, add blacklist bcm43xx lines for each driver to the modprobe blacklist. 
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist[/COLOR]

I continued on until instruction 3.6 'configuring wireless network settings' where I could not continue as I could not understand the instructions.

Now I have no internet connection and it appears no network manager.

Wicd still shows up in Applications > Internet but it wont open?

I reinstalled wicd but the same problem occurs.

I am completely new to ubuntu but it seems I would need to restore the drivers I disabled but I have no idea how to do this. :(

Please Help

---

### Post by xir_ on 2009-09-04
I've never done this before but this is my best ***guess***

It seems that you have just blacklisted these "[COLOR=red]blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb"

[/COLOR]i think that to fix this you need remove the drivers that you have black listed from this file
```
sudo gedit /etc/modprobe.d/blacklist
```

[COLOR=red][COLOR=black]inside the file this should look like[/COLOR]
[/COLOR]```
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
```

Let me know how it goes and as always keep a backup

---

