---
title: "Atheros QCA9565 - WiFi problem - Ubuntu 14.04 LTS"
date: 2015-11-08
forum: Networking &amp; Wireless
---

### Post by Anheru on 2015-11-08
Hello,

I've installed **Ubuntu 14.04 LTS** on **Samsung ATIV Book 9 Lite NP915S3G-K02UK**. From beginning I had problems with unstable WiFi connection, so I tried to solve this problem with many different solutions found on google (disabling "n" mode, disabling IPv6, some other changes with "modprobe" which i don't remember), but nothing helped. I had connection lost randomly - once it works for an hour, next time it disconnecting every two minutes... Most of times after losing connection, it cannot connect again (sometimes even losing my WiFi from available network list) so i had to switch off and on again whole Wireless (via gnome network manager) to connect it back. Yesterday WiFi decided to stop working at all. My WiFi is still on network list but it just cannot connect to it (without any message).

I'm sick of tired of fighting with it, so it's time to ask you for help.

1. Here is the wireless-script result: [http://pastebin.ubuntu.com/13195997/](http://pastebin.ubuntu.com/13195997/)
2. Network I'm trying to connect: TALKTALK-0F4878
3. I'm using this WiFi on another pc and smartphone, and it works. I still  have Windows on another partition, and WiFi works on it. So **it's only  Ubuntu's problem.**
4. I've just tried commands from post #6 in this thread: [http://ubuntuforums.org/showthread.php?t=2238899&p=13095893#post13095893]("http://[URL") - it didn't help
5. **I don't have access to modem**, so I can't switch wpa mode/channels/etc. and I cannot connect laptop with cable (eth) so I don't have any internet connection there atm (in case of some new drivers needed, I can download them via another pc).
6. Yeah, I know, my english is not perfect, sorry for that ;)

I hope somebody here can help me with it, because I really like this OS but without network connection it will be just useless.

Kind regards,
Anheru

---

### Post by praseodym on 2015-11-08
Please change the encryption mod in your router to pure WPA2-AES instead of mixed WPA/WPA2. Also try

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Anheru on 2015-11-08
Thank you praseodym for answer.

Yes, it helped. Connection works again and so far I didn't lose it even once.
If in next 24 hours connection will be stable, I'll mark this thread as solved.

---

### Post by Anheru on 2015-11-09
During last 24h I had connection drop only two times. So it's MUCH better :) Thank you again praseodym for help.
Thread solved.

---

### Post by Anheru on 2015-11-22
Alright, after two weeks problem returned. All the time I had connection losts, but only once-twice a day. Now it's again about 5-10 times...
Here is new wireless-script test: [http://pastebin.ubuntu.com/13461918/](http://pastebin.ubuntu.com/13461918/)

---

### Post by Anheru on 2015-11-23
Just tried to make this post on Ubuntu, and after about 20 connection lost, wifi stopped work at all.
I'm getting tired of this ****. What is the point of making this OS if even most important things doesn't work?
And nobody know how to fix it...

---

### Post by Hadaka on 2015-11-23
Hi, did you bring the os up to date after you loaded it with?
```
sudo apt-get updates
```
*If not..do so .......and then COPY and paste
```
modinfo ath9k | grep -i "168C:0036"
```
post the output. or state if there is no output.
thanks

---

### Post by Anheru on 2015-11-23
I did update many times. I can't do it now because there is no internet connection (did I mentioned about wifi problem?)
There is no output.

---

### Post by jeremy31 on 2015-11-23
Can you contact someone who can change the encryption settings for the wifi and have them change it to WPA2 only with no WEP or TKIP?

I have a few Atheros wifi cards and they do not work well with TKIP for very long.  The best I could do with a TKIP encrypted network was use a wifi repeater and have it change the encryption

---

### Post by Anheru on 2015-11-23
jeremy31, I have now access to router and I already changed encryption  to "WPA2-Only" after last advice from praseodym (few posts ago) -  screenshot: [http://i.imgur.com/zQKwccu.jpg](http://i.imgur.com/zQKwccu.jpg)

Some additional info:
New wireless-script test result: [http://pastebin.ubuntu.com/13482342/](http://pastebin.ubuntu.com/13482342/)
syslog about wireless: [http://pastebin.ubuntu.com/13483294/](http://pastebin.ubuntu.com/13483294/)

---

### Post by Hadaka on 2015-11-23
Hi, from your working wired connection please
COPY and paste.
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
remove wired connection and test wireless
thanks.

---

### Post by Anheru on 2015-11-23
It didn't help.
Last syslogs: [http://pastebin.ubuntu.com/13485422/](http://pastebin.ubuntu.com/13485422/)

btw. I did this 'wpa.conf' thing from here (comment 22): [https://bugzilla.kernel.org/show_bug.cgi?id=100621#c22](https://bugzilla.kernel.org/show_bug.cgi?id=100621#c22)
Well, it didn't helped, but looks like changed something in logs, so it might be important...

---

### Post by praseodym on 2015-11-24
Try Wicd instead:
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
If it works better or well, then uninstall the network-manager.

---

