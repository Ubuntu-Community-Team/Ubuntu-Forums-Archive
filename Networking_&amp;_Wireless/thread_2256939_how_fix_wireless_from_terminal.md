---
title: "how fix wireless from terminal?"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by einstein**-7 on 2014-12-15
Lol just had the sys freez in the middle of an update and rebooted , now its messed up and wireless isn't working so no fixing is going to happen. Anyone know how to check and enable the wireless networking from the terminal?

---

### Post by Bucky Ball on 2014-12-15
*Thread moved to **Networking & Wireless**.*

You have no access to a cable? That would be one solution re. getting online at least. 

Have you restarted the machine? You might like to have a look at what state your /etc/network/interfaces file is in. Might give some clues as to what's gone on.

---

### Post by chili555 on 2014-12-16
I assume you are asking about fixing the wireless from the terminal because the computer will only boot to a command prompt. Assuming this is true, Network Manager won't be present to start your wireless. Check to see if you have wireless capability:```
iwconfig
```If you see something like this:```
wlan0     IEEE 802.11abgn  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  
          Bit Rate=78 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```Then you are half-way there. Does it scan?```
sudo iwlist wlan0 scan
```We needn't see the results; we just want to know that it scans or the error message if it won't. If you have a wlan0 interface and it scans, let's get it to connect.

I suggest you  edit your /etc/network/interfaces file with the text editor nano. Please see: [http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal](http://askubuntu.com/questions/464507/ubuntu-14-04-server-wifi-wpa2-personal) and also: [http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano](http://askubuntu.com/questions/54221/how-to-edit-files-in-a-terminal-with-nano)  Of course, substitute your details here.

Post back if you get stuck.

---

### Post by einstein**-7 on 2014-12-17
I found a thread on remounting the sys in rw mode and starting the kernel and network manager manually buy I got some error that it wasn't present.. Just can't find the link again.  I did find that I had an older kernel option in grub and that one worked so just re updated from there and overwrote as it were the newer broken kernel.  Good stuff though guys nice to know how to check and enable networks in case of future related issues!

---

