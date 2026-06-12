---
title: "Ubuntu 17.10, WiFi unstable, can fix with phone tethering"
date: 2018-02-19
forum: Networking &amp; Wireless
---

### Post by john_ladasky on 2018-02-19
Oh, how I miss living in a house with a Cat5e wall jack.

In my current residence, I have to connect my desktop PC using WiFi.  I purchased an ASUS PCE-N15 Wireless-N card based on a list of Linux-recommended routers that I found.  Most of the time it works, but when it starts to misbehave, I can have hours of misery, with repeated dropped connections, and slow transfer speeds.

Now, this is specifically when I'm using Linux.  My system is dual-boot.  Using the same hardware running Windows 10, I haven't noticed any major problems.  I rarely use Windows though, so maybe I'm just getting lucky.  Also, I have an Android phone.  If I connect my phone to the home WiFi, and to a USB port on my computer, and I place the phone in tethering mode, I can correct my connection problems with Linux.  

This would suggest that I have a flaky Linux driver for my wireless card.  Before I reach that conclusion, does anyone know how to confirm which upstream connection my phone is using?  The phone's display says that it's connected to WiFi, but I don't know whether to trust a little icon.  It's possible that I'm actually routing through my cell phone's LTE network.  I would like to know for sure before I tinker with the driver.

Thanks!

---

### Post by wildmanne39 on 2018-02-19
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created.

---

### Post by john_ladasky on 2018-02-19
Hi wildmanne39, thanks for your reply.

Following the first few instructions in your post, I've executed **sudo apt update** and **sudo apt dist-upgrade**.  As of now, my WiFi is working fine over Linux... so did I fix a problem?  Since the problem is intermittent, I will have to wait for a while to see whether it returns.

---

### Post by wildmanne39 on 2018-02-19
Probably not but it is always best to run those commands first when we are beginning to trouble shoot wifi issues.

---

### Post by john_ladasky on 2018-03-02
OK, I had a busy week.

I ran the wireless script twice.  I started tethered through my phone, because earlier this evening my wireless-N adapter dropped my connection again:  [http://paste.ubuntu.com/p/MGkdcXDTPD/](http://paste.ubuntu.com/p/MGkdcXDTPD/)

Then I unplugged my phone, and I happened to re-connect successfully through my wireless-N (actually, it usually works):  [http://paste.ubuntu.com/p/kzwtv4W39M/](http://paste.ubuntu.com/p/kzwtv4W39M/)

I can see some changes between the two files in the NetworkManager Info region.  I'm not sure what they mean.  I'm not sure whether there are other changes.

One encouraging thing that I can see is that, when I'm tethered, I'm definitely connected to the house router and not to LTE.  So I'm changing just one variable between the two conditions, how I connect between my desktop PC and the router.

---

### Post by wildmanne39 on 2018-03-07
There is a lot of information missing from that file you posted so I can only see two things that can be changed but one of them is probably your biggest issue, so please do the following commands by copying and pasting for accuracy.
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then:
```
echo "options rtl8192ce swenc=1 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
watch for errors I may have the wrong parameter without the rest of the file I can not be 100 percent sure but if it throws an error we will know and it will do no harm.
Reboot

---

### Post by kerry_s on 2018-03-07
are you using a hidden ssid?

if so unhide & then try

---

