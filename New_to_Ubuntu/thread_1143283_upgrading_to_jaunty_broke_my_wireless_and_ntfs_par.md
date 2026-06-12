---
title: "upgrading to jaunty broke my wireless and ntfs partition wont shrink"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Yondergod22 on 2009-04-29
wireless problem:
I was running Ubuntu 8.04, and I got my wireless working  by installing the driver with ndiswrapper and manually connecting on the command line. 
Now after upgrading to 9.04 it doesn't work any more. I installed the same driver with ndiswrapper, and tried both manually connecting and with network manager. When I try manually connecting DHCP discover always fails, and when I try with network manager it keeps asking for my wep key over and over(with about 20-30 seconds in between each time it asks) until I cancel it. I double checked my key a million times and it still doesn't work.
oh and Its a trendnet TEW424UB usb adapter
and the commands I use the manually are
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "(ssid)"
sudo iwconfig wlan0 key (wep key)
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```
[s]NTFS problem:
I want to make my windows partition smaller so I can make ubuntu bigger, it wont let me shrink the ntfs partition. I tried both gparted live and the one in Ubuntu (and on ubuntu live cd)
I ran chkdsk, restarted, and defraged it multiple times. But it still wont let me. :-x[/s]
fixed :D

Thank you for your help :)

---

### Post by dmaxel on 2009-04-29
OK, first off, I can't help you with the wireless problem, I have no clue myself. :popcorn:

For the NTFS problem, it would actually be safest to go into Windows and then shrink it from there, without causing any data loss. Depending on what version of Windows you have, you either need a program to shrink the partition, or do it quickly without installing anything (that would be one of the few good things about Vista). So what Windows are you using?

---

### Post by Yondergod22 on 2009-04-29
Thanks for your help, I have windows XP

edit: lol [http://www.giveawayoftheday.com/](http://www.giveawayoftheday.com/) just happens to have a partition manager when I need it, should I use that one or is there a better one?

edit2: nevermind, I used that one and it worked XD thanks a lot :D :D :D 

still need to fix the wireless though

---

### Post by Yondergod22 on 2009-05-01
bump. 

windows is annoying I need internet on my ubuntu >.< 

help me, please and thank you

---

