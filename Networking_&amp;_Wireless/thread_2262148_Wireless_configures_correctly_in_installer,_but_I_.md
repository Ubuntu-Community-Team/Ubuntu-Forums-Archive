---
title: "Wireless configures correctly in installer, but I can't get working after reboot."
date: 2015-01-23
forum: Networking &amp; Wireless
---

### Post by Dimitri_Bosiers on 2015-01-23
Hi,

I've Installed Ubuntu sever 14.04.1 LTS
The installer configures my wifi nic correctly, so that was great :p

But...
It doesn't save the configuration :?, and I'm struggling to get the wifi nic online ( quite important since the machine has no wired connection to the gateway ) I'm getting a lot of these : Register frame command failed ( type=208): ret=-114 (Operation already in progress )
The card gets configured or at least partly, I have an IP (static), netmask, broadcast.
Some TX,RX bytes. But I can't ping my gateway. Although RX goes up after pinging.

Is there a way to make the installer save the damn thing, so I can modify it later ?
Or is there a way to restart the configuration wizzard. 
Or any other simple fix. 

I hope someone answers this quick, i'm finally would like to setup my personal subnetrouter/fileserver and it took me more than a week without any result. I Blame CentOS for that. That one really sucked but that's not for here.

---

### Post by chili555 on 2015-01-23
May we see:```
iwconfig
lsmod
cat /etc/network/interfaces
lspci -nn | grep 0280
```Thanks.

---

### Post by Dimitri_Bosiers on 2015-01-23
Is going to be difficult, as i have NO network i'm typing this from a spare laptop but i'll try to >> it to a file on usb so i can upload it.

---

### Post by chili555 on 2015-01-23
> **Dimitri_Bosiers said:**
> Is going to be difficult, as i have NO network i'm typing this from a spare laptop but i'll try to >> it to a file on usb so i can upload it.How about this?```
iwconfig > wifi.txt
lsmod >> wifi.txt
cat /etc/network/interfaces >> wifi.txt
lspci -nn | grep 0280 >> wifi.txt
```Then transfer the file wifi.txt on a USB to post.

---

### Post by Dimitri_Bosiers on 2015-01-23
all info exept my macaddr and ssid

/etc/wpa_supplicant.conf :

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1


network={
    ssid=&#8220;xxxxxxx&#8221;
    bssid=xxxxxxxxxxxxx
    scan_ssid=0
    proto=WPA2
    key_mgmt=WPA-PSK
    pairwise=TKIP
    group=TKIP
    psk=e1a98c6c2fec605fb2faeb144d385006e2fb804c34d704312bb42453bfc9d188
}

```

/etc/networking/interfaces :

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# wifi WPA2
auto wlan0
iface wlan0 inet static
address 192.168.1.64
netmask 255.255.255.0
wireless-essid xxxxxxxx
gateway 192.168.1.1
pre-up wpa_supplicant -B w -D wext -i wlan0 -c /etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant



```

iwconfig

```

          wlan0     IEEE 802.11abgn  ESSID:"xxxxxxx"            Mode:Managed  Frequency:2.412 GHz  Access Point: xxxxxxxxxxxxxxxx   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:475   Missed beacon:0

```

lspci :

```
07:00.0 "0200" "10ec" "8168" -r06 "1043" "8432"

```

---

### Post by Dimitri_Bosiers on 2015-01-23
oops forgot module list...

```
Module                  Size  Used by
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     46254  4 
arc4                   12608  2 
intel_rapl             18773  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
kvm                   451511  0 
snd_hda_codec_realtek    61438  1 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
ghash_clmulni_intel    13216  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mac80211              630653  1 ath9k
serio_raw              13462  0 
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
lpc_ich                21080  0 
nouveau              1097199  1 
cfg80211              484040  3 ath,ath9k,mac80211
mxm_wmi                13021  1 nouveau
video                  19476  2 nouveau,asus_wmi
ttm                    85115  1 nouveau
drm_kms_helper         53081  1 nouveau
snd_hda_intel          52355  0 
drm                   303102  3 ttm,drm_kms_helper,nouveau
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
i2c_algo_bit           13413  1 nouveau
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mei_me                 18627  0 
mei                    82276  1 mei_me
mac_hid                13205  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29482  1 snd_pcm
lp                     17759  0 
parport                42348  1 lp
snd                    69238  7 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_hda_codec,snd_hda_intel
soundcore              12680  1 snd
wmi                    19177  3 mxm_wmi,nouveau,asus_wmi
usb_storage            62209  1 
hid_generic            12548  0 
hid_logitech_dj        18581  0 
pata_acpi              13038  0 
usbhid                 52570  0 
hid                   106148  3 hid_generic,usbhid,hid_logitech_dj
firewire_ohci          40409  0 
psmouse               106678  0 
pata_marvell           12923  0 
r8169                  67581  0 
firewire_core          68769  1 firewire_ohci
ahci                   25819  3 
libahci                32560  1 ahci
crc_itu_t              12707  1 firewire_core
mii                    13934  1 r8169
```

---

### Post by Dimitri_Bosiers on 2015-01-23
Dinnertime here...raging hunger.

---

### Post by chili555 on 2015-01-23
First, I wouldn't use the less secure TKIP; I recommend the more secure AES. Second, I'd slim my interfaces file waaaaay down to:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# wifi WPA2
auto wlan0
iface wlan0 inet static
address 192.168.1.64
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 192.168.1.1 8.8.8.8
wpa-essid bbox2-d1a1
wpa-psk <your_plain_key>

```Then restart the interface:```
sudoo ifdown wlan0 && sudo ifup -v wlan0
```The -v for verbose will produce some output that may be helpful if there is a problem.

Check:```
ping -c3 www.ubuntu.com
```

---

### Post by Dimitri_Bosiers on 2015-01-24
shouldn't I provide some sort of certificate for AES ? I doubt that the certification authority utilities are installed, so that's why I went for TKIP.
But I'm a little confused, do you mean that I should try to get it up without wpa_supplicant because you stripped the pre-up and post-down rules from the interfaces file. Or does it run anyway if there is a /etc/wpa_supplicant.conf file ?

---

### Post by chili555 on 2015-01-24
> **Dimitri_Bosiers said:**
> shouldn't I provide some sort of certificate for AES ? I doubt that the certification authority utilities are installed, so that's why I went for TKIP.
But I'm a little confused, do you mean that I should try to get it up without wpa_supplicant because you stripped the pre-up and post-down rules from the interfaces file. Or does it run anyway if there is a /etc/wpa_supplicant.conf file ?No certificate file is required.

It runs anyway, even if there is *NOT* an /etc/wpa_supplicant.conf file!

TKIP is inherently less secure than AES; I do not recommend it ever. Also, in a few years of answering wireless posts, I am quite convinced that many Linux drivers work well will AES and not at all well with TKIP. All you need do is switch the encryption method in the router. [http://www.planex.net/pdf/router/mzk-mf150/v1/html/image/4-1-3.gif](http://www.planex.net/pdf/router/mzk-mf150/v1/html/image/4-1-3.gif)

Please let us know if the suggested changes are effective.

---

### Post by Dimitri_Bosiers on 2015-01-24
Of course I will let you know :smile: , i'll try it monday since i'm out of bed 6 hours before you, you will have your feedback somewhere in the late morning. 
By the way it's very sweet of you to give me some router education, but i would like to inform you that i'm not a complete noob.
I"ve been using routers and linux since 2000.;)  Have a great weekend.

---

### Post by Dimitri_Bosiers on 2015-01-26
Sweet, it finally works so i can go on building my subnet router. :biggrin: Big thank you !

Although this morning there was some weird **** going on, but i'm going to start a new thread for that.
 I had no network but my root password changed, I had to reset it to be able to use su. I hope there's not some kind of X-hack in the wifi-driver. Going to keep a watchful eye. :-k

---

### Post by chili555 on 2015-01-26
> **Dimitri_Bosiers said:**
> Sweet, it finally works so i can go on building my subnet router. :biggrin: Big thank you !

Awesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

