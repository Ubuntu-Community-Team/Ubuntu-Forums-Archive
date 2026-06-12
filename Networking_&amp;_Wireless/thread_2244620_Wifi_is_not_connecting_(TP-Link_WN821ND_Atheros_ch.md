---
title: "Wifi is not connecting (TP-Link WN821ND: Atheros chip: AR9277 adapter)"
date: 2014-09-17
forum: Networking &amp; Wireless
---

### Post by avro2 on 2014-09-17
Hello!

New guy here, just installed Ubuntu 14.04!

I've been hunting down solutions of fix my wifi situation. I've recently purchased a TP-Link WN821ND wifi card and upon installing it in my desktop (ga-z68xp-ud3 mobo, made from scratch) it can't seem to log onto the wifi network. A message keeps popping up, "Disconnected: you are now offline", everytime I try to access wifi. I've ran the wireless script (and will provide at the bottom of this message) but I'm unsure what I'm looking for in there. 

Cheers!

---

### Post by praseodym on 2014-09-17
Your /etc/resolv.conf is empty, fill it by hand:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
If its not enough deactivate the hardware encryption of the driver
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
and change to pure WPA2 encryption. Check the router manual for that

---

### Post by avro2 on 2014-09-17
> echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf

Is "nnameserver" a typo? Should it be "nameserver"?

Edit: A typo in "typo".

---

### Post by praseodym on 2014-09-17
"\n" is RETURN

---

### Post by avro2 on 2014-09-17
Wifi still won't connect after plugging in both sets code into Terminal. I thing changed though. I keep getting the password authentication window everytime I try to access the wifi. What do you mean by pure WPA2? Just setting the router on WPA2?

---

### Post by praseodym on 2014-09-17
Yes, change the router settings accordingly. How many characters does the PW have? It should be at least 8 for WPA2

---

### Post by avro2 on 2014-09-17
If I can't get access to the router, is there another way?

---

### Post by praseodym on 2014-09-18
Try Wicd instead of the network-manager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Chose wlan0 as interface name and wext as driver.

---

### Post by avro2 on 2014-09-19
Hi [[COLOR=#000000]praseodym[/COLOR]]("http://ubuntuforums.org/member.php?u=1411497")!

Sorry for the late reply. Just got back from school. I've run into an issue here:

> 
avrobullet@avrobullet-Z68XP-UD3:~/Desktop/wicd-1.6.x_addon01441$ sudo ./install_wicd_addon

prüfe Wicd 1.6.x Installation...

find: `/etc/wicd/encryption/templates/active': No such file or directory

Wicd nicht gefunden
Installation abgebrochen

avrobullet@avrobullet-Z68XP-UD3:~/Desktop/wicd-1.6.x_addon01441$ 


Does this mean that the wcid file is missing something?

---

### Post by praseodym on 2014-09-19
```
sudo apt-get install --reinstall wicd
```
Did it work? Obviously, its a German installation? Check here, too:

[http://wiki.ubuntuusers.de/wicd](http://wiki.ubuntuusers.de/wicd)

---

### Post by avro2 on 2014-09-19
The sudo command stated this at the end:

 E: Unable to locate package wicd

For the website, am I to follow the steps in the installation section? Should I wait until the wicd package has been found?

---

### Post by praseodym on 2014-09-19
Wicd is located in the "universe" repository. Is that one activated?

[http://wiki.ubuntuusers.de/Paketquellen](http://wiki.ubuntuusers.de/Paketquellen)

---

### Post by avro2 on 2014-09-19
I have no idea...

Let me check online and see if I can find out how I can actvate it.

---

### Post by avro2 on 2014-09-20
Hi praseodym,

I'm have not clue how to determine if wicd is active or not...

---

### Post by avro2 on 2014-09-21
> Hi praseodym,

I'm have not clue how to determine if wicd is active or not...

Forget what I wrote. I've arrived at the part in wicd where I can connect, but when it's asking me for encryption information a window pops up blank. Researching this still. Thoughts if I don't get back to you before then?

Edit: Brain fart. When you mentioned that wicd is active, did you mean that I had it installed? In any case, I downloaded wicd-1.7.2.4 and even with that some of the gui isn't responding properly (mention of blank windows above).

---

### Post by praseodym on 2014-09-21
[http://packages.ubuntu.com/trusty/wicd](http://packages.ubuntu.com/trusty/wicd)

Download it from here, plus all dependecies.

---

### Post by avro2 on 2014-09-25
Hey praseodym,

I got wifi going, but without using wicd. I just copy and pasted the DNS, IPv4, and router addresses into the network manager. Now I have another porblem. There are times when the wifi disconnects at random, and the connection is slower than any of the connections I have on my laptop. I saw this post here:

[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)

and I wonder if I should follow the steps posted there. Thoughts?

---

### Post by praseodym on 2014-09-25
Yes, please run that script.

---

### Post by avro2 on 2014-09-25
[ATTACH]256685[/ATTACH]

---

### Post by avro2 on 2014-09-26
Hey praseodym,
I followed the stops shown in the forum page I posted and nothing seems to work. In the wireless-info text, there is an "options ath9k nohwcrypt=1" where "options" is set already.

---

### Post by varunendra on 2014-09-29
Hello avro2,

If your ethernet connection works, I suggest updating your system to current kernel (3.13.0-36) and try its native driver first.

And your 'ath9k.conf' file has unnecessarily 3 entries of the same option. Although it is still doing its job, you should overwrite the file with a single entry -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

And since you seem to have a Gigabyte motherboard, check your BIOS to see if there is a feature called "**IOMMU**". I think all the newer Gigabyte motherboards have it. If yours has too, try toggling its state to "**Enabled**". If this alone makes things work, you may choose to either keep it enabled (if it doesn't cause problem with other I/O devices like USB), or use a boot option like "iommu=soft".

---

### Post by avro2 on 2014-09-30
I'll give it a shot, varunenda. I'll update as soon as possible!

---

### Post by avro2 on 2014-10-03
> If your ethernet connection works, I suggest updating your system to current kernel (3.13.0-36) and try its native driver first.


Well I did that, but now I have a kernel panic and an unbootable computer. Thoughts?

---

### Post by avro2 on 2014-10-03
SO! I finally got internet! Because of the kernel panic I just re-installed Ubuntu 14.04.1 and everything went smoothly! Could it be that you have to install Ubuntu after you install the wifi card? Does that help for anything?

---

### Post by varunendra on 2014-10-03
Nope, it doesn't matter you install the card before or after installing it. That can only affect the logical name it is given (e.g., wlan1 instead of wlan0) in case there is/was another card in the machine. But it doesn't affect its performance.

It was possibly something else broken in the previous install. Anyway, glad the current one solved it all. :)

---

