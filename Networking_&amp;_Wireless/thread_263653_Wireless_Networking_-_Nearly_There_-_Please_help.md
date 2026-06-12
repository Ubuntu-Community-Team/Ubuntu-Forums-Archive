---
title: "Wireless Networking - Nearly There - Please help"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by puppy on 2006-09-23
Hi everyone - I am sure that I am nearly there with getting connected wirelessly. Drivers are installed etc but I'm a bit lost from there - there's lots of information about scanning for networks but not much about how you actually connect to a network???  

This is the output of "iwlist wlan0 scan":

wlan0     Scan completed :
          Cell 01 - Address: 00:11:50:EB:88:C2
                    ESSID:"Darnassus"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:0/100  Signal level:-63 dBm  Noise level:-256 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

I've turned off encryption for the moment, so that doesn't introduce any difficulties, but what do I do now? I can see my router, how do I connect to it please?

Thanks for any help

---

### Post by spd106 on 2006-09-23
It should just be a simple matter of setting the essid to the same as the AP. Then you will see iwconfig show the same essid and the Access Point's MAC address to indicate that you have associated with an AP. The card should automatically set the correct frequency etc.

If you aren't associated with an AP, iwconfig will typically show AP:off/any.

---

### Post by puppy on 2006-09-23
"It should just be a simple matter of setting the essid to the same as the AP. Then you will see iwconfig show the same essid and the Access Point's MAC address to indicate that you have associated with an AP. The card should automatically set the correct frequency etc."


Sorry, you've completely lost me - how do I go about "setting the essid..." etc etc? Sorry I am still a complete noob when it comes to networking   :rolleyes:

---

### Post by spd106 on 2006-09-23
This is basically the network name, so you can set it through the Network-Admin applet in the System menu. 


Alternatively while we're at the terminal **sudo iwconfig wlan0 essid *insert name here*** will work, but it won't be persistent. So editing the /etc/network/interfaces file by making it look something like this will allow it work on boot.
```
iface wlan0 inet dhcp
wireless-essid netgear
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
```.

If your using Network-Manager or Wifi-Radar to manage the connection then it should be straight forward.

---

### Post by puppy on 2006-09-23
OMG :shock: 

It works!! I have wireless internet :D 

Thankyou, you are a :KS 

Pups

---

### Post by happy-and-lost on 2006-09-23
To make life easier...

```
sudo apt-get install wifi-radar
```

---

### Post by puppy on 2006-09-23
Thanks for this link, I just found out about wifi radar - I can't find any posts about how to successfully enable WPA with it however, which is my next problem - I don't want to use an unsecured network :rolleyes:

---

### Post by happy-and-lost on 2006-09-23
WPA? Hehe, you don't really need to worry about security in Linux :)

---

### Post by puppy on 2006-09-23
I do if someone is packet-sniffing the stream, or wants to piggyback my connection... right??

---

### Post by happy-and-lost on 2006-09-23
Oh right. Sorry, I live out in the middle of nowhere... there's no-one near enough to my connection to even attempt to piggyback mine!

Does your router have WPA enabled?

EDIT: Most routers have a router manager, which can be accessed through any web browser via [http://192.168.1.1](http://192.168.1.1) (Default user/pass is usually admin/admin)

---

### Post by puppy on 2006-09-23
It's disabled at the moment, otherwise I can't connect to it in linux  :rolleyes: 

I want to enable WPA (I live in a very built-up city area, in fact I can sniff three other networks from here lol) but as I said, although it looks like a useful program, I can't find any successful how-tos to enable wifi-radar to use WPA... well at least I have a connection :)

---

### Post by puppy on 2006-09-23
OK, we're going to get there...  :D 

Right you can change the RTS and Fragmentation settings on the card with the following commands: (high default RTS and Fragmentation settings are what caused the high pings for me in Windoze)

The commands are:

sudo iwconfig wlan0 [<<< substitute the reference for your card] rts 256  [<<< which is the lowest setting]  

and

sudo iwconfig wlan0 [<<< substitute the reference for your card] frag 256
[<<< which is the lowest setting]

Job done!

Pings are now (wireless is behind one wall about 10 feet away):

64 bytes from 192.168.2.1: icmp_seq=64 ttl=64 time=0.858 ms
64 bytes from 192.168.2.1: icmp_seq=65 ttl=64 time=0.815 ms
64 bytes from 192.168.2.1: icmp_seq=66 ttl=64 time=0.860 ms
64 bytes from 192.168.2.1: icmp_seq=67 ttl=64 time=0.843 ms
64 bytes from 192.168.2.1: icmp_seq=68 ttl=64 time=0.824 ms

:D

EDIT: I understand that different setups benefit from different settings so you might find that 256 for both are not the best solution for you, but at least now you can experiment to improve your performance ;)   Avaialble settings are between 256 and 2346

---

### Post by spd106 on 2006-09-24
Network Manager has WPA support built in and is easy to configure. The only problem is that it doesn't work for everyone yet. Wifi-Radar doesn't do WPA yet and conflicts with NM. Here's a useful setup guide [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager).

---

