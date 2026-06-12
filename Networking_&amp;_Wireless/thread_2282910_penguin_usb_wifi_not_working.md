---
title: "penguin usb wifi not working"
date: 2015-06-17
forum: Networking &amp; Wireless
---

### Post by Richard_Schwendler on 2015-06-17
I have a desktop running 14.04 LTS server, Fios router  and a laptop running 14.04 LTS  client
works great I am using Apache2,ftp,squirrelmail  with wired internet   and wifi to laptop     also   iphones and ipads
I want to  move the desktop to the house (a/c)  from the garage 
I purchase a Penguin  USB wifi receiver  model TPE-N150USB   says "works out of the box using lunix"

software setup apt-get install wpasupplicant wireless-tools
  wpa_passphrase "FiOS-6RK0G" "...wpa .."  > /etc/wpa_supplicant.conf
 /etc/network/interface   add to file

auto wlan0
iface wlan0 static
address 192.168.1.240
wpa-driver  nl80211
wpa-conf   /etc/wpa_supplicant.conf

did ifdown wlan0  , ifup wlan0    no errors   
ping doesn't work   
debug
iwconfig      wlan0    essid off   no ac
ifconfig      wlan0     looks ok
lshw  -c net  wlan0    shows their product and my desktop ip address
dmesg    wlan0 link not ready
wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf  -Dnl80211 -dd     >   sysout
it says
read /etc/wpa_supplicant.conf
line 1 start new  network
ssid  hexdump(10)   FiOS-6RK0G
        hex numbers  67...
psk   hexdump(32)  removed
     no numbers 
prority group 0
id = 0 ssid = FiOS-6RK0G
nl80211: could not add multicast membership for vendor list event: -2 no such directory
rfkill  ...
interface  wlan0 in phy phy0
   I cut it off after 15 sec

I plugged their USBcard  into my laptop   it came up in network panel but grayed out so I can't compare
besides my laptop doesnot use wpa_supplicant or passphrase 
but it works with the internal wifi receiver


when I setup my printer,  it found  my ssid    then I hit the "wps" button on my router   it worked
This is what i expected with this card

Penguin helped to get out typo errors  but when it came to big errors they stop responding via email
out of the box to them means you don't need diskwrapper   what ever that is.
I google wpasupplicant  I found their setup proceedure but it was dated 2006
UBUNTU has 9 upgrades since then. 

how do i get this server working?
Richard

---

### Post by chili555 on 2015-06-17
> I google wpasupplicant I found their setup proceedure but it was dated 2006
UBUNTU has 9 upgrades since then. That's a big problem, isn't it? People read and follow tutorials that were perfectly fine ten years ago but that are hopelessly outdated today.

Please try this instead: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal/464552#464552)

---

### Post by Richard_Schwendler on 2015-06-18
it is working
I can now connect
Thanks
I can type on my laptop 192.168.1.240
Apache2 ubuntu                         it works

how do I change 192.168.1.240     to   myserver
I have DNS server  running     bind9
using krizna   setup

Richard

---

### Post by chili555 on 2015-06-18
> **Richard_Schwendler said:**
> it is working
I can now connect
Thanks
I can type on my laptop 192.168.1.240
Apache2 ubuntu                         it works

how do I change 192.168.1.240     to   myserver
I have DNS server  running     bind9
using krizna   setup

RichardI'm sorry, bind9 is not a subject I've studied. I suggest you start a new question and ask that specific question.

Glad it's working.

---

