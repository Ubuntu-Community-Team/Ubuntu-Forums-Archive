---
title: "Wireless on Toshiba A20 laptop"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by TaylorHelferty on 2007-03-23
I recently installed Ubuntu on my Toshiba A20 laptop and everything is working fine. The wireless card even picks up the signal, but it doesn't actually connect. I choose my SSID from the list, which if finds (it even picked up my neighbours signal), I put in my WEP key and whether I choose DHCP or Static IP, it shows that the signal is great and wireless connection ath0 is active and running, but when I open any internet utility it says I'm not connected. Same thing when I connect it using ethernet. Any ideas on how to fix the problem?

Would the Gateway address have anything to do with this? When I choose Static IP, I put in my IP and subnet, but I don't know where to find my gateway, so I leave that blank. Although it still says connected and good signal, maybe I need to fill in gateway? I dunno. Any help would be appreciated.

---

### Post by ffxr on 2007-03-23
the gateway is the address of your router..

usually but not always 192.168.1.0.1 or 192.168.1.1 or check your routers docs..

try ping them and see if you get a response and use whatever one responds as your gateway..

---

### Post by chili555 on 2007-03-23
Please let us see:```
sudo iwconfig
sudo iwlist ath0 scan
```Please obscure only 2/3 of your WEP key so we may study it's structure. We'll get you going.

---

### Post by ffxr on 2007-03-23
youll need to put your isp's DNS server addresses @ the network control panel as well.. 

or use 208.67.222.222 & 208.67.220.220 courtesy of opendns: [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by TaylorHelferty on 2007-03-23
chili555:

This is what I got when I did those two commands:

taylor@taylor-laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"helferty20"
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:13:A3:5F:0E:20
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:3D02-1264-E**C-38AD-D6**-***-**   Security mode:restricted
          Power Management:off
          Link Quality=65/94  Signal level=-30 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

taylor@taylor-laptop:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:13:A3:5F:0E:20
                    ESSID:"helferty20"
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Quality=67/94  Signal level=-28 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200

Any ideas? And as for that DNS server address, if you could point me into the direction of where to find those settings? I'm still new to networking and wireless, so I don't really understand all of the terminology/settings yet. Still learning. Those gateway addresses won't work, and I couldn't find mine anywhere I looked.

Edit: I found the DNS address options and put those in. It didn't work. Not only that, it knocked out my entire internet connection on all computers. Got that repaired though. Maybe I put it in the wrong spot? I dunno. Again, new to all this networking stuff.

---

### Post by chili555 on 2007-03-24
First, we will use a text editor to amend a file. Open a terminal and do:```
sudo gedit /etc/resolv.conf
```Make sure it looks like this:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```Save (very important!) and close gedit.

Next, let's issue two commands:```
sudo iwconfig ath0 rate auto
sudo dhclient ath0
```We will either get an IP address from the router....or not. If not, let's try another two commands:```
sudo iwconfig ath0 key open
sudo dhclient ath0
```Post back and let us know.

---

### Post by TaylorHelferty on 2007-03-25
Here's what I got with the sudo dhclient ath0:

DHCPOFFER from 192.168.2.1
DHCPREQUEST from ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.12 - - renewal in 104501 seconds


Now, I know my router is 2.12, so would I put that one in my IP address under Network settings, or the 2.1 which I used before?

As an side note: whenever I turn on my laptop, my router just quits. Like, all the right lights stay on, but I lose connection from the internet until I repair the connection. It only takes a few seconds, but it's quite the inconvenience. Any ideas on why that may be while we're working on this?

---

### Post by chili555 on 2007-03-26
```
DHCPOFFER from 192.168.2.1
DHCPREQUEST from ath0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.12 - - renewal in 104501 seconds

```Wonderful! You are connected.> Now, I know my router is 2.12, so would I put that one in my IP address under Network settings, or the 2.1 which I used before?Nope, your router is 192.168.2.1 and it's DHCP server has handed out an IP address to your laptop: 192.168.2.12.

I would just leave your network settings as DHCP. No need for a static IP, as far as I can see.

---

### Post by TaylorHelferty on 2007-03-26
That worked! It didn't work after i tried it the first time, but then I changed it to DHCP and it connected fine. Thanks for all the help! I really appreciate it!

---

### Post by joneil1000 on 2007-03-26
Hi;
     Although you got your connection going, i wanted to make another comment.  I have a Toshiba A10 laptop - the one just before yours.  :)    Brand new it came loaded with XP, and recently I wiped XP completely away and installed Ver 6.10

    Anyhow, the built in wireless card in my A10, even under windows, was always very poor.  It had hard time picking up, detecting or holding connections with any wireless network.  Under Ubuntu it was no better.

    So my solution was to turn off the wireless card (there is an actual hardware switch on the front of the machine to do this), then at a local discount computer store, I bought a brand new Belkin PCI wireless card and inserted it in.   Ran the drivers - argh - forget the name - starts with "N" (I read the name in the manual), then loaded up the program "WiFi-radar" and boom - instant connect, works perfectly.

    so my point is, especially for those who have a A10 Toshiba like  me, see thsi headline, are looking for help and are having problems, sometimes it's not the software, sometimes it really is a hardware issue - hardware that just doesn't work right.   Even if I never installed Ubuntu and stayed with win XP, I am 99.9% certain I would have still installed a wireless PCI card

joe

---

