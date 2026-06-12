---
title: "kismet working!.... now airodump-ng quits after some time"
date: 2008-01-20
forum: Networking &amp; Wireless
---

### Post by thefatmoop on 2008-01-20
alright i couldn't find a post with really any info on this... Well i updated my ipw3945 with a driver that supports packet injection. I was able to get kismet working nearly perfectly and now i'm having a problem with airodump-ng 
after i start airodump-ng doing a monitor it will work for about 12 seconds and quit working, well applet-nm (wifi network app?) will join my network and airodump-ng will say something like "read failed: network is down" how do i keep the wifi card in monitor mode? it keeps going out. even if i kill the applet-nm it connects to the network =/ 

here is the error 

 CH  6 ][ Elapsed: 4 s ][ 2008-01-19 23:53 
                                                                               
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ES
                                                                               
 00:01:******   -1   0        0        2    0   6  -1  OPN              <
 00:E0:******   -1   0        0       11    0   6  -1  OPN              <
                                                                               
 BSSID              STATION            PWR  Lost  Packets  Probes              
                                                                               
 00:01:F4:*****  00:0C:********   -1     0        2                      
 00:E0:63:*****  00:15:********   -1     1       11                      
read failed: Network is down
euphoria@Euphoria:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.167.99) 56(84) bytes of data.
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=1 ttl=244 time=168 ms
64 bytes from py-in-f99.google.com (64.233.167.99): icmp_seq=2 ttl=244 time=114 ms

---

### Post by pytheas22 on 2008-01-20
How are you putting your card in monitor mode?  Are you using iwconfig or airmon-ng first, or just trying to start it on airodump immediately?  Also are you killing the NM daemon as well as NM itself?  And do you have any other software running that could be interfering with it?  Did you install the patch to support packet injection for your card (I believe that none of the Ubuntu drivers support injection out-of-the-box)?  Can you inject packets (using aireplay)?

If you did all the things above, it could just be that your card does not support airodump well--strange that kismet would work and not airodump, but who knows...I had similar behavior trying to use a Broadcom card; it would work for a few seconds and then crash.  Maybe the aircrack forums could help you if no one here does.  In any case, kismet should allow you to do the same thing airodump would, wouldn't it?  Or Ethereal/Wireshark would also let you sniff packets.

---

### Post by thefatmoop on 2008-01-20
yes i'm using new drivers that supposedly support packet injection 
i believe i used 
sudo iwconfig eth1 mode monitor
sudo kismet
sudo airodump-ng -c 6 -w data ......etc eth1  

oh i just killed the applet >< 
i'll try killing the daemon tomorrow.

another question ~ here is the network environment ~

my school associates user accounts (1 gig a day bandwidth ><) with mac addresses to keep track of computers. well the server assigns people their ip address by their mac address... very convienent cause i never need to hunt anyone down when i need to test something... anyway ubuntu and vista are both using dhcp, well ubuntu got a different ip than vista, but obviously same mac address. why did ubuntu get a different ip if it's on dhcp? the mac is the same!

well i'm having problems with macchanger >< it's able to swap the mac address, but for some reason  i get the wrong ip, i spoofed my desktop and it still brought me to the computer registration page. i've tried "sudo ifconfig eth1 down" "sudo macchanger --mac=desktop mac eth1" "sudo ifconfig eth1 up" and i've tried "sudo macchanger --mac=desktop mac eth1" "sudo ifconfig eth1 down" "sudo ifconfig eth1 up"

sudo macchanger --mac=desktop mac eth1
sudo macchanger -s 
*macchanger will show the desktop mac*

and if i do ifconfig the eth1 mac address is the desktop address. 
also, the desktop was off when i joined with its' mac

it works when i use TMAC in windows xp/vista and it works when i use macchanger in backtrack 2 or 3 
i don't know any student who could even begin to help/make suggestions and if i asked tech support they would probably fine / put me on academic probation lol

well it's almost 3am gtg wake up in 4 hours. sorry i wrote this post and it looks like a 6 year old wrote it

---

### Post by hahahan on 2008-01-20
I had problems too when using kismet and airodump-ng. After using kismet resetting the NIC (ifconfig NIC down, unplug for >4 sec and ifconfig NIC up again) helped.
Are you using the latest version of the aircrack-ng suite?
About the spoofing: After spoofing the mac config the IP and gw manualy :
ifconfig NIC xxx.xxx.xxx.xxx
route add default gw xxx.xxx.xxx.xxx

Good luck.

---

### Post by tturrisi on 2008-01-20
Kismet will work because the newer version (what you are using) contains code to kill the network-manager daemon.  Aircrack won't work unless you kill the network-manager daemon.  Best solution is to uninstall network-manager and its daemon completely and just use the good old built in reliable methods of connecting to wlans.

---

### Post by thefatmoop on 2008-01-20
Alright so on the kismet, yeah looks like kismet is automatically putting the wifi card in monitor mode, and airodump works, the instant they both quit working is when the nm-applet starts rejoining the network

how do i kill the daemon? whats the process name? / how would i find how to uninstall? 

and about the spoofing, well if you join the network and you aren't registered it takes you to a completley different network 172.x.x.x (registered starts with 10.x.x.x) and a different mask cause yeah i tried to manually set my ip to the correct one

---

### Post by tturrisi on 2008-01-20
> **thefatmoop said:**
> Alright so on the kismet, yeah looks like kismet is automatically putting the wifi card in monitor mode, and airodump works, the instant they both quit working is when the nm-applet starts rejoining the network

how do i kill the daemon? whats the process name? / how would i find how to uninstall? 

and about the spoofing, well if you join the network and you aren't registered it takes you to a completley different network 172.x.x.x (registered starts with 10.x.x.x) and a different mask cause yeah i tried to manually set my ip to the correct one

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

permanently disable:
create these files with just the word "exit". (no quotes)
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

---

### Post by thefatmoop on 2008-01-20
yeah that did it awesome thanks 

```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

permanently disable:
create these files with just the word "exit". (no quotes)
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher
```

everything is working perfectly, although i havent tried packet injection yet >< lol well drivers supposedly support it

---

### Post by tturrisi on 2008-01-22
test injection:

put adapter in rfmon mode

aireplay-ng -9 wlan0 
(where wlan0 = your interface; ath0, eth0, etc.)

---

### Post by troutbum13 on 2008-02-05
$sudo killall NetworkManager
$sudo killall NetworkManagerDispatcher

also work, when you want to bring NM back up

$sudo NetworkManager
$sudo NetworkManagerDispatcher


My question, I have three NIC,
eth0=wired
wlan0=wireless
eth2=wireless

I want to exclude eth2 from network manager so that it does not constantly kick the card out of monitor mode?? That way I can remain online while monitoring....

Anyone have any ideas?

---

### Post by ubutufan on 2008-02-05
I wonder if you have tried enabling the monitor mode via
sudo airmon-ng start eth1 or whatever your wireless is?

---

### Post by troutbum13 on 2008-02-05
yep, that is how I enable monitor mode, and then I can confirm through iwconfig. 

Airodump-ng works great capturing ivs, until it doesn't. Network Manager seems to kick the nic back to managed mode. 

when I $killall NetworkMonitor this probelm goes away but so does my wired connection... this is stated to be a known ubuntu problem in the aircrack wiki... I would like to exclude the monitoring NIC from being managed :)

---

### Post by ubutufan on 2008-02-06
I have removed the NM and I am using Wicd instead.
You might want to give it a try at

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

I never get any kind of interruptions from wicd

---

