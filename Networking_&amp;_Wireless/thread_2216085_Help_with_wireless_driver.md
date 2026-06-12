---
title: "Help with wireless driver"
date: 2014-04-07
forum: Networking &amp; Wireless
---

### Post by Micheal_David_Lege on 2014-04-07
I got this. my wireless tries to connect but just keeps trying and trying. but its only when the wireless routers are [h=2]siemens gigaset se567[/h]
Help would be appreciate

micheal@MichealDavidLeger:~$ wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-04-07 16:30:05--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com... 204.236.219.205
Connecting to dl.dropbox.com|204.236.219.205|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-04-07 16:30:05--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com... 54.235.138.1, 23.21.47.41, 54.225.159.160, ...
Connecting to dl.dropboxusercontent.com|54.235.138.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4357 (4.3K) [text/plain]
Saving to: `wireless_script'


100%[======================================>] 4,357       --.-K/s   in 0.004s  


Last-modified header missing -- time-stamps turned off.
2014-04-07 16:30:06 (969 KB/s) - `wireless_script' saved [4357/4357]




Results archived in "wireless-info.tar.gz", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.


micheal@MichealDavidLeger:~$

---

### Post by varunendra on 2014-04-08
> **Micheal_David_Lege said:**
> **Results archived in "[COLOR="#0000FF"]wireless-info.tar.gz[/COLOR]"**, as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.

We need this "wireless-info.tar.gz" file (highlighted above) that has been created by the script. It should be in your Home directory. Please attach it in your next post.

---

### Post by Micheal_David_Lege on 2014-04-08
[ATTACH]251836[/ATTACH]

---

### Post by Micheal_David_Lege on 2014-04-08
so here is the file. Thanks for your effort varunendra

---

### Post by papibe on 2014-04-09
Moved to its own thread.

---

### Post by varunendra on 2014-04-09
Ubuntu 11.10 is no more supported, and the kernel you are using is pretty outdated now. Please upgrade to 12.04.4. I would recommend a clean install overwriting the current one. That will give you a newer kernel with better driver.

Apart from that, some other suggestions -

**1)** Make sure the ethernet cable is unplugged while trying to connect to wireless access-point. Network Manager does not attempt to connect wirelessly when a wired connection is detected.

**2)** In your router/access-point, change the encryption to WPA2 with AES (CCMP), currently it is using WPA with TKIP which is not good for signal quality and speed. Reboot the router after saving the changes.

**3)** Try a driver parameter with the following command -
```
echo "options ath5k nohwcrypt=Y" | sudo tee /etc/modprobe.d/ath5k.conf
```
This change will take effect after a system reboot.

**4)** If the above simple changes don't seem to help (try their effect after rebooting if required), try installing a backported driver as suggested in this post (replace "**[COLOR="#FF0000"]defconfig-ath9k[/COLOR]**" with "**[COLOR="#0000CD"]defconfig-ath5k[/COLOR]**" in the commands) : [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)

---

