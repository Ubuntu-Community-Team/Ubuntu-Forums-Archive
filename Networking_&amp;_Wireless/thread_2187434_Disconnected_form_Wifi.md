---
title: "Disconnected form Wifi"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by dina.rasquinha on 2013-11-12
[COLOR=#000000]I purchased a new system Dell inspirion15 with ubuntu 12.04 OS. Everything was fine, then suddenly my wifi connection went off.
I do not see the signal strength on the wifi symbol nor any options for available networks which are present. The Fn+F2 option switches on/off the bluetooth but no effect on the wifi. I do not have any other external option for wifi settings.
I have tried the following:
$ rfkill list

soft blocked :no
hard blocked:no

$ rm -r ~/.config/ ~/.cache/
and restarted my system but no use.
$ sudo /etc/init.d/network-manager restart
no use either.


Link to wireless information[/COLOR]
 [COLOR=#000000][pastebin.com/2Ei8225F]("http://pastebin.com/2Ei8225F")

Hoping for some sugesstions[/COLOR]

---

### Post by chili555 on 2013-11-12
Let's try to load the driver and see what happens:```
sudo modprobe ath9k
```Is a wireless interface, ideally wlan0, created?```
iwconfig
```If so, the only problem is that the driver didn't load automagically; we'll fix it:```
sudo -i
echo ath9k >> /etc/modules
exit
```If that didn't fix it, let's see why in the message logs:```
dmesg | grep ath
```> $ rm -r ~/.config/ ~/.cache/
and restarted my system but no use.I don't understand why you would do that. Did you read that somewhere?

---

