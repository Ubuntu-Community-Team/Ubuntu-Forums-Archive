---
title: "Unstable connection with intel 6235 -n"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by kamikaze1993 on 2014-09-27
Hello, I've had some issue with wifi card on my laptop [COLOR=#000000][FONT=verdana]Asus Zenbook UX32VD  .  I am running Lubuntu 14.04 nowadays, for a couple of days ago i suddenly got troubles with my wifi card after a software update. Problems like disconnecting all the time,low speed and low range. 


[/FONT][/COLOR][COLOR=#000000][FONT=verdana]Information about my wifi card:
[/FONT][/COLOR]http://pastebin.com/xKm7ZkD8




I would really appreciate if someone could help me?


[COLOR=#000000][FONT=verdana]

[/FONT][/COLOR]

---

### Post by weatherman2 on 2014-09-27
You appear to have a USB wireless card also plugged in?  You should unplug the USB card and re-run the wireless tool, as that will show more accurate connection info.

I use this same Intel 6235 card daily on my own laptop in Ubuntu and it works well for me.  Some people report needing to set the "11n_disable" parameter = to "8" with Ubuntu 14.04 (I didn't have to do that when I tested my card with 14.04 - I normally use Ubuntu 12.04.).  You already set this parameter to "1" in the file:

/etc/modprobe.d/iwlwifi.conf

(It's in there twice.)  You could try changing the value from 1 to 8 (delete the redundant line so you have only one line).  Use a text editor with "sudo" to get root access to the file.

---

### Post by kamikaze1993 on 2014-09-27
Here is the new version :
[http://pastebin.com/ZsdswBr7](http://pastebin.com/ZsdswBr7)

I did change it from 1 to 8,but it still doesn't work. Does anyone have some other ideas?

---

### Post by weatherman2 on 2014-09-27
That looks like the same wireless output as the first pastebin; it still shows the USB card plugged in and 11n_disable = 1.

---

### Post by kamikaze1993 on 2014-09-28
I try one more time: 
[http://pastebin.com/2W4g7FCK](http://pastebin.com/2W4g7FCK)

I am now connected through cabel;)

Does someone know how i could fix my wifi card?

---

