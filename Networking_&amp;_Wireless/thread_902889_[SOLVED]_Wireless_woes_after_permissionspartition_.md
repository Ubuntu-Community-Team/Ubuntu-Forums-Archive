---
title: "[SOLVED] Wireless woes after permissions/partition moving fiasco"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by pmsumner on 2008-08-27
I recently moved around some partitions - moved /usr /tmp and /home to their own partitions.  I found afterwards that some files had their ownerships set incorrectly (root.root for everything in /home for example).  I think I missed something with the moving directory command.

Anyhow, why it happened aside - I now can't connect to the wireless network I could connect to effortlessly before with WICD.

Can anyone suggest what might be wrong?  I hope it's just a perms problem.

(I am using a Fujitsu Siemens Li1718 - Atheros AR242x wireless. Compiled madwifi drivers again and lsmod | grep ath0 shows all drivers loaded.  iwconfig ath0 shows everything I'd expect:

```
phil@home-laptop:~$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:"WIRELESS_HO"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:6595  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Ignore attached file, just realised I ran the wrong command...

---

### Post by pmsumner on 2008-08-27
Attached is the output from:

```
phil@home-laptop:~$ sudo wpa_supplicant -w -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -ddd > /home/phil/wpa_supp.txt 
```

---

### Post by pmsumner on 2008-08-27
GAH!  After playing for a while and trying various things, I managed to connect manually using wpasupplicant and had changed nothing since that last attempt.

I think my router's on the fitz.

---

