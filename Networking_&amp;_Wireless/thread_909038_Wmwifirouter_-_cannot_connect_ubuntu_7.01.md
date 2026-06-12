---
title: "Wmwifirouter - cannot connect ubuntu 7.01"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by antodena on 2008-09-03
Dear All,

in need help about a wireless connection, i've tried to search in your forums without findin any helpful thread...

the fact is that i own a smartphone SAMSUNG i600 that i use as an access point with a great piece of software called WMWIFIROUTER... this program use the wifi built-in connection to broadcast the internet creating a wifi network.

this software can manage to act as a full operational router, in fact i usually use it with extreme success on my windows vista and xbox360, with an ad-hoc connection supported by DHCP function and no security settings. (WEP-WPA...)

the problem is that my UBUNTU 7.01 despite the fact it recognize the network (it appears in the list, clicking on the icon on the upper/left bar) doesn't accomplish to connect... it show 2 round symbols spinning and it write something about “trying to connect to wmwifirouter”
then suddently stop to try and return to the idle state.
I hope that someone can help me connect with this wifi network, because in my house I got no cabled internet connection… I lack the internet on my ubuntubox, in this way I could totally substitute and finally quit using Microsoft Vista…
Waiting for your help!
Regards

dna

---

### Post by antodena on 2008-09-03
can i make a bump? i'm afraid that no one can read my post...

if i broke some rules feel free to close my post please.

thanks.


dna

---

### Post by shankscomp on 2008-09-09
I got WMWifiRouter also, running Ubuntu 8.04, and guess what... Same damn issue.  If anyone has a solution to help us, that would be great.  I also wrote a script to help, but it doesn't seem to help at all.  Below is the code from my script.

Any Suggestions???

----------------------------------

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo ifconfig wlan0 down
sudo rm -r -f /home/tim/.gconf/system/networking/wireless/networks/WMWifiRouter
sudo /etc/dbus-1/event.d/25NetworkManager start
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid 'WMWifiRouter'
sudo iwconfig wlan0 mode ad-hoc
sudo iwconfig wlan0 channel 11
sudo dhclient wlan0

---

### Post by trugate on 2008-09-24
bump, this probably has to do with the wireless drivers from the limited experience I have with linux and from what I've read.  I do know that using windows drivers through ndiswrapper that it solves most of these issues.

I think the root of the problem is that WMWifiRouter creates an ad-hoc network, which comes back to the linux driver to work with.  The reason I came to this conclusion is that I'm using 8.04 on my dell d505 laptop and posting this through WMWifiRouter right now...So I know it can work.

It'd be great to figure out what's wrong with the drivers so someone could update/fix the ad-hoc issue.

If I'm right anyways... anyone care to verify?

---

### Post by superprash2003 on 2008-09-25
try this.. may work.. first try to find out which interface is your wifi interface. then set it to adhoc mode first by typing the following
1)sudo ifconfig eth1 down
2)sudo iwconfig eth1 mode ad-hoc
3)sudo iwconfig eth1 essid 'wifinetworkname' 
4)sudo ifconfig eth1 up

presuming that eth1 is the wifi interface.. have you set a WEP or WPA for the wifi network you setup on your phone?

---

### Post by apienk01 on 2009-09-02
A bump for future reference. I managed to make WMWifiRouter work with Ubuntu. The problem turned out to be the wlan card driver, namely madwifi (for Atheros cards). I just changed this proprietary driver to the GPL-ed ath5k (using proprietary driver manager in system/administration menu; just 'turn off' madwifi) which works great. One extra step was un-blacklisting the ath5k driver in /etc/modprobe.d/madwifi.conf as described [here]("https://bugs.launchpad.net/ubuntu/+source/madwifi-tools/+bug/359820"), because otherwise the driver would not load itself on boot.

---

