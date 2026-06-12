---
title: "HP 355 G2 Wifi keeps disconnecting 14.04"
date: 2015-08-18
forum: Networking &amp; Wireless
---

### Post by ben172 on 2015-08-18
Hi, Newbie here, been running Ubuntu on my main desktop for a couple of month with no issues, installed 14.04 on a new laptop - HP 355 G2 - and I'm having a problem with wifi connectivity.
It connects on startup and stays connected for a few minutes then drops out. It says it's connected to my network but can't access any webpages or local devices. No issues with wired connection, that works fine.

I read the sticky first, I did this:
```
sudo apt-get update
```
and this:
```
sudo apt-get dist-upgrade
```

Then, I googled a bit more and tried this:
```
sudo apt-get install linux-firmware-nonfree
```

That seemd to help a bit, it stayed connected for longer but not fixed.

I've run the script in the sticky, results below.
[ATTACH]263925[/ATTACH]

The wifi card is a Realtek RTL8723BE 

The full hardware spec is here:
[http://www.ubuntu.com/certification/hardware/201403-14879/](http://www.ubuntu.com/certification/hardware/201403-14879/)

Really hoping someone can help, many thanks in advance.

---

### Post by praseodym on 2015-08-18
Try these module parameters:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

---

### Post by ben172 on 2015-08-18
Thanks for the quick reply,  I tried what you suggested and the connection only lasted a few seconds. 
I'd googled a bit more in the meantime and tried what you said but with swenc=0 and it seems to be a bit more stable. It's been connected for about 15 minutes since the last reboot but the connection speed is fluctuating alot, one minute it will load an image heavy page instantly, the next it's taking 30 seconds to load a simple page of text.

---

### Post by praseodym on 2015-08-18
This reduces the amount of current if the card gets too hot:
```

echo 'KERNEL=="wlan0", RUN+="/sbin/iwconfig wlan0 txpower 15"' | sudo tee -a /etc/udev/rules.d/70-persistent-net.rules
sudo service udev reload
sudo service udev restart
```
Set the encryption mode in your router to pure WPA2-AES (CCMP) instead of WPA/WPA2 mixed mode. Also try deactivating IPv6 in the network-manager profile

---

### Post by ben172 on 2015-08-18
Many thanks, the WPA2 only trick seems to have solved it, connection speed seems much more stable now. Will test again later when the family aren't using other devices on the wifi.
This is why I finally made the move from Windows after all this time, people told me that the community support for Ubuntu was awesome and they were right, thanks again.

---

### Post by ben172 on 2015-08-19
Looks like I spoke too soon, it's better but stil unreliable. 
Is there anything else I can try?
I'm open to replacing the wifi card if need be.
It may be unrelated but the battery seems to drain very quickly if I'm connected via wifi
Also, the signal strength graphic shows the signal strength fluctuating constantly even when I'm right next to the router.

---

