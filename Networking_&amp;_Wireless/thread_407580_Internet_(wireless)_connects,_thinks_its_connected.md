---
title: "Internet (wireless) connects, thinks its connected, but won't transfer data"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by alex_anthony on 2007-04-12
I'm running my laptop dual booting. Internet is working fine in windows but not ubuntu. Internet stopped randomly, not just after an update or anything. It ran fine after my most recent update, but stopped abruptly. According to network manager, I'm still connected to the wireless network. It claims that 2 or 3 packets of data have been transferred, but I can't surf the internet.

With any suggestions, bare with me as I am writing this on Windows, so would need to reboot.

(Also, my sound stopped working in ubuntu after last update (fine in windows). Any ideas?)

---

### Post by happy-and-lost on 2007-04-12
What hardwae are you using? (What's the model of your wireless card?)

---

### Post by alex_anthony on 2007-04-12
on a dell inspiron 1300 laptop with the broadcom wireless card. intel pro 1370 (use broadcom drivers) 
I've had wireless working for months already (ndiswrapper) and it was working fine up until it stopped

---

### Post by ittiam on 2007-04-12
Well I dont know but this is just a suggestion. Since you say that your network manager says that u r connected and it has transferred couple of packets, I am suggesting this ...try disabling ipv6! I also did read that it was working for you before but just a suggestion.

If this doesnt work, kindly post the output of the following,

> sudo iwconfig wlan0 essid <your_network_id> (wlan0 is the wireless interface, so if ur wifi interface is eth0 or eth1..just substitute it for wlan0)
iwconfig
sudo dhclient wlan0

---

### Post by alex_anthony on 2007-04-12
ipv6 had no effect but thanks for the suggestion

iwconfig
eth1      IEEE 802.11g  ESSID:"********"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:**:**:**   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-70 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


dhclient eth1

There is already a pid file /var/run/dhclient.pid with pid 5631
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:**:**:**
Sending on   LPF/eth1/00:14:a5:**:**:**
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.3 -- renewal in 35933 seconds.


any ideas now?

---

### Post by ittiam on 2007-04-12
well you are able to connect to the access point and u also get an ip from it! That looks fine. Then only thing i can think of is ipv6 being enabled in ur system. But since you already said you have checked that. Sorry i am out of suggestions!

---

### Post by alex_anthony on 2007-04-13
thanks anyway

also, I tried using a wired connection (same router) but still wouldn't transfer, so must conclude problem isn't with the wireless transmission

found out that somehow I have received 6225 packets of data and sent 15, but I don't know at all what data this is.

---

### Post by alex_anthony on 2007-04-13
BREAKTHROUGH
found it is a serious DNS fault, just connected to google through its IP, now just trying to get the DNS Server going properly

Anyone know any of the details (AOL UK)?

Really stuck on getting DNS to work properly! Please Help!

---

### Post by grkravi on 2007-04-13
I am also having the same problem...I updated my Dell Inspiron 5160 Edgy to kernel 2.6.20.6 and after this kernel update, i lost access to internet.
Switched back to 2.6.17.

---

### Post by alex_anthony on 2007-04-13
my kernel is 2.6.17 and has never been to 2.6.20. Any other ideas?

---

### Post by alex_anthony on 2007-04-13
(bump) 
Please someone! 
I really need help, I'm having to live with a ridiculously slow Windows XP, compared to my flying ubuntu. 
Ideas for getting DNS to work?

---

### Post by alex_anthony on 2007-04-14
(bump again)
Please Help me!

---

### Post by TimDuncan on 2007-04-14
Try adding a DNS server in your resolv.conf file, found in /etc

the syntax is 

namespace xxx.xxx.xxx.xxx

where xxx is the IP provided by your ISP for DNS

I had this problem also, you'll also have to find a way for that file not to be overwritten automatically.

It's something to do with the router incorrectly forwarding DNS to linux, because it works in windows..

let me know how you go

Tim

---

### Post by Thingymebob on 2007-04-18
> I had this problem also, you'll also have to find a way for that file not to be overwritten automatically.

You'll need to edit /etc/dhcp3/dhclient.conf to stop resolv.conf being overwritten:
Add a line that reads

prepend domain-name-servers xxx.xxx.xxx.xxx;

Where xxx.xxx.xxx.xxx is the DNS IP Provided by your ISP. You can add more than one by seperating them with a comma

---

### Post by alex_anthony on 2007-04-18
I have added my real DNS settings but I still can't access a site. I reboot and its still in /etc/resolv.conf, along with the address of my router added aswell...
Even when I have it in resolv.conf alone, it won't work... any ideas why not?
I'm thinking I should just upgrade to Feisty (complete reinstall) tomorrow and see what happens then.

---

### Post by flukierdonut on 2007-07-18
Im having the same problem...i have tried everything i could think of but have still had no luck. i really dont want to redo my installation but its the only solution i can think of.

---

### Post by Thingymebob on 2007-07-18
alex_anthony, flukierdonut
Have you done the ipV6 stuff?

In firefox address type:
about:config

then in the filter type ipv6

double click the value
network.dns.disableipv6

---

### Post by alex_anthony on 2007-07-22
flukierdonut,
do you use a router?
Any idea where your dns servers are pointing

---

