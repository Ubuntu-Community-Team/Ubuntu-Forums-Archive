---
title: "ASUS X450J Wireless is not working [Soft blocked]"
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by jay62 on 2014-10-27
Hi

I bought ASUS X450J and wanted to try out Ubuntu 14.04 LTS before installing it on bootable USB. 

Everything worked fine except wireless. I did not tried Ethernet connection but I am assuming it should work fine.

However, to install I would require wireless to be working. Any help is much appreciated.

Some details that might be useful to understand the issue:

```

ubuntu@ubuntu:~$ lspci -nnk | grep -A2 0280
03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6627]
    Kernel driver in use: ath9k

```

```

ubuntu@ubuntu:~$ lsmod | grep -e ath9k
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211

```

```

ubuntu@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

If required I can provide more details.

---

### Post by jeremy31 on 2014-10-27
Did you try the keyboard combo to toggle wifi(FN+F?) or ```
rfkill unblock all
```

And it looks like an acer module might be loaded ```
lsmod | grep -e acer -e wmi
```

---

### Post by jay62 on 2014-11-05
Hi Jermy


Thanks for Reply.


I could have included these in my first post it self. I tried those options as well but no luck.


Here is the output.

Below command did not return any success code or any error but wireless did not turn on. I tried Function+F2 as well after that but wifi did not turn on.
```
ubuntu@ubuntu:~$ sudo rfkill unblock all


```


```
ubuntu@ubuntu:~$ lsmod | grep -e acer -e wmi
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
acer_wmi               32522  0 
sparse_keymap          13948  2 acer_wmi,asus_wmi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    69238  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mxm_wmi                13021  1 nouveau
video                  19476  4 i915,acer_wmi,nouveau,asus_wmi
wmi                    19177  4 acer_wmi,mxm_wmi,nouveau,asus_wmi
ubuntu@ubuntu:~$

```

---

### Post by Bucky Ball on 2014-11-05
You will have a better chance of installing the wireless driver if you do a full install. You can't install much in a Live session and what you manage to install will be erased on reboot. 

If you look in Additional Drivers you might see something for the wireless card, but that card should work out of the box with a full install.

[HERE'S]("http://www.htpcbeginner.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/") a fix if it doesn't and [HERE'S ]("https://duckduckgo.com/?q=Atheros+AR9485+ubuntu+14.04")is some research material if that doesn't work. Always good to do some prior to posting. ;)

---

### Post by jay62 on 2015-03-19
Hi Bucky Ball,

As you suggested I did installed Ubuntu 14.04 with third party drivers and that also did not fix the problem.

After installation of Ubuntu I tried both the links and many most of the items from both the links. But none of the things are working for me. I believe the issue I am facing is different.

I believe most of the solutions are proided for hard blocked but in my case it is soft blocked. 

Can someone help?

Chears

---

### Post by jeremy31 on 2015-03-19
> **jay62 said:**
> Hi Bucky Ball,

As you suggested I did installed Ubuntu 14.04 with third party drivers and that also did not fix the problem.

After installation of Ubuntu I tried both the links and many most of the items from both the links. But none of the things are working for me. I believe the issue I am facing is different.

I believe most of the solutions are proided for hard blocked but in my case it is soft blocked. 

Can someone help?

Chears

Blacklist acer_wmi and reboot```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
If it is soft blocked after reboot try the FN combo and/or ```
sudo rfkill unblock all
```

---

