---
title: "[SOLVED] WEP network names and connection problems"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by njd4k on 2008-08-22
Quick question: are there any characters that are off-limits when setting up a wireless network for Linux? I have had no trouble connecting to unencrypted networks, or to this particular WEP network using my Win XP boot, but I can't connect in Linux. The name of the network is "a&g" but when I try to connect using the GUI interface it says it's trying to connect to "%s" which makes me wonder whether it's taking the ampersand to be some sort of operator rather than just another character. The password is a string of numerals, and I also wonder whether whether it should be some or all alphabetical.

I realize that this is an easy thing to just test (change the network name) but this was set up by my roommates before I recently moved in, and the names connected by that & are theirs. I don't want to look like I have social problems demanding they change the network name unless I have good reason to think this is the problem. I haven't been able to find anything about this by searching the forums or Googling.

---

### Post by livestockPimp on 2008-08-22
Sorry I have not experienced this personally

have you tried connecting via command line, you might be able to test it this way.
below are some general commands that are used to connect a wireless network via command (assuming your wireless adapter is wlan0 and your key is xxxxxxxxxx)

iwconfig wlan0 essid a&g
iwconfig wlan0 key restricted xxxxxxxxxx
ifconfig wlan0 mode managed
dhclient wlan0

if this works you can script it and make it come up on boot.

---

### Post by njd4k on 2008-09-03
I am sorry to be replying so late to this, but I tested my hypothesis and it (partly) worked. However, I am still having trouble using encrypted networks. I hope someone can help me.

When I tried livestockPimp's suggestion, I received an error, and the terminal told me "g" was not a valid command. (Actually, I may as well admit I changed the letters out of hyperconscious security -- the network was named "j&d").

I reconfigured the wireless router to be named jandd and removed any security, and it worked on Ubuntu without a problem, just as other wireless networks have. Then I tried reinstating WEP security, and it failed. Using the GUI, the computer will try to connect for several minutes before redisplaying the dialog window requesitng the WEP key. Using livestockPimp's command line approach, the terminal now returns this error:

```
nic@nic-laptop:~$ iwconfig wlan0 essid jandd
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```

So; does this mean wlan0 is not my adapter? How can I check to see? What should I do next?

---

### Post by njd4k on 2008-09-03
I tried enabling third-party repositories and updating in case my driver was not up to date, and that did not work.

---

### Post by njd4k on 2008-09-04
This was the output I got describing my card using a command I found on another forum here:
```

nic@nic-laptop:~$ lspci | grep Broadcom
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

I'm a total noob. Will someone please point me in the right direction?

---

### Post by newtubunix on 2008-09-11
> **njd4k said:**
> 

```
nic@nic-laptop:~$ iwconfig wlan0 essid jandd
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
```

So; does this mean wlan0 is not my adapter? How can I check to see? What should I do next?

Have you tried ..
```
sudo iwconfig wlan essid jandd
```

---

### Post by njd4k on 2008-09-13
Yes, but that didn't work either. It seems to be a Dell driver issue. Thanks for responding. I'll post a solution when I find one.

---

### Post by njd4k on 2008-10-26
Problem solved. See this other thread:

[http://ubuntuforums.org/showthread.php?t=913901](http://ubuntuforums.org/showthread.php?t=913901)

---

