---
title: "WiFi log?"
date: 2016-12-30
forum: Networking &amp; Wireless
---

### Post by Langstracht on 2016-12-30
In the last couple of days I've been experiencing regular network disconnects.  NOT a problem I "ever" had before.

It's not at all clear to me whether it's the laptop (Acer Aspire 5251, ubuntu 14.04) or the router (LinkSys WRT320N) or the modem (SpeedStream 5200) or my ISP that's misbehaving ... and I am wondering whether ubuntu maintains a log of what's going on and how I can access it.

Alternatively, if there is no "default" log, is there some way I can create one.

TIA

---

### Post by wildmanne39 on 2016-12-30
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by Langstracht on 2016-12-30
Thanks for replying,

The resulting code is more than 500 lines so I thought better an attachment.

Appreciate your help with this.

---

### Post by wildmanne39 on 2016-12-30
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
```
sudo sed -i '/blacklist brcmsmac/ d'  /etc/modprobe.d/blacklist-bcm43.conf
```
your computer should connect and work well if it has connection issues there are some settings we can change but we will wait and see.
Thanks

---

### Post by Langstracht on 2016-12-30
Just want to be sure,  by everything you mean:

```
sudo apt-get purge bcmwl-kernel-source

sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit

sudo sed -i '/blacklist bcma/ d' /etc/modprobe.d/blacklist.conf

sudo sed -i '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf

sudo apt-get install --reinstall network-manager-gnome
```

I noticed references to 16.04.  Presumably this is also good for 14.04 which is what I am running ...

Again, thanks

---

### Post by wildmanne39 on 2016-12-30
I changed the directions a little just run the commands in the post above.
Thanks

---

### Post by Langstracht on 2017-01-03
Seasonal festivities got in the way of fixin'.  And caution in the way of reporting back.

I've run all the commands.  And have significant amelioration ... but not eradication.

My laptop is still disconnecting - but maybe twice a day rather than six or more times.

I presume that the commands dealt with problem(s) on the laptop (I COULD pretend I knew what they were and how they were corrected!) so that any problems I have now are either with the modem or the router.

Confirmation that's the case would be muchly appreciated.

Thanks for your much appreciated help.

---

### Post by wildmanne39 on 2017-01-03
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

