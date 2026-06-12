---
title: "eth1 has disappeared...help!!!"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by friedokra on 2006-08-30
my wireless card eth1 disappeared when I tried to install my wireless drivers. what happened? here is what is says after I type "iwlist scan" into the terminal:

```
lo no wireless extensions. eth0 no wireless extensions. sit0 no wireless extensions
```



- it included eth1 up until about 15 minutes ago. I followed these bunk-*** instructions listed here- [http://www.ubuntuforums.org/showthre...ure+broadco](http://www.ubuntuforums.org/showthre...ure+broadco) m

my wireless card used to work, but today it quit and I was following the instructions in the how-to above. now my eth1 has disappeared and I am in a panic cause I have to use this notebook laptop at school tomorrow
-----------------------------------------------------------
```
sudo apt-get install ndiswrapper-utils sudo ndiswrapper -i ~/Desktop/bcmwl5.inf sudo ndiswrapper -m for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile done
```


I think this is what did the damage. Is there anyway to get my blessed eth1 back? My wireless worked fine for a while. I have a broadcom card/chip and followed the instructions in the how-to.

when I used to type "iwconfig", I would get back:

```
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid Bit Rate=1 Mb/s
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.
```

but when I was having problems I would type (in the terminal)
```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

and this would get my wireless card working like a charm. recently though, this has not been working and my eth1 card disappears from where my networks are listed. Is this a computer virus? Why would it just stop working one day and then disappear?

---

### Post by friedokra on 2006-08-30
no ideas?

---

### Post by Omnios on 2006-08-30
Found this in the wiki 
[https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=broadcomwirelessworking](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=broadcomwirelessworking)

[https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=0&value=broadcom+&context=160](https://wiki.ubuntu.com/FindPage?action=fullsearch&titlesearch=0&value=broadcom+&context=160)

---

### Post by friedokra on 2006-08-30
I tried that. that doesn't make my eth1 card appear again. and if it does, it only does temporarily. some of those instructions in the wiki are what ****ed my computer up the first time. thanks though, I'm going to look over it again.

---

