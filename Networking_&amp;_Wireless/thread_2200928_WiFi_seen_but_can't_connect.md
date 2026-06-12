---
title: "WiFi seen but can't connect"
date: 2014-01-21
forum: Networking &amp; Wireless
---

### Post by dbdrybones on 2014-01-21
My driver is this
configuration: broadcast=yes driver=wl0 driverversion=6.30.223.141 (r415941) latency=0 multicast=yes wireless=IEEE 802.11abg

It is mid 2007 iMac

---

### Post by dbdrybones on 2014-01-22
Also I'm running Ubuntu now but same thing

---

### Post by chili555 on 2014-01-22
Please open a terminal and tell us about your device:```
lspci -nn | grep 0280
```Then we'll probably tell you that 'Additional Drivers' offered and installed the wrong driver; then we'll fix it up and then you'll give me a [SOLVED].

---

### Post by dbdrybones on 2014-01-25
04:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)

---

### Post by chili555 on 2014-01-26
I think the Broadcom STA driver that you have installed is correct. Is your router operating on the 5 GHz band? I think the STA driver needs some tinkering to get it to work on 5 GHz. Check:```
sudo iwlist eth1 scan
```You may get a result like:> Cell 02 - Address: XX:D7:19:41:54:XX
                    Channel:165
                    [COLOR="#FF0000"]Frequency:5.825 GHz (Channel 165)[/COLOR]
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"GBR1"
Then compare:```
sudo iwlist eth1 chan
```> 32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:5.825 GHz (Channel 165)



----------
Possible reference: [http://ubuntuforums.org/showthread.php?t=1923762](http://ubuntuforums.org/showthread.php?t=1923762)

---

### Post by dbdrybones on 2014-02-02
My is channel 7, what I do with it?

---

### Post by chili555 on 2014-02-02
> **dbdrybones said:**
> My is channel 7, what I do with it?So the router is on a channel the driver can use. Let's see why it isn't connecting. Please detach any ethernet cable and try to connect. Then run:```
cat /var/log/syslog | grep -e eth1 -e etwork | tail -n20
```Post the result here.

---

### Post by dbdrybones on 2014-02-02
toxbox@toxbox-iMac:~$ cat /var/log/syslog | grep -e eth1 -e etwork | tail -n20
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Activation (eth1/wireless): connection 'Wi-Fi connection 1' has security, and secrets exist.  No new secrets needed.
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Config: added 'ssid' value 'Dr_Who'
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Config: added 'scan_ssid' value '1'
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Config: added 'psk' value '<omitted>'
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> Config: set interface ap_scan to 1
Feb  2 09:36:31 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: inactive -> scanning
Feb  2 09:36:32 toxbox-iMac wpa_supplicant[2669]: eth1: Trying to associate with c8:d7:19:16:96:54 (SSID='Dr_Who' freq=2442 MHz)
Feb  2 09:36:32 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: scanning -> associating
Feb  2 09:36:32 toxbox-iMac wpa_supplicant[2669]: eth1: Associated with c8:d7:19:16:96:54
Feb  2 09:36:32 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: associating -> associated
Feb  2 09:36:35 toxbox-iMac wpa_supplicant[2669]: eth1: CTRL-EVENT-DISCONNECTED bssid=c8:d7:19:16:96:54 reason=0
Feb  2 09:36:35 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: associated -> disconnected
Feb  2 09:36:36 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb  2 09:36:37 toxbox-iMac wpa_supplicant[2669]: eth1: Trying to associate with c8:d7:19:16:96:56 (SSID='Dr_Who' freq=5180 MHz)
Feb  2 09:36:37 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: scanning -> associating
Feb  2 09:36:37 toxbox-iMac wpa_supplicant[2669]: eth1: Associated with c8:d7:19:16:96:56
Feb  2 09:36:37 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: associating -> associated
toxbox@toxbox-iMac:~$ 


My WiFi is Dr_Who

---

### Post by chili555 on 2014-02-02
> SSID='Dr_Who' freq=5180 MHzThat's not channel 7. That is channel 36 in the 5 MHz band. Does your card/driver combination see channel 36?```
sudo iwlist eth1 chan
```

---

### Post by dbdrybones on 2014-02-02
Yes

Channel 36 : 5.18 GHz

---

### Post by chili555 on 2014-02-02
> Feb 2 09:36:32 toxbox-iMac wpa_supplicant[2669]: eth1: Associated with c8:d7:19:16:96:54
Feb 2 09:36:32 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: associating -> associated
Feb 2 09:36:35 toxbox-iMac wpa_supplicant[2669]: eth1: [COLOR="#FF0000"]CTRL-EVENT-DISCONNECTED bssid=c8:d7:19:16:96:**54** reason=0[/COLOR]
Feb 2 09:36:35 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: associated -> disconnected
Feb 2 09:36:36 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 2 09:36:37 toxbox-iMac wpa_supplicant[2669]: [COLOR="#FF0000"]eth1: Trying to associate with c8:d7:19:16:96:**56** (SSID='Dr_Who' freq=5180 MHz)[/COLOR]
Feb 2 09:36:37 toxbox-iMac NetworkManager[668]: <info> (eth1): supplicant interface state: scanning -> associatingIt is evidently trying to hop back and forth between channel 7 and 36 as the router decides which channel has the least interference and changes. I'm studying this but, so far, I'm not quite sure what to try. I will keep looking for a solution.

---

### Post by dbdrybones on 2014-02-02
Thanks

---

### Post by dbdrybones on 2014-02-07
Did you found the solution?

---

### Post by dbdrybones on 2014-02-15
Please hurry

---

### Post by chili555 on 2014-02-15
Is power management on or off?```
sudo iwconfig eth1
```



-------

Possible reference to power: [https://wiki.debian.org/wl](https://wiki.debian.org/wl)

---

### Post by dbdrybones on 2014-02-20
IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

Can't turn off smiley, how I do that?

---

### Post by varunendra on 2014-02-20
> **dbdrybones said:**
> IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

**Can't turn off smiley, how I do that?**

By putting your code in 'Code' box. Please follow the "Using Code Tags" link in my signature below to see how.

---

### Post by chili555 on 2014-02-21
This is a purely experimental test and I am suggesting a radical experiment because we have tried everything else and have little or nothing to lose. Please get a temporary wired ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us have your report.

There is an additional option to disable smilies: [http://www.aruba.com/forum/attachments/f7/2401d1364938785-new-aruba-com-website-disable-smiles.jpg](http://www.aruba.com/forum/attachments/f7/2401d1364938785-new-aruba-com-website-disable-smiles.jpg)

---

### Post by dbdrybones on 2014-02-21
My Linux partition is gone because of that code.

All of my data is wiped out because of that code.

I lost everything and even that hard drive because of that code.

There is no way to restore because of that code.

I'm posting from my OS X

---

### Post by varunendra on 2014-02-21
> **dbdrybones said:**
> My Linux partition is gone because of that code.

All of my data is wiped out because of that code.

I lost everything and even that hard drive because of that code.

There is no way to restore because of that code.

I'm posting from my OS X

Congratulations!! Please immediately call Guinness and Limca book of World Records, you (or your system) just created one !!

No one in the entire History of Linux was ever able to wipe out 'Data' and lose everything because of **[THAT]("http://ubuntuforums.org/showthread.php?t=2200928&p=12935716#post12935716")** code, you're the First One (and I'm absolutely sure the last one too) !! :shock:

Why? Because THAT code is supposed to just remove a driver and install a tiny little package very nicely and gently. THAT poor little code can't do anything else no matter how much power you run with, regardless of how many times you run it.

So.... Congratulations once again ! :P

---

### Post by dbdrybones on 2014-02-21
I'm installing Linux Mint and try to see if it works

---

### Post by Iowan on 2014-02-21
> **varunendra said:**
> Congratulations!! Now, now... [-X

---

### Post by varunendra on 2014-02-21
> **Iowan said:**
> Now, now... [-X
Erm..(gulp!). If I need to clarify..

..I am absolutely sure that the code (in [post=12935716]this[/post] post) that I think dbdrybones was referring to (or 'Any' code so far in this thread for that matter) can never do anything like ANY of these -
> **dbdrybones said:**
> My **Linux partition is gone** because of that code.

All of my **data is wiped out** because of that code.

I **lost everything and even that hard drive** because of that code.

There is **no way to restore** because of that code.

That code ("apt-get remove --purge bcmwl-kernel-source" and "apt-get install linux-firmware-nonfree") is absolutely safe and doesn't even touch the filesystem except a few non-critical files in it.
*(oh yeah, the 'purge' part rebuilds the initramfs, which MAY be critical if the partition containing the boot image is low on disk space. But in that case, the system was going to crash anytime anyway, and even that can NEVER cause data loss or even a total system blackout).*

So I believe it might have been either an already failing hard-disk/other hardware, or some other external factor. If the '**accident**' occurred during or after running that code, it **is merely a coincidence** which I'm sure all of us (except the OP, until then at least) are 100% sure of.

Sorry if my way of expressing that hurt anybody, I certainly didn't mean to. :)

---

### Post by chili555 on 2014-02-21
> So I believe it might have been either an already failing hard-disk/other hardware, or some other external factor. If the 'accident' occurred during or after running that code, it is merely a coincidence which I'm sure all of us (except the OP, until then at least) are 100% sure of.Quite correct. We are sorry you had this misfortune, dbdrybones. We will be interested in your Mint experience.

---

### Post by dbdrybones on 2014-02-23
Got Mint and it is more faster than Ubuntu but I still have WiFi issue so I think my Mac could be too old and got outdated WiFi driver. I'm fine with ethernet cable. Does anybody know of a good WiFi USB stick from amazon that work with Linux?

---

