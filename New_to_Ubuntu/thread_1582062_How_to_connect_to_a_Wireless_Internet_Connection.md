---
title: "How to connect to a Wireless Internet Connection?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by rohan_m on 2010-09-25
Hello,
I just installed Ubuntu on my desktop computer using wubi on my Windows 7 computer, and so far I am loving every moment of it. However, I cannot seem to get the internet connection to work. The network has MAC-Adress security, so when creating the connection, I said that the security is "None" as I could not find Mac Adress Security on the list. However, I cannot find the place that allows me to actually connect to the network, as when i right click on the network icon in the top right taskbar-thing it says "Network Disconnected" under Wireless Connections and it is greyed out. ANy help for this newbie? Thanks in advance!

BTW I am running 10.04 Stable

---

### Post by mrhhug on 2010-09-25
can you paste the output of ```
ifconfig
``` here?

---

### Post by rohan_m on 2010-09-26
Here you go:
 
> rohan@ubuntu:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:1a:a0:8b:21:dc 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Memory:fdfc0000-fdfe0000 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2188 errors:0 dropped:0 overruns:0 frame:0
TX packets:2188 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:280667 (280.6 KB) TX bytes:280667 (280.6 KB)

---

### Post by rohan_m on 2010-09-26
bump? Please help! I dont have Internet on my main PC untill I fix this!

---

### Post by spiky001 on 2010-09-26
Hi the best thing to do as you have just installed is connect eth0 cable carry out updates then check for hardware updates

---

### Post by dirghrabadia on 2010-09-26
I had issues connecting to wireless networks while I had 8.04 as a wubi install, on Vista. Try a LIVE CD, and see if it works.

---

### Post by mrhhug on 2010-09-26
> **rohan_m said:**
> bump? Please help! I dont have Internet on my main PC untill I fix this!

what that output is telling us is that your wireless card for some reason or another is not connected/ or otherwise unrecognized by ubuntu.

what kind of wifi card are you useing? if you can get online with a cable and do updates, that might help but might not, most popular cards should just work with ubutnu,

so what is the model of your card, and is it usb/pci/or other

---

### Post by lumore22 on 2010-09-29
Greetings-

Read your original post and the replies. All good, but ...

A simple  ?:  Did you enable your wireless device?

I also have Windows 7 dual boot w/ubuntu Lucid 10.04 2.6.24. Somewhere on your chassis/laptop ?? is a touch sensitive LED indicator that should be lighted up if your wireless is enabled. If not lighted, enable it by either pressing on the indicator or by right-clicking on the wireless icon in your docking area.

Fingers crossed for you.

Hope this is it. Pls let us know.:rolleyes:

---

### Post by rohan_m on 2010-09-30
its a desktop, so the wifi is indeed on, but thanks for the suggestion.
 
My card is a Broadcom 802.11g Network Adapter

---

### Post by mrhhug on 2010-09-30
can you try pasting ```
iwconfig
``` not sure why i recommend ifconfig, iwconfig (is used for wireless).... silly me, sorry to waste a post

i would like an output similar to [http://media.photobucket.com/image/sameple%20iwconfig/BadBoyDiddy/Screenshot-gqgQ.png](http://media.photobucket.com/image/sameple%20iwconfig/BadBoyDiddy/Screenshot-gqgQ.png) showing that you card is alive.

if you get nothing from that my next move would be to install "hardinfo" its an easy install ```
sudo aptitude install hardinfo
```
then type hardinfo into the command line to launch, now go down to PCI devices and see if you wireless card is listed - mine was all the way at the bottom of the PCI devices list, the attached pic is a screenshot from my box

(im assuming that the card is PCI correct? if not it might be under usb or however you have it connected)

ok so the more information that would be helpful is :
1)type of card: PCI USb ect - exact model numbers remove all doubt
2)output of iwconfig
3)did you try booting off the live cd? - most time ubuntu just works especially with popular chipsets like your broadcom g

EDIT: normally it is soo easy to connect to wifi in ubuntu, not sure why exactly your having these issues but i don't want this little problem to deter you for future ubuntuing

---

### Post by rohan_m on 2010-10-03
1. ill get that for you in a sec
2.
[EMAIL="rohan@ubuntu:~$"]rohan@ubuntu:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
[EMAIL="rohan@ubuntu:~$"]rohan@ubuntu:~$[/EMAIL] 
 
 
3. I burnt a live cd and tried it, i cant connect using that either

---

### Post by mrhhug on 2010-10-03
this thread soomed to help others:

```
sudo iwconfig wlan0 essid on 
```

[http://ubuntuforums.org/showthread.php?t=463707](http://ubuntuforums.org/showthread.php?t=463707)

---

### Post by gandaran on 2010-10-03
> **rohan_m said:**
> its a desktop, so the wifi is indeed on, but thanks for the suggestion.
 
My card is a Broadcom 802.11g Network Adapter
did you install the Broadcom driver, Broadcom drivers are not installed in Ubuntu by default.

---

### Post by lkraemer on 2010-10-03
Maybe this will help!
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=howto%3A+Broadcom)

lk

---

### Post by Ubuntic on 2010-10-05
I have two HP laptops that are essentially the same except one came with Windows XP and the other is running Vista.  Both use the same wireless connection.  I have installed Ubuntu 10.04 on both.  After entering the required SSID and WEP info, I have not been able to activate a wireless connection with the laptop running Vista, but a wireless connection was established immediately with the computer running XP.  I am able to connect to the internet on the Vista machine with the cable, but not wireless.  And I can be wireless with the Vista machine when using Vista.  I don't like Vista!  Which is why I decided to try Ubuntu.  I like Ubuntu except for the connection problem.  This is not exactly a "quick reply."  Just had to vent some frustration.

---

