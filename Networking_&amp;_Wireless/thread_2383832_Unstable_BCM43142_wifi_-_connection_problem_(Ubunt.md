---
title: "Unstable BCM43142 wifi - connection problem (Ubuntu 16.04.03)"
date: 2018-01-30
forum: Networking &amp; Wireless
---

### Post by hargitay on 2018-01-30
First of all. I still love Ubuntu, and I still love unity. I have tried dozens of OS-es, but Ubuntu is still my favourite OS.
Unfortunately I am having problems with my wifi connection which is very unstable. My laptop is seemingly connected to the wifi network, but sometimes it just stops downloading and uploading. 
Disabling and re enabling the network connection seems to fix the problem temporally. I do live streaming almost every day. And if the connection fails, the live stream is over.:(

1. I don't remember having these issues with Ubuntu 14.04
2. Ever-since I upgraded to Ubuntu 16.04 I am struggling with the wifi connection.
3. I have never been able to use my Bluetooth, but this is the smallest problem.
4. I am not having this issue with Lubuntu 16.04.3, Manjaro, Windows, Debian,etc...
5. A week ago my wifi totally disappeared, then I reinstalled it. This seemed to solve the problem, but now I am experiencing connection problems rarely but unexpectedly again. :(
6. I ran a script, found [here]("https://ubuntuforums.org/showthread.php?p=13024222#post13024222"),
Results Attached.

If anyone has any ideas, why this issue is only happening in Ubuntu 16.04, please feel free to give me some wisdom! :) 

[ATTACH=CONFIG]278375[/ATTACH]

---

### Post by howefield on 2018-01-30
Moved to the "*Networking & Wireless*" forum.

---

### Post by Hadaka on 2018-01-30
Hi, From a working wired connection please open a terminal then Copy and Paste..
#Update features and kernel
```
sudo apt-get update
sudo apt-get dist-upgrade
```
#Insure wl-bcmwl-kernel-source is current
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall bcmwl-kernel-source
```
#wlp2s0 ESSID-"blue"Power Management-on ~ Set to off
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
#[connection] id=blue | type=wifi | [ipv6] method=auto ~ Set to Ignore
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/blue
systemctl restart network-manager.service
```
#Regio- Europe/Buchares country 00: DFS-UNSET~ Set to RO
```
sudo iw reg set RO
sudo sed -i 's/=.*/=RO/' /etc/default/crda
```
Disconnect wired connection boot and test wireless

---

### Post by hargitay on 2018-02-01
Thanks a lot, for your suggestion!
I will try your  solution as soon as I will have a wired connection. 
As mentioned before, my wifi is working, but it is unstable. It looses the signal unpredictably. Sometimes I don't have this problem for days. 
Did you figure anything out from the results attached? What could be be the problem?

---

### Post by Hadaka on 2018-02-01
Hi, providing the wireless connection stays up, the commands
may be done without a wired connection. The update and upgrade
command are usually done wired.The rest do not need to be.
The "#" comments above the code to insert reflects the current state
of the item..the "Set to..is the change to that state. I.E.

"#wlp2s0 ESSID-"blue" Power Management-on ~ Set to off"

The Power Management feature for wlp2s0  is currenty 'ON'...
This command Sets it to 'OFF'
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Thanks.

---

### Post by hargitay on 2018-02-08
Dear Hadaka!
I followed your hints, and tested my wifi... so far s good. Your advice seems to have fixed my problem. Do you think, that I will have to do this every time I reinstall the system? Do I have to start with purging an reinstalling the BCMWL driver, or it should be enough to do the last three steps (Setting the power management to off, ipv6 to ignore, reg set to RO)?

Thanks a lot for your kind support! May the love of the Almighty shine upon you every day! :)

---

