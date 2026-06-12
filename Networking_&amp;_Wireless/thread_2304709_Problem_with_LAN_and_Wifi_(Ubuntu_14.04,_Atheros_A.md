---
title: "Problem with LAN and Wifi (Ubuntu 14.04, Atheros AR2861, Wireless-N 2200)"
date: 2015-11-29
forum: Networking &amp; Wireless
---

### Post by Anuschka on 2015-11-29
I am running Ubuntu 14.04 and Windows 10 as Dual Boot. I have no problems with my internet under Windows 10. However, under Ubunutu, both wifi and lan make trouble:

- I have a slow and unstable **wifi** connection (speed varies, sometimes it completely disconnects - best speed is 20 Mbits, compared to 50 Mbits under Windows 10). 
- My **lan** connection does show as connected, but I am unable to open any websites at all. I cannot even access my router configuration.

LAN: Qualcomm Atheros AR8161 Gigabit Ethernet
Wifi: Intel Centrino Wireless-N 2200
Router: Speedport W724V Type C (German Telecom)
Laptop: Lenovo Ideapad Y580
OS: Windows 10 / Ubuntu 14.04.3 LTS

So far, I have tried:
- Set IPv6 to "Ignore" for both Wifi and Lan - no difference.
- Make sure both devices are not listed under System Settings -> Software & Updates -> Additional Drivers - they are not.
- Update my router firmware.

Not sure if this info helps: sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 08
       serial: b8:88:e3:94:47:a5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.2.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:31 memory:d3600000-d363ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 9c:4e:36:8c:d8:10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-37-generic firmware=18.168.6.1 ip=192.168.2.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:29 memory:d3500000-d3501fff
```

Thank you all for your help!

---

### Post by Hadaka on 2015-11-29
Hi, lets mess about with your wireless first then the ethernet.
Please COPY and paste.
*NOTE the [COLOR=#ff0000]sed[/COLOR] commands are to **delete** the entry *IF it fails to improve.
marked in [COLOR=#ff0000]red[/COLOR] rymes with [COLOR=#ff0000]sed[/COLOR].
so..**do not **run the red commands first time through..
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi

echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
sudo [COLOR=#ff0000]sed[/COLOR] -i '/^options iwlwifi 11n_disable=8/ d' /etc/modprobe.d/iwlwifi.conf

echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo [COLOR=#ff0000]sed[/COLOR] -i '/^options mac80211 probe_wait_ms=1000/ d' /etc/modprobe.d/mac80211.conf

sudo modprobe -v iwlwifi
```
boot
[B]
*if  there is no improvement in the wireless...run the red-sed commands only.

[/B]

---

### Post by Anuschka on 2015-12-02
Thank you very much for your quick answer! Was away from home for a couple of days, but I finally got around to trying it out. Here is what I got:

   ```
afh@Laxi:~$ sudo ifconfig wlan0 down  
[sudo] password for afh:  
afh@Laxi:~$ sudo modprobe -r iwldvm  
afh@Laxi:~$ sudo modprobe -r iwlwifi  
[COLOR=#ff0000][B]rmmod: ERROR: missing module name.  
[/B][/COLOR][COLOR=#ff0000]**modprobe: FATAL: Error running remove command for iwlwifi **[/COLOR]
afh@Laxi:~$ echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf  
options iwlwifi 11n_disable=8  
afh@Laxi:~$ echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf  
options mac80211 probe_wait_ms=1000  
afh@Laxi:~$ sudo modprobe -v iwlwifi  
insmod /lib/modules/3.19.0-37-generic/kernel/net/wireless/cfg80211.ko  
insmod /lib/modules/3.19.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=8

```

I have no idea what those 2 bold red lines mean/what I have to do about them? Other than that, at least the Wifi seems to run more smoothly (I have not waited for a page to load for 2 minutes again yet, might be just coincidence though, will see), speedtest is still showing a range from 8 mbit to 21 mbit.

**Edit:** Yes, it was just chance, I just had the Wifi slow down to a stop again.

---

### Post by Hadaka on 2015-12-02
Hi, please post the output of..
```
cat /etc/modprobe.d/mac80211.conf 
/etc/modprobe.d/iwlwifi.conf
```
then go here,follow instructions and post
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

---

### Post by Anuschka on 2015-12-02
Output:

```
afh@Laxi:~$ cat /etc/modprobe.d/mac80211.conf 
options mac80211 probe_wait_ms=1000
afh@Laxi:~$ /etc/modprobe.d/iwlwifi.conf
bash: /etc/modprobe.d/iwlwifi.conf: Permission denied
```

I hope I got that right?

And here is the result from the other forum post.

---

### Post by Hadaka on 2015-12-02
Hi please copy and paste

```
sudo rfkill unblock all
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Your wireless signal seems a bit weak
```
wlan0     Scan completed :
          Cell 01 - Address: <MAC 'WLAN-779866' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm
```
Try etting your channel to 6 or 11 and check the physical connection of the router antenna
and the wireless card.
also disconnect the wired connection and see if there is an improvement in the wireless
thanks.

---

### Post by Anuschka on 2015-12-05
I believe that did it! Right now, it shows continuously around 30 Mbit/s, at least! :D Thank you very much!

Do you have any tips what to do about my lan connection, as well?

---

### Post by Hadaka on 2015-12-05
Hi, since you have another post for the lan
"And here is the result from the other forum post."
please mark this one as solved and post the link
to your other thread. To mark solved sign in to this thread,
your first post,click TOOLS then choose solved
thanks.

---

### Post by Anuschka on 2015-12-06
I actually don't have another forum post; the post you quoted was me posting the result from the Wifi forum thread you linked to me ("then go here,follow instructions and post
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)"). But I can make a new seperate post for the lan, if you want me to?

---

