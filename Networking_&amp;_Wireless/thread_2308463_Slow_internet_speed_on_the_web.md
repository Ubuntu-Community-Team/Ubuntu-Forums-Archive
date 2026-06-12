---
title: "Slow internet speed on the web"
date: 2016-01-03
forum: Networking &amp; Wireless
---

### Post by enricobe on 2016-01-03
Hello,
I'm using Xenial (16.04) but I got the same problem since I've started using Ubuntu (14.04).
Web surfing works fine, but when I try to download any file the speed is low. I've done a test:

PC1: Toshiba C855-2j5 with realtek RTL8723AE
PC2: Acer travelmate 4500 (bought in 2004!) with intel pro wireless 2200 

I've launched a "wget" command of an Ubuntu ISO from an Italian mirror.

PC1: max speed 500 kb/s (the average speed was about 350 kb/s)
PC2 max speed 800 kb/s (which is the max speed for my ADSL contract)
same problem if I try to download something via firefox

I think this can be due to a poor driver support for this wifi card, but if I try to download an ubuntu ISO from .torrent I get a full speed download! It seems that only HTTP/FTP protocols are so slow on this wireless card. Could you suggest other tests that I can do?

---

### Post by Hadaka on 2016-01-03
Hi,from what information you have provided it appears to be
a firefox issue and not a ubuntu dirver problem. Try this..
[https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding?redirectlocale=en-US&redirectslug=Firefox-hangs#w_turn-off-hardware-acceleration](https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding?redirectlocale=en-US&redirectslug=Firefox-hangs#w_turn-off-hardware-acceleration)
if that doesnt help the run the wireless info script and post the wireless-info.txt file that will be created in your home directory.
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
thanks.

---

### Post by enricobe on 2016-01-03
> **Hadaka said:**
> Hi,from what information you have provided it appears to be
a firefox issue and not a ubuntu dirver problem. Try this..
[https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding?redirectlocale=en-US&redirectslug=Firefox-hangs#w_turn-off-hardware-acceleration](https://support.mozilla.org/en-US/kb/firefox-hangs-or-not-responding?redirectlocale=en-US&redirectslug=Firefox-hangs#w_turn-off-hardware-acceleration)
if that doesnt help the run the wireless info script and post the wireless-info.txt file that will be created in your home directory.
[http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)
thanks.

Hi. I don't think this is a firefox-related problem because I get the same slow speed with "apt-get" or wget as they download from an HTTP server. It seems to be an HTTP-protocol problem. BitTorrent protocol works fine.
I'm not an expert or a developer so I can't say where is the problem or if the HTTP-related problem makes sense.

Please find attached the wifi report (tar.gz).
[ATTACH]266524[/ATTACH] 

Thank you very much!

---

### Post by Hadaka on 2016-01-03
Hi your wireless report shows..
```
#wlp8s0: disabling HT as WMM/QoS is not supported by the AP
#wlp8s0: disabling VHT as WMM/QoS is not supported by the AP
```
these are related to your router settings.
[http://kb.netgear.com/app/answers/detail/a_id/23851/~/what-is-wi-fi-multimedia-quality-of-service-and-how-do-i-enable-it-on-my](http://kb.netgear.com/app/answers/detail/a_id/23851/~/what-is-wi-fi-multimedia-quality-of-service-and-how-do-i-enable-it-on-my) router
research and make any changes you might need.
you may also try this..
```
echo "options rtl8723ae swenc=1" | sudo tee /etc/modprobe.d/rtl8723ae.conf
```
then please copy and paste...
```
sudo iw reg set IT
sudo sed -i 's/^REG.*=$/&IT/' /etc/default/crda
```


good luck

---

### Post by enricobe on 2016-01-04
> **Hadaka said:**
> Hi your wireless report shows..
```
#wlp8s0: disabling HT as WMM/QoS is not supported by the AP
#wlp8s0: disabling VHT as WMM/QoS is not supported by the AP
```
these are related to your router settings.
[http://kb.netgear.com/app/answers/detail/a_id/23851/~/what-is-wi-fi-multimedia-quality-of-service-and-how-do-i-enable-it-on-my](http://kb.netgear.com/app/answers/detail/a_id/23851/~/what-is-wi-fi-multimedia-quality-of-service-and-how-do-i-enable-it-on-my) router
research and make any changes you might need.
you may also try this..
```
echo "options rtl8723ae swenc=1" | sudo tee /etc/modprobe.d/rtl8723ae.conf
```
then please copy and paste...
```
sudo iw reg set IT
sudo sed -i 's/^REG.*=$/&IT/' /etc/default/crda
```

good luck

Thank you. I've disabled the QoS because internet was much more slow than now with the QoS activated. But maybe it was not set correctly. Could you suggest to me what shoud I activate?
[ATTACH=CONFIG]266526[/ATTACH]

I can't understand why only my PC is so slow with these router settings. The other PC is much more faster.
I've copied and pasted your command and I'll write here if the internet speed is improved. Thank you :D

---

### Post by Hadaka on 2016-01-04
Hi, my knowledge on QoS and WMM is very limited and i have zero
experience with that router. Here are a couple links that may give you
some additional information. Hopefully someone with more knowledge 
can advise.
[http://www.pcworld.com/article/2689995/quality-of-service-explained-how-routers-with-strong-qos-make-better-home-networks.html](http://www.pcworld.com/article/2689995/quality-of-service-explained-how-routers-with-strong-qos-make-better-home-networks.html)
 
[http://routerguide.net/how-to-adjust-optimal-wmm-settings-improving-wireless-network-speed/](http://routerguide.net/how-to-adjust-optimal-wmm-settings-improving-wireless-network-speed/)

[https://community.republicwireless.com/thread/23490](https://community.republicwireless.com/thread/23490)

---

### Post by enricobe on 2016-01-04
> **Hadaka said:**
> Hi, my knowledge on QoS and WMM is very limited and i have zero
experience with that router. Here are a couple links that may give you
some additional information. Hopefully someone with more knowledge 
can advise.
[http://www.pcworld.com/article/2689995/quality-of-service-explained-how-routers-with-strong-qos-make-better-home-networks.html](http://www.pcworld.com/article/2689995/quality-of-service-explained-how-routers-with-strong-qos-make-better-home-networks.html)
 
[http://routerguide.net/how-to-adjust-optimal-wmm-settings-improving-wireless-network-speed/](http://routerguide.net/how-to-adjust-optimal-wmm-settings-improving-wireless-network-speed/)

[https://community.republicwireless.com/thread/23490](https://community.republicwireless.com/thread/23490)

Thank you anyway. I'll try to do some tests waiting for other users ;)
I have also bought a low-cost USB wifi adapter. I just want to check if the problem is my wifi card or something else.

---

### Post by enricobe on 2016-01-06
Some updates.

If I enable the WMM service on the router, it kills my network speed (about 120 kb/s).
Enabling/disabling other options doesn't improve the network speed.

But I've seen that:
- If the PC is in my bedroom the network speed is about 400 kb/s
- If the PC is near the router the network speed is about 800 kb/s
- If the PC is in my bedroom BUT RUNNING WINDOWS the network speed is about 800 ks/s

So it seems that the wireless card, on linux, has an high package loss or low transmission quality because on Windows it works fine. I don't know if this can help.

---

