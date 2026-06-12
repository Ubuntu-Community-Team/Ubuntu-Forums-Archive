---
title: "Lenovo IdeaPad Yoga - slow wifi"
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by imper2 on 2016-01-22
Hi everyone!

I'm fresh user of Ubuntu, so I'm not really good at using terminal  commands etc. However, Ubuntu is very easy, and everything works just  fine, but...

My wifi achieve max 1mbps download on ubuntu. On windows 10, and on my  android phone I got about 15mbps results (speedtest.net). I also "feel"  this weakness using the web...

I don't want to give up ubuntu, so I want to solve this problem. Here's, what I did:

Updated everything using (from this thread: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) ):
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then I've searched this forums for threads with similiar problems. Found:
[http://ubuntuforums.org/showthread.php?t=2178572](http://ubuntuforums.org/showthread.php?t=2178572) - didn't worked
[http://ubuntuforums.org/showthread.php?t=2262693](http://ubuntuforums.org/showthread.php?t=2262693)  - as far as i understand it - it swapped drivers for a moment, but this  didn't helped at all.

I would apriciate any help and ideas.

```

dmesg | grep -e 8723 -e 80211 | tail -n15
```

outputs:
```
[    5.381088] RTL8723AU: set ssid [imperplayzte] fw_state = 0x00000008
[    5.437027] RTL8723AU: start auth
[    5.442642] RTL8723AU: auth success, start assoc
[    5.456387] RTL8723AU: send eapol packet
[    5.456866] cfg80211: Regulatory domain changed to country: PL
[    5.456869] cfg80211:  DFS Master region: ETSI
[    5.456870] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    5.456874] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    5.456875] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    5.456877] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    5.456878] cfg80211:   (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2700 mBm), (0 s)
[    5.456880] cfg80211:   (57000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[    5.464350] RTL8723AU: send eapol packet
[    5.464495] RTL8723AU: set pairwise key to hw: alg:4(WEP40-1 WEP104-5 TKIP-2 AES-4) camid:4
[  589.490809] RTL8723AU: send eapol packet
```

If you need it, I also attached my wireless-info.txt file.

Thanks in advance.


[ATTACH]266886[/ATTACH]

---

### Post by Vladlenin5000 on 2016-01-22
You can try the driver from a PPA that has been reported as working fine.

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8723au-bt-dkms rtlwifi-new-dkms linux-firmware
```

---

### Post by imper2 on 2016-01-22
Thank you for your reply!

After ```

sudo apt-get install rtl8723au-bt-dkms rtlwifi-new-dkms linux-firmware
```
I got such error:
```
new-dkms linux-firmware
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
E: Nie uda&#322;o si&#281; odnale&#378;&#263; pakietu rtl8723au-bt-dkms
```
Which means in english:
```
...
E: Packet rtl8723au-bt-dkms was not found
```
What should I do now?

---

### Post by Vladlenin5000 on 2016-01-22
As you can see in [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi) the package exists. Did you updated the software sources after adding the PPA? That's what *sudo apt-get update* is for...

---

### Post by imper2 on 2016-01-23
I've done all three steps, just copying what you gave mi in code block. I've done it one more time, I got the same error. Tried to find something about such errors in google, but with nothing there.

I'm stuck :(

**edit**
OMG I just realized that in my house wifi is working excellent - I mainly use ubuntu at work.
Strange thing is that I got exactly the same model of router in home and in work (ZTE MF28D).

Any ideas?

---

