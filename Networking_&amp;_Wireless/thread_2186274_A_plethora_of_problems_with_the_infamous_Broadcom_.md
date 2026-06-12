---
title: "A plethora of problems with the infamous Broadcom wifi drivers."
date: 2013-11-06
forum: Networking &amp; Wireless
---

### Post by jstratta on 2013-11-06
Where to start....  We have multiple types of computers that do not have the wireless preinstalled when we install Ubuntu, they all are Broadcom variants. Most have Ubuntu 12.04 on them. Some have Lubuntu or Debian but still do not work. I have tried to follow the guide here ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) and many fall under the "wl" category. When we go to add from additional drivers they start to install then we get a black screen with mostly gibberish text and that jockey backend crashed we reboot it and the driver is not installed. I have tried many other "solutions" on this very site and elsewhere on the internet but nothing has worked on any of our models yet. Some are even macs too. Some of these answers are too complicated, not well enough explained, or do not work. I was able to figure out the exact model and chip of all the wireless cards but the above guide only crashes all of them or just doesn't work. Can someone please provide a more definitive answer. If we can only work with even one model so we can get an idea this would be very helpful. Thank you in advance.

---

### Post by Hadaka on 2013-11-06
Hi, how may machines total? are they currently "networked" together?
and THE most important question...can you access the internet with the
ethernet cable? getting one machine going will not get them all going, It will
be different for each broadcom card type and computer type.
On the MAC machines i would suggest this..
from a Wired connection conneted to the internet..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
the other machines will require a query as to card type.
please post..for each machine..the output of.
```
lspci -nnk | grep -iA3 net
```
thanks.

---

### Post by jstratta on 2013-11-07
Thank you i will try the purge commands but there are many different types of computers. Several different types of Macs and HP Mini 1000 and several other PC types off the top of my head. I am not at work today but i would be here all day trying to post all of the different types. I would like to just at least figure out 1 or 2 in one scenario and try to go from there

---

### Post by wildmanne39 on 2013-11-07
Please keep on computer per thread or make sure to only work with one at a time so as not to confuse people.
Thanks

---

### Post by jstratta on 2013-11-08
I am certainly not going to go through all of them here at once and i will specify whatever model it is that i am talking about.

---

### Post by jstratta on 2013-11-08
OK, regarding this particular MAC it is a IMAC A5 with the BCM4321 card. It does have an Ethernet port so i will try your first suggestion, once this is working i would like to move onto another machine.  UPDATE: I followed your instructions, it recognizes the wifi adapter now in the network manager. However it does not seem to scan for wireless networks, no available networks show up in the list but if i enter the name of the network manually and with the password it is able to connect. So how do i get it to scan? I have also rebooted,

---

### Post by Hadaka on 2013-11-08
Hi, to scan please do..
```
sudo iwlist wlan0 scan
```
* or eth1 or whatever it is.
also please post the output of..
```
cat etc/network/interfaces
```
this must be done on EVERY machine..to see HOW
you are managing your network,with the /etc/network file or network manager.
There are other things we need to cover,but for now..let's see what you have.
thanks.

---

### Post by jstratta on 2013-11-08
Doing the scan once returned  

"No results" 

 I ran it a second time and i got output, i would like to not have to do that every time i want to connect to to a wifi network.  

```
root@iMac:~# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:13:AB:D2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm 
                    Encryption key:on
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023282297bf
                    Extra: Last beacon: 16708ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

root@iMac:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by Hadaka on 2013-11-08
ok, please post
```
cat /etc/network/interfaces
```
its important that you read and post the commands
i request to avoid confusion with multiple machines.
thanks.

---

### Post by jstratta on 2013-11-08
I did read. I posted the commands you requested. Its at the bottom of the code.

---

### Post by Hadaka on 2013-11-08
thanks. Please do..
```
sudo service network-manager restart
```
then configure like the attached for your connection
[ATTACH=CONFIG]247669[/ATTACH]

---

### Post by jstratta on 2013-11-08
I have done the service restart, but i do not think this will solve my problem. This will only auto connect me to the same network. I want the ability for the manager in the upper right corner to scan for networks and display them automatically. These computers are going to be for end users.

---

### Post by Hadaka on 2013-11-08
ok, uncheck "Connect Automatically"  with network mgr.
then your end user can select which network to connect to..
or you can configure the connection "ssid" under the security tab 
with the network mgr. If the connection is not set up as connect auto.
then it wont remember any passphrase or security code to connet.

---

### Post by Hadaka on 2013-11-08
ok, uncheck "Connect Automatically"  with network mgr.
then your end user can select which network to connect to..
or you can configure the connection "ssid" under the security tab 
with the network mgr.

---

### Post by jstratta on 2013-11-11
Are you not understanding what i am posting? Networks do not show up in the manager, i have to manually connect to everything. How do i make it so this does not happen? How do i make it scan on its own?

---

### Post by jstratta on 2013-11-13
Still need help someone please respond.

---

### Post by jstratta on 2013-11-15
bump

---

### Post by Hadaka on 2013-11-15
Hi, i was out of town a couple days,let's take a look at
a couple things. Is this still the MAC machine?
and please post the output of..
```
lspci -n | grep 0280
lsmod
cat /etc/network/interfaces
```
thanks.

---

### Post by jstratta on 2013-11-18
Maybe we can go back to that, but since i couldnt get an answer soon enough i have moved onto a new machine. I do not blame you but as a refurbisher i couldn't wait. I have now moved onto a hp mini which i made a new post about here [http://ubuntuforums.org/showthread.php?t=2188711&p=12851353#post12851353](http://ubuntuforums.org/showthread.php?t=2188711&p=12851353#post12851353)

---

### Post by Hadaka on 2013-11-18
Thanks for the update,since you have "moved on" please do
not leave open threads,mark this thread solved. thanks.
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by jstratta on 2013-11-18
Well once i solve the mini cant i just come back here for mac and others?

---

### Post by Iowan on 2013-11-18
> **jstratta said:**
> Well once i solve the mini cant i just come back here for mac and others?
"Here" being the forums? Certainly.
This thread? Generally, one topic/thread is appropriate. It's easier to focus on a single problem, and the title can draw assistance.

---

### Post by jstratta on 2013-11-18
By here i meant this thread. And as i said i made a new one because i was not receiving help, now i am so once i finish my other problem that is in a separate thread wouldn't it make more sense to revive this instead of making a new one while also inaccurately labeling it as solved.

---

### Post by Iowan on 2013-11-18
I might recommend reading the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"). If you post a Mac problem 25+ posts into a "Broadcom wifi driver" thread, it will likely go unnoticed. Then you'll start yet anther thread anyway.

---

### Post by jstratta on 2013-11-20
Im starting another thread for a different computer and then returning to this so as to not waste or restart.

---

### Post by kurt18947 on 2013-11-20
I don't know if this is helpful or not but Xubuntu 12.04 installed the Broadcom driver found via applications -> settings -> additional drivers and it works fine.  The wifi shows "Broadcom BCM 4312 802.11 b/g LP-PHY".  I also see "Marvell Technology group ltd. 88E8040 PCI-E Fast Ethernet Controller".  On this machine at least, there's an ethernet port covered by a rubber cover on the left side in front by the headphone jack.  Perhaps this varies by model?

---

### Post by Hadaka on 2013-11-20
Hi,since you have multiple machines, it would be best to 
create a thread for each machine.Please include the wireless script
with each post to help determine the problem.
wireless script -> [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)
thanks.

---

### Post by jstratta on 2013-11-20
On this machine it crashes it

---

### Post by jstratta on 2013-11-20
Ok, i will. I have resolved the mini in the other thread and i will get back to the mac soon.

---

### Post by jstratta on 2013-11-22
I will have to move on. I will close this and make a new thread when i get a chance again.

---

