---
title: "WiFi connects but eventually disconnects"
date: 2014-07-13
forum: Networking &amp; Wireless
---

### Post by goethesf on 2014-07-13
[COLOR=#000000]Hi ...

I have a Toshiba Protege Z835-P330, which I wiped and installed 14.04. Everything went great on the install and I'm typing this post with it now.

[/COLOR][COLOR=#000000]I worked on another [thread to get my WiFi adapter unlocked]("http://ubuntuforums.org/showthread.php?t=2233052"). I now have WiFi (via USB adapter) and have successfully connected to my router. However, the connection isn't persistent and will eventually 'die'. When I say 'die', it doesn't drop the connection in Network Manager, but the network protocols die. I've opened a ping to google.com when I start up WiFi and the ping will eventually die and I know I need to restart networking to kick-start WiFi again.

I've attached the wireless script output for this setup ... any thoughts?

-goethesf

[/COLOR][ATTACH]254682[/ATTACH]

---

### Post by praseodym on 2014-07-13
> ```
IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (1) : [COLOR="#FF0000"]TKIP[/COLOR]
                        Authentication Suites (1) : PSK
```
That looks weired, WPA2 with TKIP. Change the router settings to pure WPA2-AES (CCMP). Additionally, you could change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

Is it [COLOR="#FF0000"]L[/COLOR]ubuntu?

---

### Post by goethesf on 2014-07-26
Thanks for the suggestion! I ended up solving my orig. problem [here]("http://ubuntuforums.org/showthread.php?t=2233052&page=2&p=13083309#post13083309"). All is well in my world! :)

---

