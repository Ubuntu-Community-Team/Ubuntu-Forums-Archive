---
title: "Creating an ad-hoc wireless network"
date: 2007-06-04
forum: Networking &amp; Wireless
---

### Post by qscomputing on 2007-06-04
Hi,

I often meet up with a small group to play network games on our laptops. In Windows, we are able to create an ad-hoc wireless network between the laptops, however we would of course prefer to use Ubuntu. We have confirmed that the games we want to play work in Wine, the problem now is setting up the network.

We tried clicking the network icon on the top panel on one of the computers and choosing Create New Wireless Network. After creating a wireless network, we clicked the same icon on another laptop and selected to join the network we just created - but this didn't work.

So, how can I connect two or more laptops together using a wireless network without using a router?

Also, once I've made the connection, I would like to be able to use ping to check that the network has been established... but what is the address I have to ping? Will the computer's name work, or do I need to find an IP address for each machine somehow?

I have tried searching the wiki and forums but have found nothing yet.

Thanks,
  QS.

---

### Post by spd106 on 2007-06-05
The use of ad-hoc mode depends on the wifi adaptor you have and the driver you are using.

For Broadcom cards, the bcm43xx won't do ad-hoc mode on Feisty, but it will work with ndiswrapper.

For Atheros cards, the madwifi driver needs a VAP to be created in ad-hoc mode. The procedure to this is on the madwifi.org website and the madwifi-tools package (universe repo) will be needed.

As far as I know most of the other cards will switch to adhoc mode through network manager as you have tried. To check that it's working open a terminal and run iwconfig. This should say the the interface is in adhoc mode rather than managed mode. You will also see a cell address, this must be the same on all PCs for you to be on the same network.

Avahi-autoip should assign you an IP address in the link-local address space (169.254.x.x) and you should be able to ping other PCs by these addresses or by hostname.local. 
eg if your friend's PC's hostname was fred-laptop, then you would ping it with ```
ping fred-laptop.local
```

Sometimes it just doesn't seem to work, in this case you may want to disable network manager and configure it through iwconfig alone. The commands you will need are as follows
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
```
Then assuming you would call the adhoc network 'tempnet'
```
sudo ifdown wlan0
```
```
sudo iwconfig wlan0 mode ad-hoc
```
```
sudo iwconfig essid tempnet
```
maybe add a WEP encryption key
```
sudo iwconfig wlan0 key 1234567890
```
Since you are doing this manually, you will have to make up an address
```
sudo ifconfig wlan0 169.254.34.2 up 
```



There are other posts on this in the forum, though it would be nice if the information could be collated into a wiki page.

---

### Post by spd106 on 2007-06-06
I've written this up as a community doc in the wiki.
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

As I only have access to Broadcom and Atheros cards these are the only ones I can comment on directly.

If anyone has any changes they want to make, please go ahead. I will try to maintain the page and flesh it out as I go along.

---

### Post by darkfox on 2007-06-29
Hey  spd103 - thanks for a great HowTo on ad hoc wireless networking.

I have an atheros based pcmcia card (Netgear WG511T).   When I try either of the 2 methods you mention (autocreation or wlanconfig) all input devices (keyboard and mousepad) stop working after about 2 seconds.  I can't tell if anything else stops working, obviously, becuase my input devices are down ;)

Any idea what may be wrong, or where I should start to look?

---

### Post by darkfox on 2007-07-03
I have added my experiences to the bottom of [the wiki page]("https://help.ubuntu.com/community/WifiDocs/Adhoc").  If you use an Atheros card and are interested in connecting wirelessly to a Windows ad-hoc (peer to peer) network to make use of another machine's internet connection, example #1 describes one way of doing it.

---

