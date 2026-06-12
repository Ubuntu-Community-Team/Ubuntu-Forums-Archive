---
title: "Wifi Adapter doesn't recognize all networks (XBMCbuntu)"
date: 2015-01-10
forum: Networking &amp; Wireless
---

### Post by michael244 on 2015-01-10
Hi,

I'm running XBMCbuntu and up to yesterday the network adapter worked perfectly. Unfortunately this distribution doesn't provide me with nice GUI Tools and all I have is a default Network Manager where I can enter some data but cannot see if a connection was actually established. I use firefox to see if it works.
Today I had to change my router setup because for some reason the password was no longer accepted from various iPhones. In this process I set a different password and changed the SSID type to hidden.

I can connect to my default Wi-Fi "FM24" under windows 7 (same hardware) but cannot get it to work in linux. In Linux I can however connect to my guest network "FM24G" from which I can access the internet but not my servers.
Can anyone here see in my script output why my system behaves like that?

(or is there a packet recommendation for a nicer GUI application?)
[ATTACH=CONFIG]259142[/ATTACH]

---

### Post by praseodym on 2015-01-10
Deactivate the hardware encryption of the driver

```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
and change the encryption mode to pure WPA2-AES (CCMP) and to a fixed channel, check the router manual

---

### Post by chili555 on 2015-01-10
At the outset, I will preface my comments by telling you that Network Manager and many Linux drivers are troubled by hidden networks. I know a fair bit about wireless networking and my network is not hidden because I know that the tools that serious hackers use easily show all networks, hidden or not. A hidden network probably only helps with the neighborhood kid who imagines he knows hacking because he discovered Kismet. In that case, a network protected with WPA2-AES; not TKIP and certainly not WPA-WPA2 mixed mode, plus a strong password, is plenty of protection. The NSA thinks so! [https://en.wikipedia.org/wiki/Advanced_Encryption_Standard](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

Nonetheless, let's see if we can connect to your hidden network. First, I suggest you click the Network Manager icon, select 'Edit Connections,' and under Wifi, delete all networks. Then, in a terminal, restart NM:```
sudo service network-manager restart
```After it restarts, NM should pop up a balloon to tell you that networks are available. Ignore it.

Click the NM icon and select 'Connect to Hidden Wi-Fi Network..." Fill in your details and see if it connects.

If not, we will try another technique.

---

