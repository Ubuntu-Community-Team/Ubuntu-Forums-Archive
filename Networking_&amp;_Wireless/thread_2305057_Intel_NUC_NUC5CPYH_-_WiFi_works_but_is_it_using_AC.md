---
title: "Intel NUC NUC5CPYH - WiFi works but is it using AC protocol ?"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by mridul3 on 2015-12-02
Hi, 

I am noob on 15.10 64bit Intel NUC NUC5CPYH. 

Wifi works but its half the speed compared to my macbook pro that uses AC.  I am trying to get similar speed on the NUC which also has AC wifi in the specs. 

The intel website asked me to download this file and copy it to lib/firmware. 
[https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.14.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.14.0.tgz)

I unzipped the file and copied the ucode files to /lib/firmware. Is that all that I have to do ? Is there a modprobe also needed? 
Here is the link to the intel website: 

[www.intel.com/support/wireless/wlan/sb/CS-034398.htm](www.intel.com/support/wireless/wlan/sb/CS-034398.htm)


Could someone please advise on 

1. How to ensure wifi is using the best possible driver and is connecting using AC protocol. 
2. If its not, what are the exact steps to get this to work using AC wifi. 

Thanks.

---

### Post by Hadaka on 2015-12-02
Hi, try this..
[http://ubuntuforums.org/showthread.php?t=2295720](http://ubuntuforums.org/showthread.php?t=2295720)
read the entire thread before you issue any commands
i "think" the backports have been updated since this, so
you may not have to jump through all the hoops.
you say "I am noob on 15.10 64bit Intel NUC NUC5CPYH."
so if you need help,let us know.
also please post..
```
modinfo iwlwifi | grep 5212
```
good luck.

---

### Post by mridul3 on 2015-12-03
Thanks. I read the whole thing and if you see the post #9, it shows networks a/b/g/n. I get that too. But no AC. 

As requested: 
modinfo iwlwifi | grep 5212
alias:          pci:v00008086d0000095Bsv*sd00005212bc*sc*i*


Here are my wifi details: 

02:00.0 Network controller: Intel Corporation Wireless 3165 (rev 81)
	Subsystem: Intel Corporation Dual Band Wireless AC 3165
	Flags: bus master, fast devsel, latency 0, IRQ 314
	Memory at 81300000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [40] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 94-65-9c-ff-ff-7e-48-1b
	Capabilities: [14c] Latency Tolerance Reporting
	Capabilities: [154] L1 PM Substates
	Kernel driver in use: iwlwifi



... and 

iwconfig
enp3s0    no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"Himalaya-5"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: E8:FC:AF:F5:37:28   
          Bit Rate=54 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0


lo        no wireless extensions.

---

### Post by kurt18947 on 2015-12-04
This sort of looks like you're connecting at "G" speeds:
> Bit Rate=54 Mb/s   Tx-Power=22 dBm

I have no experience with Intel AC devices but do have a couple Intel 6200 devices and one had significant speed issues as installed. I tried a few things and this seems to have helped the most. I was not/am not using bluetooth.
[INDENT]> If your WiFi is slow when using Bluetooth, try adding the following to /etc/modprobe.d/iwlwifi.conf and reboot: 

options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8
[/INDENT]

That line got my speed from 26-54 mb./sec to 117 mb./sec. This is on a wifi connection that should max out at 144 mb./sec. Again, I'm not sure if this will help your machine but it seems to be a common fix with Intel 6200 adapters. Given that iwlwifi seems to drive most newer Intel wifi adapters it might be something to keep in mind.

---

### Post by mridul3 on 2015-12-04
@kurt18947, thats great. 
I am not intending to use BT, but I dont want to lose the capability. Will BT work if I add this line ?

---

### Post by Hadaka on 2015-12-04
Hi, if you leave out..
```
bt_coex_active=0 
```
it will have no effect on your bluetooth.
you can still possibly gain better speed with..
*To install
```
echo options iwlwifi swcrypto=1 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf 
```
*To Delete --remove back to default
```
sudo sed -i '/^options iwlwifi swcrypto=1 11n_disable=8/ d' /etc/modprobe.d/iwlwifi.conf
```
boot and test
Also please post the output of..
```
iw reg get
```

---

### Post by mridul3 on 2015-12-04
No change in bit rate unfortunately . 

```

$ iw reg get
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

---

### Post by Hadaka on 2015-12-04
ok, if you havent already please do..
copy and paste
```
sudo sed -i '/^options iwlwifi swcrypto=1 11n_disable=8/ d' /etc/modprobe.d/iwlwifi.conf
```
then to set your country code.
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
boot
any change?

---

### Post by mridul3 on 2015-12-04
Speeds went down. speedtest.net shows connecting at 12mbps (as compared to 28 before.)  
Bit rate shows 0 mbps.

```

 iwconfig
enp3s0    no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"Himalaya-5"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: E8:FC:AF:F5:37:28   
          Bit Rate=6 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:418   Missed beacon:0
```

---

### Post by mridul3 on 2015-12-04
i mean bit rate is 6. 
 do we know if it actually picked ucode files I placed in /lib/firmware after downloading from intel website.

---

### Post by Hadaka on 2015-12-05
it probably wouldnt have this..
```
modinfo iwlwifi | grep 5212
alias:          pci:v00008086d0000095Bsv*sd00005212bc*sc*i*
```
if something was missing.
lets see if there is anything in dmesg
please post
```
dmesg | grep iwl
```
thanks

---

### Post by mridul3 on 2015-12-06
Seems like firmware is detected correctly. 

```
  
dmesg | grep iwl
[    3.924734] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    3.939482] iwlwifi 0000:02:00.0: loaded firmware version 15.195093.0 op_mode iwlmvm
[    3.994221] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    3.994740] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.995352] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.172336] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.708173] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    5.471851] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.472525] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.539396] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    5.540025] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled

```


I noticed that my reg country is set to 00 again. I repeated the steps but I could not get is back to US. 
No change in speeds though.

---

### Post by mridul3 on 2015-12-09
Thanks Hadaka. 
It still shows its using abgn and not AC. In other threads people do make it to show AC. Also speed is also half of what I get on other computers.  D oes not seem like a signal/reception issue.

---

### Post by Hadaka on 2015-12-09
Hi, try to copy and paste the country code commands in post #8
that should set it to US
There was a recent thread with chili555  about the inability to use 5ghz
and the user found the answer by moving his antenna wire from one post
to the other on his internal wifi card. I failed to save that link so i do not
know what type of card it was. It may be worth your while to take a peek
and see if you have the 2 post type card also.

---

### Post by chili555 on 2015-12-09
> loaded firmware version [COLOR="#FF0000"]15[/COLOR].195093.0It loads the -15 firmware.You downloaded and installed the earlier and, I assume, less good -14.> sudo iw reg set US
sudo sed -i 's/^REG.*=$/&[COLOR="#FF0000"]US[/COLOR]/' /etc/default/crdaIs your region US? Or some other? Please check: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) If it is not US, then run the command again with your two letter code in place of US.> wlp2s0    IEEE 802.11[COLOR="#FF0000"]abgn[/COLOR]  ESSID:"Himalaya-5"  This is not an indicator of what the card is doing. It doesn't change. I have never seen AC listed on an Intel device.

In my case, no matter which of the three routers I have and use, including an AC, my card always reports the same:> wlp3s0    IEEE 802.11[COLOR="#FF0000"]abg[/COLOR]  ESSID:"GBR1"> sudo sed -i '/^options iwlwifi swcrypto=1 11n_disable=8/ d' /etc/modprobe.d/iwlwifi.confI think I'd try both with and without the 11n_disable part.

Finally, I also have a NUC and all sorts of vague problems were fixed when I updated the BIOS. I suggest you do the same.

---

### Post by mridul3 on 2015-12-10
thanks Chilli555 
Updated bios. No  change. still 54mbps in iwconfig. 

but cant seem to get my country set to US
```

$ sudo iw reg set US
$ sudo iw reg get
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
```

and this is set too: 
```

REGDOMAIN=US
```

and i rebooted just to be sure.

---

### Post by chili555 on 2015-12-11
When the regulatory domain is set to US, it is quite different from unset:> country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)And from my machine:> country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)
Whether this is a deal-breaker or -maker in terms of connectivity and speed, I don't know. I do know that I have worked on hundreds of cases over the years and have recommended this, along with other tweaks and quite often, it helps.

We might try two other things:```
sudo apt-get install --reinstall crda wireless-crda wireless-regdb
```Also:```
sudo -i
echo "options cfg80211 ieee80211_regdom=US"  >  /etc/modprobe.d/cfg80211.conf
exit
```Reboot and check:```
dmesg | grep US
```We hope we see:```
cfg80211: Regulatory domain changed to country: US
```

---

### Post by mridul3 on 2015-12-15
Did not get expected results. 


```
dmesg | grep 802

[    4.544490] cfg80211:  DFS Master region: unset
[    4.544493] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    4.544498] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    4.544502] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    4.544504] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    4.544508] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    4.544512] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    4.544515] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    4.544518] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    4.544520] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)




```

---

### Post by chili555 on 2015-12-16
I am not at all sure that crda is a deal-breaker or -maker as respects AC speeds, but I am quite curious as to how and why, on your system, it defies all efforts whatsoever to set it! I haven't any other suggestions, unfortunately. 

What is your verified speed now? What does speedtest.net report? What do file transfers within your own network tell you?

---

### Post by mridul3 on 2015-12-21
The iwconfig shows 54mbps and speedtest.net shows 30mbps tops for download.  I dont have file sharing on yet but my guess is that will be somewhat in the range. ( cant expect 200 mbps) 

i feel the same way, crda could help only if setting to US would turn on that magic radio freq needed for AC. I cant seem to find anything on the net that talks to that.

---

