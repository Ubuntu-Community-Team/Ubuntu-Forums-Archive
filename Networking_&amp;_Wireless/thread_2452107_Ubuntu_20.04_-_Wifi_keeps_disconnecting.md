---
title: "Ubuntu 20.04 - Wifi keeps disconnecting"
date: 2020-10-16
forum: Networking &amp; Wireless
---

### Post by nemethda on 2020-10-16
Hello everyone!

Few months ago when I bought my new laptop (Acer Nitro AN515-43-R40X) I decided to install Ubuntu 20.04 LTS on it. So I'm a Linux novice :)

At the beginning I didn't have any network/WiFi issues, then roughly a month ago my WiFi connection started to drop. The connection is always up and working when I start the laptop but after few minutes of surfing the net, it gets disconnected. It happens almost instantly if I start to download something. Turning the wifi off and on from the GUI or issuing ```
sudo service network-manager restart
``` does always the trick to go back online. And then I get disconnected again.. Also, the issue is only with the WiFi, the net is stable using Ethernet cable.

I've tried few suggestions like, changing the powersafe to 2 (in /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf) and the suggestion to send ARP requests by a cron job, mentioned here [https://askubuntu.com/questions/1230140/wifi-keeps-dropping-out-ubuntu-20-04-and-broadcom-wireless-adaptor](https://askubuntu.com/questions/1230140/wifi-keeps-dropping-out-ubuntu-20-04-and-broadcom-wireless-adaptor). Nothing helped so far.

I've run the wireless-info script mentioned here in the forum, let me attach the result of it.*

Could you please help me with this issue? Many thank in advance!
Daniel


*For some reason the pastebin thing didn't work for me: it seems to me that ```
ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com 
``` produces bad timing interval error for me.

---

### Post by jeremy31 on 2020-10-16
Can you change the encryption on the router to WPA2 AES only without TKIP?

---

### Post by nemethda on 2020-10-16
Thanks so much for the response! Yes, I think I've just managed to do that: WPA2-PSK is the one, correct? It comes up as encryption:AES after the change. Let me try if the issue goes away!

---

### Post by nemethda on 2020-10-16
Unfortunately the issue still exists. After few minutes I get "the site cannot be reached" followed by "No Internet" in the browser. Annoyingly in the top right corner the WiFi signs show that I'm connected and as per the Wi-Fi settings my signal strength is "Good".

---

### Post by tlee on 2020-10-22
I came across this thread because I was having a similar issue.  Attempting jeremy31's suggestion, I looked into my router's encryption settings and saw three options: none, WPA2-PSK, and WPA-PSK/WPA2-PSK.  (I didn't see anything about AES or TKIP.)  The second one was checked, so on a whim, I switched it to the third one: WPA-PSK/WPA2-PSK.  And so far, this has been working for me.  It's been a couple hours and the connection hasn't dropped.

FWIW my router is a Netgear, and I'm running 20.04 on an old Macbook Air with a Broadcom BCM43224.  The connection problem started for me yesterday, possibly the day before, I think after a kernel upgrade (to 5.4.0-52).

Hope this helps--

---

### Post by nemethda on 2020-10-26
Thanks, but for me it was originally WPA-PSK/WPA2-PSK and then I changed it to WPA2-PSK as per jeremy31's suggestion - but the issue still persists. 

With regards to AES vs TKIP: these are encryption types and as far as I know WPA2-PSK with AES encryption is more secure (and faster) and should be preferred over WPA-PSK/WPA2-PSK which probably uses TKIP + AES encryption (WPA2-PSK is mandated to use AES but WPA-TSK is not).

---

### Post by saaim on 2020-11-03
Hi Im having the same issue did you solve it somehow?

---

### Post by chili555 on 2020-11-03
Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable pwer saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddnely changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda

```
Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

### Post by valbux on 2020-11-10
I have the same issue, I followed chilli555's suggestions; will let you know if it works.

---

### Post by nemethda on 2020-11-12
Thanks for the suggestions chili555! Unfortunately I've tried all those things and the situation didn't get better at all.. After browsing the net for days I'm thinking the problem is with my wifi driver - I have a Qualcomm QCA6174 wifi chip and this type of problem seem to be recurring for a lot of users. I posted into this thread too: [https://ubuntuforums.org/showthread.php?t=2446430](https://ubuntuforums.org/showthread.php?t=2446430).

I've tried to install new firmware to fix ([https://askubuntu.com/questions/870412/wifi-dell-xps-13-9360-keeps-disconnecting-with-qca6174-802-11ac-wireless-network](https://askubuntu.com/questions/870412/wifi-dell-xps-13-9360-keeps-disconnecting-with-qca6174-802-11ac-wireless-network)) but I wasn't sure which files to rename and gave it up at some point. I feel hopeless at this point, but I'll try to look into this again. In the meantime if you have any other suggesstions that would be much appreciated!!

Thanks a lot!

---

### Post by luifernandi on 2020-11-14
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
this command work for me. i restarted my pc as soon as it connected i used the command. i will retried this again to see if this was the problem.

---

### Post by anderegg1739 on 2021-01-02
I had this problem and finally traced it down. Verizon FiOS recently switched my wifi to self organizing network to automatically switch between 2G and 5G instead of them being two different ssid's.  I could not change this on my FiOS router.  I had to change if from myVerizon login.  Once I disabled self organizing networks, I have not been prompted for wifi password.  Prior, this was happening almost continuously.  I think this feature has been rolling out slowly.  Perhaps others will find this helpful.

---

### Post by ddiepo on 2021-01-20
I've been struggling with this same problem with my Qualcomm Atheros QCA6174 chip in my dell latitude.  I noticed that if I leave a ping job running to my router I didn't experience the problem.  However, it is very intermittent, and I haven't pinned it down to any particular errors logged on my local system.  So I suspect my issue may be with the arp on the router, and I'm trying the arp via cron to see if that works for me.  I posted a suggestion on the [arp thread]("https://askubuntu.com/questions/1230140/wifi-keeps-dropping-out-ubuntu-20-04-and-broadcom-wireless-adaptor") for an improvement to that solution.  However, this seems like such a hack.

I can say that I have a nearly identical laptop with an Intel wireless adapter (in fact, I cloned that system onto the problem laptop) and that system has no problems with wifi staying rock solid all day long.  There's no significant software or configuration differences between the two (both are Ubuntu 20.04, up-to-date, etc.).  I also have a dual-boot to windows 10, and although I rarely use it, I've never noticed a problem there.

---

### Post by kali99 on 2021-02-21
In all previous Ubuntu versions I had the same problem with my Wi-Fi. I have fixed the Wi-Fi issue by creating a new config file in folder 

*/etc/NetworkManager/conf.d/*

Create there the config file

*wifi.scan-rand-mac-address.conf*

copy the following content into it:

[B][device]
wifi.scan-rand-mac-address=no[/B]

Then restart your network via:
 
*$> sudo service network-manager restart*

For further information, see also: [https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing](https://askubuntu.com/questions/902992/ubuntu-gnome-17-04-wi-fi-not-working-mac-address-keeps-changing)

---

### Post by nemethda on 2021-03-05
Thanks for the suggestion, but for me this doesn't work... it took 10 seconds for the connection to drop.

---

### Post by nemethda on 2021-03-28
Hello,

I'm still trying to figure it out if it's possible to fix my wireless issues. 2 weeks ago I spent a weekend at my parent's house and I noticed that my connection was not dropping at all. Not even once in 2 days. I run the wireless-info script there with working wifi and then I run it again here at home, where the issue is constant. Can anyone please look at the diagnostic files and help me figure out what's causing this?

I'm thinking of trying other Linux distros and see if the wireless issues would go away - but on the other hand since wifi worked on another network, is it possible that something is going on with my router?

Could anyone please advise?
Thanks
Daniel

---

### Post by chili555 on 2021-03-28
> is it possible that something is going on with my router?
Exactly!

Please start your own new question and I or one of my esteemed colleagues will be happy to help.

Here is a hint: [https://askubuntu.com/questions/1321818/install-drivers-for-wifi-card-ax200-wie7265/1322139#1322139](https://askubuntu.com/questions/1321818/install-drivers-for-wifi-card-ax200-wie7265/1322139#1322139)

> Your wireless may be struggling because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

---

### Post by nemethda on 2021-03-28
Thanks Chili555!

Actually I opened this thread originally.. but of course I'm happy to open a new question if that's needed. If that's the case in which category should I post it in?

Thanks
Daniel

---

### Post by chili555 on 2021-03-28
> **nemethda said:**
> Thanks Chili555!

Actually I opened this thread originally.. but of course I'm happy to open a new question if that's needed. If that's the case in which category should I post it in?

Thanks
DanielPardon my misstep, please. I mistakenly posted with haste.

As my "shoot first, get the facts later" post implies, please try renaming the 2.4 and 5 gHz segments of your router and I'm pretty confident that the drops caused by roaming will be resolved.

---

### Post by praseodym on 2021-03-31
Alternatively, add the MAC address of the respective AP in the **BSSID** section of your networkmanager profile

---

### Post by nemethda on 2021-04-03
Thanks praseoym for your suggestion too! I've tried that too but finally ended up naming the two access points differently. That's somewhat more transparent to me, although this way none of my devices can roam anymore, if my understanding is correct.

So after renaming the APs, I've tried to connect with the 5GHz segment. As soon as I started to download something, the speed of the connection went down to 0 and then I got disconnected. However with the 2.4 GHz network, so far so good! I'll need to test this more but this is encouraging.

I'm attaching a screenshot of my current wireless configuration. It seems that for the 5 GHz segment, I can only choose between these modes:

[LIST]
[*]802.11a/n/ac mixed (currently selected)
[*]802.11n/ac
[*]802.11ac
[/LIST]

While for the 2.4GHz connection I can select 802.11b/g/n mixed mode, which I think is the one, suggested by chilli555. Is this normal / expected that this mode is not available for 5 GHz? Sorry if this is a stupid question, but I have no expertise in this area.. Also for the channel width: is it worth tying to fix the channel as 20 MHz for the 5 GHz connection as well? Could the problem be the current 20/40/80 MHz setting? I did look at setting the channel manually too (channels 1, 6 or 11 are only available for the 2.4 GHz signal as far as I can see) but I haven't changed the default 'auto' setting yet. 

Anyway thanks for all the help!! For sure I should have looked at chili555's suggestion earlier, but somehow I missed the router config bit back than :)
Daniel

---

### Post by chili555 on 2021-04-03
> Is this normal / expected that this mode is not available for 5 GHz? 

The corresponding modes for 5 gHz are 802.11a/n/ac. If you can’t find any place to select it, then don’t worry. We can only fine-tune what is tuneable.

> Also for the channel width: is it worth tying to fix the channel as 20 MHz for the 5 GHz connection as well? Could the problem be the current 20/40/80 MHz setting? 

I suggest that you leave that alone for now. Let’s revisit later if needed.

> I did look at setting the channel manually too (channels 1, 6 or 11 are only available for the 2.4 GHz signal as far as I can see) but I haven't changed the default 'auto' setting yet.

I think this step is crucial; however, let’s go deeper. First, let’s see what nearby routers are set to use. From the terminal:

```
nmcli device wifi list
```

In my case, I see that all of my neighbors are using channel 11 in the 2.4 gHz band. I use channel 1.

In the 5 gHz band, one neighbor uses channel 36; I’ll use 149.

You can find out the channels that your wireless card supports with:

```
sudo iw list 
```

Here is a sample from my machine:

```
                        * 5180 MHz [36] (22.0 dBm) (no IR)
			* 5200 MHz [40] (22.0 dBm) (no IR)
			* 5220 MHz [44] (22.0 dBm) (no IR)
			* 5240 MHz [48] (22.0 dBm) (no IR)
			* 5260 MHz [52] (22.0 dBm) (no IR, radar detection)
			* 5280 MHz [56] (22.0 dBm) (no IR, radar detection)
			* 5300 MHz [60] (22.0 dBm) (no IR, radar detection)
			* 5320 MHz [64] (22.0 dBm) (no IR, radar detection)
			* 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
			* 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
			* 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
			* 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
			* 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
			* 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
			* 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
			* 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
			* 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
			* 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
			* 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
			* 5720 MHz [144] (22.0 dBm) (no IR, radar detection)
			* 5745 MHz [149] (22.0 dBm) (no IR)
			* 5765 MHz [153] (22.0 dBm) (no IR)
			* 5785 MHz [157] (22.0 dBm) (no IR)
			* 5805 MHz [161] (22.0 dBm) (no IR)
```

Then compare the available frequencies on your router. I also suggest that you avoid the channels marked ‘radar detection.'

As you see, in my example, channel 149 doesn’t mention radar detection, isn’t in use by my neighbors and is available on my router.

Best of all, a fixed channel in either 2.4 or 5 gHz band, doesn’t require your wireless device and Network Manager to continuously try to find an ever-changing channel. In both my personal and forums experience, auto channel select doesn’t work well, at all.

[https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection/1311177](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection/1311177)

---

### Post by nemethda on 2021-04-04
Thanks [COLOR=#000000]chili555!

I can choose between [/COLOR][COLOR=#000000]802.11a/n/ac mixed, [/COLOR][COLOR=#000000]802.11n/ac and [/COLOR][COLOR=#000000]802.11ac modes for the 5 GHz signal, but for the time being I left it on the default which is [/COLOR][COLOR=#000000]802.11a/n/ac mixed. As you advised, I didn't change the channel width either.[/COLOR]

[COLOR=#000000]I've been looking at the nmcli command [/COLOR][COLOR=#000000]a lot[/COLOR][COLOR=#000000], but in my case the results are quite random: I can see quite a lot of networks and they are clearly hopping from channel to channel all the time. I created a little script to visualize them, but at the end of the day the result changes so often I don't think it matters much.. I selected channel 1 for the 2.4 band and channel 48 for the 5 Ghz band. I looked at the supported channels as you suggested thanks very much for the tip![/COLOR]

[COLOR=#000000]I'll test these new settings out now. Unfortunately yesterday, my connection started to drop again and even worse, I experienced some bad crashes too. After connection started to drop, I used the Ethernet cable again - but when I tried the wireless again (removing the cable), the network manager crashed and my machine was not responding to anything. Looking at syslog and dmesg I see long tracebacks and firmware crashes for [/COLOR]ath10k_pci.. This happened two times yesterday.

I'll report back on the status after the fix channel selection is applied!!
Thanks for all the help
Daniel

---

### Post by chili555 on 2021-04-04
> firmware crashes for ath10k_pci..Ah, haa!! Let's address that next. Please run and post:

```
sudo dmesg | grep ath
sudo dpkg -s linux-firmware | grep Version
```Here is an interesting post: [https://bugzilla.kernel.org/show_bug.cgi?id=205311#c8](https://bugzilla.kernel.org/show_bug.cgi?id=205311#c8) Please try:

```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Any improvement?

---

### Post by nemethda on 2021-04-04
Sure!

```

sudo dmesg | grep ath
[    7.484646] systemd[1]: /lib/systemd/system/dbus.socket:5: ListenStream= references a path below legacy directory /var/run/, updating /var/run/dbus/system_bus_socket &#8594; /run/dbus/system_bus_socket; please update the unit file accordingly.
[    7.546906] systemd[1]: /lib/systemd/system/docker.socket:6: ListenStream= references a path below legacy directory /var/run/, updating /var/run/docker.sock &#8594; /run/docker.sock; please update the unit file accordingly.
[    8.015078] ath10k_pci 0000:04:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    8.337225] ath10k_pci 0000:04:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
[    8.337227] ath10k_pci 0000:04:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    8.337675] ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.4.4.1-00140-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1
[    8.402288] ath10k_pci 0000:04:00.0: board_file api 2 bmi_id N/A crc32 4ac0889b
[    8.561331] ath10k_pci 0000:04:00.0: htt-ver 3.60 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    8.620404] Modules linked in: fjes(+) amd64_edac_mod(-) nvidia_drm(POE) edac_mce_amd nvidia_modeset(POE) kvm_amd kvm nvidia(POE) crct10dif_pclmul ghash_clmulni_intel aesni_intel crypto_simd cryptd glue_helper snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg ath10k_pci snd_hda_codec ath10k_core snd_hda_core snd_hwdep uvcvideo btusb btrtl videobuf2_vmalloc amdgpu input_leds rapl ath btbcm videobuf2_memops snd_pcm btintel serio_raw bluetooth efi_pstore joydev snd_seq_midi videobuf2_v4l2 snd_seq_midi_event hid_multitouch iommu_v2 videobuf2_common mac80211 snd_rawmidi gpu_sched videodev ecdh_generic snd_seq ecc acer_wmi mc ttm sparse_keymap wmi_bmof k10temp snd_seq_device cfg80211 snd_timer drm_kms_helper cec snd i2c_algo_bit rc_core fb_sys_fops syscopyarea libarc4 sysfillrect soundcore sysimgblt ccp mac_hid acer_wireless sch_fq_codel parport_pc ppdev lp drm parport ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj usbhid
[    8.701653] ath: EEPROM regdomain: 0x6c
[    8.701655] ath: EEPROM indicates we should expect a direct regpair map
[    8.701657] ath: Country alpha2 being used: 00
[    8.701658] ath: Regpair used: 0x6c
[    8.711167] ath10k_pci 0000:04:00.0 wlp4s0: renamed from wlan0
[  169.676627] audit: type=1107 audit(1617519783.125:58): pid=951 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.12" pid=16127 label="snap.snap-store.ubuntu-software" peer_pid=953 peer_label="unconfined"
[  170.352371] audit: type=1107 audit(1617519783.801:59): pid=951 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.9" pid=16127 label="snap.snap-store.ubuntu-software" peer_pid=976 peer_label="unconfined"
[  170.352837] audit: type=1107 audit(1617519783.801:60): pid=951 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=16127 label="snap.snap-store.ubuntu-software" peer_pid=976 peer_label="unconfined"
[  170.374327] audit: type=1107 audit(1617519783.825:61): pid=951 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.9" pid=16127 label="snap.snap-store.ubuntu-software" peer_pid=976 peer_label="unconfined"
[  170.374684] audit: type=1107 audit(1617519783.825:62): pid=951 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.9" pid=16127 label="snap.snap-store.ubuntu-software" peer_pid=976 peer_label="unconfined"
[ 1489.345553] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x110198 flags=0x0020]
[ 1489.345565] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xa9a0004 flags=0x0020]
[ 1489.345573] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xa9b0004 flags=0x0020]
[ 1489.345580] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xf000000 flags=0x0020]
[ 1489.345586] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x860efd14 flags=0x0020]
[ 1706.574263] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[ 1706.574271] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[ 1706.574274] ath10k_pci 0000:04:00.0: failed to start hw scan: -110
[ 1746.769577] ath10k_pci 0000:04:00.0: wmi command 12289 timeout, restarting hardware
[ 1746.769586] ath10k_pci 0000:04:00.0: failed to start hw scan: -11
[ 1746.780212] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[ 1749.817642] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[ 1752.842181] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[ 1752.842190] ath10k_pci 0000:04:00.0: failed to wait for target init: -110
[ 1753.192206] ath10k_pci 0000:04:00.0: device successfully recovered
[ 3878.706265] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x110180 flags=0x0020]
[ 3878.706275] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x860efd14 flags=0x0020]
[ 3878.706283] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x10 flags=0x0020]
[ 3878.706290] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xf000000 flags=0x0020]
[ 3938.619086] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[ 3938.619093] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[ 3938.619096] ath10k_pci 0000:04:00.0: failed to start hw scan: -110
[ 3987.770305] ath10k_pci 0000:04:00.0: wmi command 12289 timeout, restarting hardware
[ 3987.770312] ath10k_pci 0000:04:00.0: failed to start hw scan: -11
[ 3987.780925] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[ 3988.225268] ath10k_pci 0000:04:00.0: device successfully recovered
[ 7275.029442] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x110180 flags=0x0020]
[ 7275.029454] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x860efd14 flags=0x0020]
[ 7275.029463] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x10 flags=0x0020]
[ 7275.029471] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xf000000 flags=0x0020]
[ 7316.803661] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[ 7316.803667] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[ 7316.803669] ath10k_pci 0000:04:00.0: failed to start hw scan: -110
[ 7361.603527] ath10k_pci 0000:04:00.0: wmi command 12289 timeout, restarting hardware
[ 7361.603539] ath10k_pci 0000:04:00.0: failed to start hw scan: -11
[ 7361.633977] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[ 7362.082646] ath10k_pci 0000:04:00.0: device successfully recovered
[ 9538.626862] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[ 9538.626869] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[ 9538.626872] ath10k_pci 0000:04:00.0: failed to start hw scan: -110
[ 9548.606840] ath10k_pci 0000:04:00.0: wmi command 12289 timeout, restarting hardware
[ 9548.606850] ath10k_pci 0000:04:00.0: failed to start hw scan: -11
[ 9548.633302] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[ 9551.680206] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[ 9554.707277] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[ 9554.707282] ath10k_pci 0000:04:00.0: failed to wait for target init: -110
[ 9554.708642] ath10k_pci 0000:04:00.0: failed to start hw scan: -108
[ 9554.708685] Modules linked in: rfcomm vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ccm aufs cmac algif_hash algif_skcipher af_alg bnep overlay nls_iso8859_1 nvidia_uvm(OE) nvidia_drm(POE) edac_mce_amd nvidia_modeset(POE) kvm_amd kvm nvidia(POE) crct10dif_pclmul ghash_clmulni_intel aesni_intel crypto_simd cryptd glue_helper snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg ath10k_pci snd_hda_codec ath10k_core snd_hda_core snd_hwdep uvcvideo btusb btrtl videobuf2_vmalloc amdgpu input_leds rapl ath btbcm videobuf2_memops snd_pcm btintel serio_raw bluetooth efi_pstore joydev snd_seq_midi videobuf2_v4l2 snd_seq_midi_event hid_multitouch iommu_v2 videobuf2_common mac80211 snd_rawmidi gpu_sched videodev ecdh_generic snd_seq ecc acer_wmi mc ttm sparse_keymap wmi_bmof k10temp snd_seq_device cfg80211 snd_timer drm_kms_helper cec snd i2c_algo_bit rc_core fb_sys_fops syscopyarea libarc4 sysfillrect soundcore sysimgblt ccp mac_hid acer_wireless
[ 9555.048239] ath10k_pci 0000:04:00.0: device successfully recovered
[16561.934959] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x1101ac flags=0x0020]
[16561.934973] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x860efd14 flags=0x0020]
[16561.934982] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xc flags=0x0020]
[16561.934991] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x16d76d8 flags=0x0020]
[16561.935000] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0xf000000 flags=0x0020]
[16561.935009] ath10k_pci 0000:04:00.0: AMD-Vi: Event logged [IO_PAGE_FAULT domain=0x000e address=0x16d7700 flags=0x0020]
[16611.624256] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[16611.624263] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[16611.624266] ath10k_pci 0000:04:00.0: failed to start hw scan: -110
[16618.535736] ath10k_pci 0000:04:00.0: wmi command 12289 timeout, restarting hardware
[16618.535748] ath10k_pci 0000:04:00.0: failed to start hw scan: -11
[16618.582877] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[16619.014982] ath10k_pci 0000:04:00.0: device successfully recovered

```


```

sudo dpkg -s linux-firmware | grep Version
Version: 1.187.10

```

The firmware crash that I mentioned..that I saw in syslog yesterday. I'm attaching the bit that I saved for myself - sorry if this is irrelevant! But the logs in them very similar to the ones you linked, and I do have the exact same wifi chipset as well. However the powersave is already disabled for me.

Another issue of mine that I've already edited /etc/default/crda file to set my REGDOMAIN appropriately but when I issue

```
[COLOR=#242729][FONT=Consolas]sudo iw reg get[/FONT][/COLOR]
```
..it's still unset (00) - I think this is coming up in the logs too.

I've found one of your earlier [post]("https://askubuntu.com/questions/819830/sudo-iw-reg-get-still-shows-country-00-after-updating-etc-default-crda)") regarding this but not sure if those suggestions are still applicable?
Thanks!!

PS.: Today so far so good: I'm on wifi and the connection has been stable so far..

---

### Post by nemethda on 2021-04-05
In the meantime, I think I managed to set the regdomain. I re-read your older post and used the steps described here  ([https://synaptica.info/2020/06/26/ubuntu-20-04-rc-local-start-a-process-after-boot/](https://synaptica.info/2020/06/26/ubuntu-20-04-rc-local-start-a-process-after-boot/)) to setup rc.local with the appropriate command.

Now after reboot I can see that it run:
```
$ sudo systemctl status rc-local
 rc-local.service - /etc/rc.local Compatibility
     Loaded: loaded (/lib/systemd/system/rc-local.service; enabled-runtime; vendor preset: enabled)
    Drop-In: /usr/lib/systemd/system/rc-local.service.d
             &#9492;&#9472;debian.conf
     Active: active (exited) since Mon 2021-04-05 13:29:26 CEST; 27min ago
       Docs: man:systemd-rc-local-generator(8)
    Process: 3304 ExecStart=/etc/rc.local start (code=exited, status=0/SUCCESS)


ápr 05 13:29:26 daniel-Nitro-AN515-43 systemd[1]: Starting /etc/rc.local Compatibility...
ápr 05 13:29:26 daniel-Nitro-AN515-43 systemd[1]: Started /etc/rc.local Compatibility.


```

and the regdomain is set:
```
$ sudo iw reg getglobal
country HU: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A), NO-OUTDOOR, AUTO-BW
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS, AUTO-BW
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (5725 - 5875 @ 80), (N/A, 13), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)



```

In dmesg output I still see the same output though:

```
$ dmesg -T | grep -i "ath" | egrep "regdomain|Country"
[h ápr  5 13:29:18 2021] ath: EEPROM regdomain: 0x6c
[h ápr  5 13:29:18 2021] ath: Country alpha2 being used: 00
```

Looking at this link: [https://wireless.wiki.kernel.org/en/users/drivers/ath](https://wireless.wiki.kernel.org/en/users/drivers/ath) -> the above output is might be OK?

---

### Post by chili555 on 2021-04-05
First of all, I’ve examined your crash log and it says this, in part:

> WARNING: CPU: 7 PID: 708 at drivers/gpu/drm/amd/amdgpu/../display/dc/core/dc_link.c:2546 dc_link_set_backlight_level+0x92/0xf0 [amdgpu]

RIP: 0010:dc_link_set_backlight_level+0x92/0xf0 [amdgpu]

amdgpu_dm_backlight_update_status+0xb9/0xd0 [amdgpu]

In short, the crash is related to amdgpu, your graphics driver. I have no experience in graphics and I suggest that you ask here:

[https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331)

As to the ath10k firmware crash, it seems to be a well-known issue. I haven’t yet found a permanent, repeatable solution. I do notice however, that the firmware that crashes is:

> ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.4.4.1-[COLOR="#FF0000"]00140[/COLOR]-QCARMSWPZ-1 api 6 features wowlan,ignore-otp,mfp crc32 29eb8ca1

The firmware has been recently updated:

[https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/log/ath10k/QCA6174/hw3.0](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/log/ath10k/QCA6174/hw3.0)

 > update firmware-6.bin to WLAN.RM.4.4.1-[COLOR="#FF0000"]00157[/COLOR]-QCARMSWPZ-1

In other words, version 00140 was upgraded to 00157. Let’s try that firmware and see if there is any improvement. From the terminal:

```
cd /usr/lib/firmware/ath10k/QCA6174/hw3.0
sudo mv firmware-6.bin firmware-6.bak
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/ath10k/QCA6174/hw3.0/firmware-6.bin

```
Reboot and tell us if there is any change.

> and the regdomain is set:
$ sudo iw reg getglobal
country HU: DFS-ETSI

I think that’s fine as is.

---

### Post by nemethda on 2021-04-07
Thanks for looking at the logs! I'll look into graphics driver issue separately.

I installed the new [COLOR=#000000]ath10k firmware as you suggested, let you know how it goes.

[/COLOR]The current wifi situation is, that the 2.4 is mostly stable, but sometimes still disconnects. And when it does, usually I got into a situation which renders the laptop completely unresponsive. The 5Ghz network is unusable, as soon I connect to it drops.

Yesterday I checked dmesg right after I started to get timeout issues:
```
[k ápr  6 21:17:53 2021] ath10k_warn: 8 callbacks suppressed[k ápr  6 21:17:53 2021] ath10k_pci 0000:04:00.0: wmi command 16387 timeout, restarting hardware
[k ápr  6 21:17:53 2021] ath10k_pci 0000:04:00.0: failed to set 5g txpower 20: -11
[k ápr  6 21:17:53 2021] ath10k_pci 0000:04:00.0: failed to setup tx power 20: -11
[k ápr  6 21:17:53 2021] ath10k_pci 0000:04:00.0: failed to recalc tx power: -11
[k ápr  6 21:17:53 2021] wlp4s0: deauthenticating from ac:22:05:29:da:6e by local choice (Reason: 3=DEAUTH_LEAVING)
[k ápr  6 21:17:53 2021] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[k ápr  6 21:17:56 2021] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to wait for target init: -110
[k ápr  6 21:17:59 2021] ieee80211 phy0: Hardware restart was requested
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to flush transmit queue (skip 1 ar-state 2): 1250
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to delete peer ac:22:05:29:da:6e for vdev 0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to recalculate rts/cts prot for vdev 0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to set cts protection for vdev 0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to set erp slot for vdev 0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to set preamble for vdev 0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to down vdev 0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to submit vdev param txbf 0x0: -108
[k ápr  6 21:17:59 2021] ath10k_pci 0000:04:00.0: failed to recalc txbf for vdev 0: -108
```

After this, network manager crashed and I wasn't able to restart it (not from GUI neither from the terminal). I was trying to do:
```
sudo service network-manager restart
```

But the prompt just hanged in the terminal and on the GUI I got the below notification on the WiFi part of Settings:
> "Oops, something has gone wrong. Please contact your software vendor. NetworkManager needs to be running"

Meanwhile logs in dmesg:
```
[k ápr  6 21:21:46 2021] INFO: task kworker/1:3:491 blocked for more than 120 seconds.[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] kworker/1:3     D    0   491      2 0x00004000
[k ápr  6 21:21:46 2021] Workqueue: ipv6_addrconf addrconf_verify_work
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  ? __switch_to+0x157/0x450
[k ápr  6 21:21:46 2021]  ? __switch_to_asm+0x36/0x70
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  rtnl_lock+0x15/0x20
[k ápr  6 21:21:46 2021]  addrconf_verify_work+0xe/0x20
[k ápr  6 21:21:46 2021]  process_one_work+0x1e8/0x3b0
[k ápr  6 21:21:46 2021]  worker_thread+0x4d/0x3f0
[k ápr  6 21:21:46 2021]  kthread+0x114/0x150
[k ápr  6 21:21:46 2021]  ? process_one_work+0x3b0/0x3b0
[k ápr  6 21:21:46 2021]  ? kthread_park+0x90/0x90
[k ápr  6 21:21:46 2021]  ret_from_fork+0x22/0x30
[k ápr  6 21:21:46 2021] INFO: task wpa_supplicant:967 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] wpa_supplicant  D    0   967      1 0x00000000
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  rtnl_lock+0x15/0x20
[k ápr  6 21:21:46 2021]  nl80211_pre_doit+0x104/0x1b0 [cfg80211]
[k ápr  6 21:21:46 2021]  genl_rcv_msg+0x184/0x320
[k ápr  6 21:21:46 2021]  ? genl_start+0x140/0x140
[k ápr  6 21:21:46 2021]  netlink_rcv_skb+0x50/0x120
[k ápr  6 21:21:46 2021]  genl_rcv+0x29/0x40
[k ápr  6 21:21:46 2021]  netlink_unicast+0x1a8/0x250
[k ápr  6 21:21:46 2021]  netlink_sendmsg+0x23b/0x460
[k ápr  6 21:21:46 2021]  ? aa_sk_perm+0x43/0x1b0
[k ápr  6 21:21:46 2021]  sock_sendmsg+0x65/0x70
[k ápr  6 21:21:46 2021]  ____sys_sendmsg+0x218/0x290
[k ápr  6 21:21:46 2021]  ? copy_msghdr_from_user+0x5c/0x90
[k ápr  6 21:21:46 2021]  ? fsnotify_grab_connector+0x51/0x90
[k ápr  6 21:21:46 2021]  ? fsnotify_destroy_marks+0x27/0xf0
[k ápr  6 21:21:46 2021]  ___sys_sendmsg+0x81/0xc0
[k ápr  6 21:21:46 2021]  ? evict+0x14c/0x1b0
[k ápr  6 21:21:46 2021]  ? iput+0x1a3/0x210
[k ápr  6 21:21:46 2021]  ? _cond_resched+0x19/0x30
[k ápr  6 21:21:46 2021]  ? __cgroup_bpf_run_filter_setsockopt+0xae/0x2d0
[k ápr  6 21:21:46 2021]  ? _cond_resched+0x19/0x30
[k ápr  6 21:21:46 2021]  __sys_sendmsg+0x62/0xb0
[k ápr  6 21:21:46 2021]  __x64_sys_sendmsg+0x1f/0x30
[k ápr  6 21:21:46 2021]  do_syscall_64+0x49/0xc0
[k ápr  6 21:21:46 2021]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[k ápr  6 21:21:46 2021] RIP: 0033:0x7f2476868747
[k ápr  6 21:21:46 2021] RSP: 002b:00007fff23b0ce78 EFLAGS: 00000246 ORIG_RAX: 000000000000002e
[k ápr  6 21:21:46 2021] RAX: ffffffffffffffda RBX: 000055a27f71a5b0 RCX: 00007f2476868747
[k ápr  6 21:21:46 2021] RDX: 0000000000000000 RSI: 00007fff23b0ceb0 RDI: 0000000000000006
[k ápr  6 21:21:46 2021] RBP: 000055a27f783bf0 R08: 0000000000000004 R09: 00007f2476930b80
[k ápr  6 21:21:46 2021] R10: 00007fff23b0cf84 R11: 0000000000000246 R12: 000055a27f71a4c0
[k ápr  6 21:21:46 2021] R13: 00007fff23b0ceb0 R14: 00007fff23b0cf84 R15: 000055a27f786300
[k ápr  6 21:21:46 2021] INFO: task ThreadPoolForeg:253493 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] ThreadPoolForeg D    0 253493  15592 0x00000000
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  __netlink_dump_start+0x7e/0x280
[k ápr  6 21:21:46 2021]  rtnetlink_rcv_msg+0x224/0x370
[k ápr  6 21:21:46 2021]  ? __schedule+0x39c/0xa60
[k ápr  6 21:21:46 2021]  ? rtnl_xdp_prog_skb+0x70/0x70
[k ápr  6 21:21:46 2021]  ? rtnl_xdp_prog_skb+0x70/0x70
[k ápr  6 21:21:46 2021]  ? rtnl_calcit.isra.0+0x100/0x100
[k ápr  6 21:21:46 2021]  netlink_rcv_skb+0x50/0x120
[k ápr  6 21:21:46 2021]  rtnetlink_rcv+0x15/0x20
[k ápr  6 21:21:46 2021]  netlink_unicast+0x1a8/0x250
[k ápr  6 21:21:46 2021]  netlink_sendmsg+0x23b/0x460
[k ápr  6 21:21:46 2021]  ? aa_sk_perm+0x43/0x1b0
[k ápr  6 21:21:46 2021]  sock_sendmsg+0x65/0x70
[k ápr  6 21:21:46 2021]  __sys_sendto+0x113/0x190
[k ápr  6 21:21:46 2021]  ? __prepare_exit_to_usermode+0x76/0x210
[k ápr  6 21:21:46 2021]  __x64_sys_sendto+0x29/0x30
[k ápr  6 21:21:46 2021]  do_syscall_64+0x49/0xc0
[k ápr  6 21:21:46 2021]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[k ápr  6 21:21:46 2021] RIP: 0033:0x7f56382fd844
[k ápr  6 21:21:46 2021] RSP: 002b:00007f562e917850 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
[k ápr  6 21:21:46 2021] RAX: ffffffffffffffda RBX: 00007f562e918970 RCX: 00007f56382fd844
[k ápr  6 21:21:46 2021] RDX: 0000000000000014 RSI: 00007f562e918970 RDI: 0000000000000031
[k ápr  6 21:21:46 2021] RBP: 0000000000000000 R08: 00007f562e918914 R09: 000000000000000c
[k ápr  6 21:21:46 2021] R10: 0000000000000000 R11: 0000000000000293 R12: 00007f562e918914
[k ápr  6 21:21:46 2021] R13: 00007f562e919040 R14: 00007f562e918930 R15: 0000000000000031
[k ápr  6 21:21:46 2021] INFO: task ThreadPoolForeg:253713 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] ThreadPoolForeg D    0 253713  15592 0x00000000
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  __netlink_dump_start+0x7e/0x280
[k ápr  6 21:21:46 2021]  rtnetlink_rcv_msg+0x224/0x370
[k ápr  6 21:21:46 2021]  ? rtnl_xdp_prog_skb+0x70/0x70
[k ápr  6 21:21:46 2021]  ? rtnl_xdp_prog_skb+0x70/0x70
[k ápr  6 21:21:46 2021]  ? rtnl_calcit.isra.0+0x100/0x100
[k ápr  6 21:21:46 2021]  netlink_rcv_skb+0x50/0x120
[k ápr  6 21:21:46 2021]  rtnetlink_rcv+0x15/0x20
[k ápr  6 21:21:46 2021]  netlink_unicast+0x1a8/0x250
[k ápr  6 21:21:46 2021]  netlink_sendmsg+0x23b/0x460
[k ápr  6 21:21:46 2021]  ? aa_sk_perm+0x43/0x1b0
[k ápr  6 21:21:46 2021]  sock_sendmsg+0x65/0x70
[k ápr  6 21:21:46 2021]  __sys_sendto+0x113/0x190
[k ápr  6 21:21:46 2021]  ? __prepare_exit_to_usermode+0x76/0x210
[k ápr  6 21:21:46 2021]  __x64_sys_sendto+0x29/0x30
[k ápr  6 21:21:46 2021]  do_syscall_64+0x49/0xc0
[k ápr  6 21:21:46 2021]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[k ápr  6 21:21:46 2021] RIP: 0033:0x7f5639bbd844
[k ápr  6 21:21:46 2021] RSP: 002b:00007f562485cd70 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
[k ápr  6 21:21:46 2021] RAX: ffffffffffffffda RBX: 00007f562485cdc0 RCX: 00007f5639bbd844
[k ápr  6 21:21:46 2021] RDX: 0000000000000011 RSI: 00007f562485cdc0 RDI: 0000000000000020
[k ápr  6 21:21:46 2021] RBP: 0000000000000000 R08: 00007f562485cdb0 R09: 000000000000000c
[k ápr  6 21:21:46 2021] R10: 0000000000000000 R11: 0000000000000293 R12: 00007f562485d210
[k ápr  6 21:21:46 2021] R13: aaaaaaaaaaaaaaaa R14: 00007f562485cdb0 R15: 00007f562485cfa8
[k ápr  6 21:21:46 2021] INFO: task kworker/4:2:95769 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] kworker/4:2     D    0 95769      2 0x00004000
[k ápr  6 21:21:46 2021] Workqueue: events linkwatch_event
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  ? newidle_balance+0x21c/0x3c0
[k ápr  6 21:21:46 2021]  ? __switch_to+0x157/0x450
[k ápr  6 21:21:46 2021]  ? __switch_to_asm+0x36/0x70
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  rtnl_lock+0x15/0x20
[k ápr  6 21:21:46 2021]  linkwatch_event+0xe/0x30
[k ápr  6 21:21:46 2021]  process_one_work+0x1e8/0x3b0
[k ápr  6 21:21:46 2021]  worker_thread+0x4d/0x3f0
[k ápr  6 21:21:46 2021]  kthread+0x114/0x150
[k ápr  6 21:21:46 2021]  ? process_one_work+0x3b0/0x3b0
[k ápr  6 21:21:46 2021]  ? kthread_park+0x90/0x90
[k ápr  6 21:21:46 2021]  ret_from_fork+0x22/0x30
[k ápr  6 21:21:46 2021] INFO: task kworker/6:1:242365 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] kworker/6:1     D    0 242365      2 0x00004000
[k ápr  6 21:21:46 2021] Workqueue: events disconnect_work [cfg80211]
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  ? set_next_entity+0xb5/0x200
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  rtnl_lock+0x15/0x20
[k ápr  6 21:21:46 2021]  disconnect_work+0x17/0xd0 [cfg80211]
[k ápr  6 21:21:46 2021]  process_one_work+0x1e8/0x3b0
[k ápr  6 21:21:46 2021]  worker_thread+0x4d/0x3f0
[k ápr  6 21:21:46 2021]  kthread+0x114/0x150
[k ápr  6 21:21:46 2021]  ? process_one_work+0x3b0/0x3b0
[k ápr  6 21:21:46 2021]  ? kthread_park+0x90/0x90
[k ápr  6 21:21:46 2021]  ret_from_fork+0x22/0x30
[k ápr  6 21:21:46 2021] INFO: task kworker/4:0:252864 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] kworker/4:0     D    0 252864      2 0x00004000
[k ápr  6 21:21:46 2021] Workqueue: events rfkill_global_led_trigger_worker
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  ? psi_group_change+0x46/0x230
[k ápr  6 21:21:46 2021]  ? __switch_to_asm+0x42/0x70
[k ápr  6 21:21:46 2021]  ? __switch_to_asm+0x36/0x70
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  rfkill_global_led_trigger_worker+0x15/0xb0
[k ápr  6 21:21:46 2021]  process_one_work+0x1e8/0x3b0
[k ápr  6 21:21:46 2021]  worker_thread+0x4d/0x3f0
[k ápr  6 21:21:46 2021]  kthread+0x114/0x150
[k ápr  6 21:21:46 2021]  ? process_one_work+0x3b0/0x3b0
[k ápr  6 21:21:46 2021]  ? kthread_park+0x90/0x90
[k ápr  6 21:21:46 2021]  ret_from_fork+0x22/0x30
[k ápr  6 21:21:46 2021] INFO: task kworker/4:1:253679 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] kworker/4:1     D    0 253679      2 0x00004000
[k ápr  6 21:21:46 2021] Workqueue: events_freezable ieee80211_restart_work [mac80211]
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  ? _cond_resched+0x19/0x30
[k ápr  6 21:21:46 2021]  ? flush_workqueue+0x196/0x430
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  rtnl_lock+0x15/0x20
[k ápr  6 21:21:46 2021]  ieee80211_restart_work+0x5d/0xf0 [mac80211]
[k ápr  6 21:21:46 2021]  process_one_work+0x1e8/0x3b0
[k ápr  6 21:21:46 2021]  worker_thread+0x4d/0x3f0
[k ápr  6 21:21:46 2021]  kthread+0x114/0x150
[k ápr  6 21:21:46 2021]  ? process_one_work+0x3b0/0x3b0
[k ápr  6 21:21:46 2021]  ? kthread_park+0x90/0x90
[k ápr  6 21:21:46 2021]  ret_from_fork+0x22/0x30
[k ápr  6 21:21:46 2021] INFO: task pool:253733 blocked for more than 120 seconds.
[k ápr  6 21:21:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:21:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:21:46 2021] pool            D    0 253733  10940 0x00000000
[k ápr  6 21:21:46 2021] Call Trace:
[k ápr  6 21:21:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:21:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:21:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:21:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:21:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:21:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:21:46 2021]  __netlink_dump_start+0x7e/0x280
[k ápr  6 21:21:46 2021]  rtnetlink_rcv_msg+0x224/0x370
[k ápr  6 21:21:46 2021]  ? rtnl_fill_ifinfo+0x1030/0x1030
[k ápr  6 21:21:46 2021]  ? rtnl_fill_ifinfo+0x1030/0x1030
[k ápr  6 21:21:46 2021]  ? rtnl_calcit.isra.0+0x100/0x100
[k ápr  6 21:21:46 2021]  netlink_rcv_skb+0x50/0x120
[k ápr  6 21:21:46 2021]  rtnetlink_rcv+0x15/0x20
[k ápr  6 21:21:46 2021]  netlink_unicast+0x1a8/0x250
[k ápr  6 21:21:46 2021]  netlink_sendmsg+0x23b/0x460
[k ápr  6 21:21:46 2021]  ? aa_sk_perm+0x43/0x1b0
[k ápr  6 21:21:46 2021]  sock_sendmsg+0x65/0x70
[k ápr  6 21:21:46 2021]  __sys_sendto+0x113/0x190
[k ápr  6 21:21:46 2021]  ? __prepare_exit_to_usermode+0x76/0x210
[k ápr  6 21:21:46 2021]  __x64_sys_sendto+0x29/0x30
[k ápr  6 21:21:46 2021]  do_syscall_64+0x49/0xc0
[k ápr  6 21:21:46 2021]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[k ápr  6 21:21:46 2021] RIP: 0033:0x7fbbdbd65844
[k ápr  6 21:21:46 2021] RSP: 002b:00007fbbd2ffb6e0 EFLAGS: 00000293 ORIG_RAX: 000000000000002c
[k ápr  6 21:21:46 2021] RAX: ffffffffffffffda RBX: 00007fbbd2ffc880 RCX: 00007fbbdbd65844
[k ápr  6 21:21:46 2021] RDX: 0000000000000014 RSI: 00007fbbd2ffc7b0 RDI: 0000000000000008
[k ápr  6 21:21:46 2021] RBP: 0000000000000000 R08: 00007fbbd2ffc770 R09: 000000000000000c
[k ápr  6 21:21:46 2021] R10: 0000000000000000 R11: 0000000000000293 R12: 00007fbbd2ffc770
[k ápr  6 21:21:46 2021] R13: 00007fbbd2ffc7b0 R14: 00007ffde18ef520 R15: 00007fbbd2ffb720
[k ápr  6 21:23:46 2021] INFO: task kworker/1:3:491 blocked for more than 241 seconds.
[k ápr  6 21:23:46 2021]       Tainted: P        W  OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[k ápr  6 21:23:46 2021] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[k ápr  6 21:23:46 2021] kworker/1:3     D    0   491      2 0x00004000
[k ápr  6 21:23:46 2021] Workqueue: ipv6_addrconf addrconf_verify_work
[k ápr  6 21:23:46 2021] Call Trace:
[k ápr  6 21:23:46 2021]  __schedule+0x394/0xa60
[k ápr  6 21:23:46 2021]  schedule+0x55/0xc0
[k ápr  6 21:23:46 2021]  schedule_preempt_disabled+0xe/0x10
[k ápr  6 21:23:46 2021]  __mutex_lock.isra.0+0x17d/0x4e0
[k ápr  6 21:23:46 2021]  ? __switch_to+0x157/0x450
[k ápr  6 21:23:46 2021]  ? __switch_to_asm+0x36/0x70
[k ápr  6 21:23:46 2021]  __mutex_lock_slowpath+0x13/0x20
[k ápr  6 21:23:46 2021]  mutex_lock+0x32/0x40
[k ápr  6 21:23:46 2021]  rtnl_lock+0x15/0x20
[k ápr  6 21:23:46 2021]  addrconf_verify_work+0xe/0x20
[k ápr  6 21:23:46 2021]  process_one_work+0x1e8/0x3b0
[k ápr  6 21:23:46 2021]  worker_thread+0x4d/0x3f0
[k ápr  6 21:23:46 2021]  kthread+0x114/0x150
[k ápr  6 21:23:46 2021]  ? process_one_work+0x3b0/0x3b0
[k ápr  6 21:23:46 2021]  ? kthread_park+0x90/0x90
[k ápr  6 21:23:46 2021]  ret_from_fork+0x22/0x30
```

I tried this few times then the computer got totally unresponsive. I tried ctrl+alt+f3 to get a different console, but nothing. I also tried the Alt + SysRq combination and then type REISUB (I've found this method here: [https://www.maketecheasier.com/4-ways-to-get-yourself-out-of-a-ubuntu-crash/](https://www.maketecheasier.com/4-ways-to-get-yourself-out-of-a-ubuntu-crash/)), but that didn't work either. Although it's possible I just did it wrong..anyway I had to turn off manually the machine at the end.

---

### Post by chili555 on 2021-04-07
Please see this thread: [https://bbs.archlinux.org/viewtopic.php?id=262456](https://bbs.archlinux.org/viewtopic.php?id=262456)

> INFO: task kworker/1:1H:117 blocked for more than 122 seconds.It appears in your log, too.

```
Yeah, I have also not experienced any freezes since I uninstalled the 'xf86-video-intel' package. I checked on my other arch install and the 'xf86-video-intel' package was not installed so it's probably this package that was causing the issue.
```What does this tell us?

```
sudo dpkg -s xserver-xorg-video-intel | grep Status
```

-----------------------------------

Note: Synaptic says: The use of this driver is discouraged if your hw is new enough (ca.
2007 and newer). You can try uninstalling this driver and let the
server use its builtin modesetting driver instead.

---

### Post by nemethda on 2021-04-08
Here's my output:

```
$ sudo dpkg -s xserver-xorg-video-intel | grep Status
Status: install ok installed

```

---

### Post by chili555 on 2021-04-08
Synaptic also says:

> This package is built from the X.org xf86-video-intel driver module.Although I am a bit skeptical, as an experiment, I removed the package from my own machine and upon reboot, there was no ill effect, that is, no effect at all. I do not, however, use the ath10k_pci wireless device. 

If you are certain that your hardware is new enough (ca. 2007 and newer), you can try uninstalling this driver:

```
sudo apt purge  xserver-xorg-video-intel
```Reboot and show us:

```
dmesg  | grep ath
```

---

### Post by nemethda on 2021-04-09
I bought the laptop last year (around September) so it should be new enough. In hindsight I should have done a better research because it seems that this model (Acer Nitro AN515-43-R40X) is not the best choice for using Linux.

I uninstalled the driver, after reboot that's the output of dmesg:
```
~$ dmesg -T | grep ath
[p ápr  9 14:27:24 2021] systemd[1]: /lib/systemd/system/dbus.socket:5: ListenStream= references a path below legacy directory /var/run/, updating /var/run/dbus/system_bus_socket &#8594; /run/dbus/system_bus_socket; please update the unit file accordingly.
[p ápr  9 14:27:24 2021] systemd[1]: /lib/systemd/system/docker.socket:6: ListenStream= references a path below legacy directory /var/run/, updating /var/run/docker.sock &#8594; /run/docker.sock; please update the unit file accordingly.
[p ápr  9 14:27:25 2021] ath10k_pci 0000:04:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0: invalid firmware magic
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 11ad:0807
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0: board_file api 2 bmi_id N/A crc32 4ac0889b
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[p ápr  9 14:27:26 2021] ath: EEPROM regdomain: 0x6c
[p ápr  9 14:27:26 2021] ath: EEPROM indicates we should expect a direct regpair map
[p ápr  9 14:27:26 2021] ath: Country alpha2 being used: 00
[p ápr  9 14:27:26 2021] ath: Regpair used: 0x6c
[p ápr  9 14:27:26 2021] ath10k_pci 0000:04:00.0 wlp4s0: renamed from wlan0
[p ápr  9 14:27:26 2021] Modules linked in: fjes(-) nvidia_uvm(OE) nvidia_drm(POE) nvidia_modeset(POE) edac_mce_amd snd_hda_codec_realtek kvm_amd snd_hda_codec_generic ledtrig_audio kvm crct10dif_pclmul ghash_clmulni_intel snd_hda_codec_hdmi aesni_intel nvidia(POE) crypto_simd cryptd glue_helper snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep snd_pcm uvcvideo ath10k_pci videobuf2_vmalloc videobuf2_memops ath10k_core videobuf2_v4l2 btusb videobuf2_common btrtl btbcm ath joydev rapl snd_seq_midi btintel snd_seq_midi_event videodev amdgpu bluetooth snd_rawmidi input_leds mc acer_wmi mac80211 hid_multitouch ecdh_generic sparse_keymap snd_seq serio_raw efi_pstore wmi_bmof ecc iommu_v2 gpu_sched snd_seq_device ttm snd_timer k10temp i2c_algo_bit snd drm_kms_helper cfg80211 cec ccp soundcore rc_core fb_sys_fops syscopyarea sysfillrect libarc4 sysimgblt mac_hid acer_wireless sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj usbhid
[p ápr  9 14:28:04 2021] audit: type=1107 audit(1617971285.251:58): pid=922 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/NetworkManager" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.9" pid=5945 label="snap.snap-store.ubuntu-software" peer_pid=923 peer_label="unconfined"
[p ápr  9 14:28:05 2021] audit: type=1107 audit(1617971286.263:59): pid=922 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.8" pid=5945 label="snap.snap-store.ubuntu-software" peer_pid=939 peer_label="unconfined"
[p ápr  9 14:28:05 2021] audit: type=1107 audit(1617971286.267:60): pid=922 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.8" pid=5945 label="snap.snap-store.ubuntu-software" peer_pid=939 peer_label="unconfined"
[p ápr  9 14:28:05 2021] audit: type=1107 audit(1617971286.291:61): pid=922 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.8" pid=5945 label="snap.snap-store.ubuntu-software" peer_pid=939 peer_label="unconfined"
[p ápr  9 14:28:05 2021] audit: type=1107 audit(1617971286.291:62): pid=922 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.8" pid=5945 label="snap.snap-store.ubuntu-software" peer_pid=939 peer_label="unconfined"
```

The amdgpu failures are indeed all over my dmesg output and I've been reading a lot of posts regarding this as you suggested. So far no luck, but I'm also impacted by problems like this: [https://ubuntuforums.org/showthread.php?t=2459895&highlight=amdgpu](https://ubuntuforums.org/showthread.php?t=2459895&highlight=amdgpu) - suspending the machine doesn't work for me either, since the very first day. Anyway, I don't want to spam this issue with another one.

Thanks a lot for still looking at my issue!!
Daniel

---

### Post by chili555 on 2021-04-09
We see none of the previous ath10k_pci errors. I assume that the firmware update has fixed the wireless issue.

Without seeing the lines in dmesg appearing just before and after this: Modules linked in: fjes(-) , I can't tell if it's related to the wireless driver ath10k_pci or not. I strongly suspect that it's related to amdgpu.

If the experts over on General Help can help fix that, I think your issues are resolved.

---

### Post by nemethda on 2021-04-09
Thanks [COLOR=#000000]chili555!

I see that dmesg looks [/COLOR][COLOR=#000000]cleaner [/COLOR][COLOR=#000000]after startup, although these lines (after another reboot) still coming up - are these OK?
```

[p ápr  9 16:51:50 2021] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[p ápr  9 16:51:50 2021] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[p ápr  9 16:51:50 2021] ath10k_pci 0000:04:00.0: failed to start hw scan: -110

```

And actually, while I'm using ethernet cable I get these messages in dmesg:
[/COLOR]```
[p ápr  9 17:51:51 2021] ath10k_pci 0000:04:00.0: wmi command 24579 timeout, restarting hardware
[p ápr  9 17:51:51 2021] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[p ápr  9 17:51:54 2021] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to wait for target init: -110
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to flush transmit queue (skip 1 ar-state 2): 1250
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to delete peer ac:22:05:29:da:6e for vdev 0: -108
[p ápr  9 17:51:57 2021] Modules linked in: rfcomm vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ccm aufs cmac algif_hash algif_skcipher af_alg bnep overlay nvidia_uvm(OE) nvidia_drm(POE) nvidia_modeset(POE) nls_iso8859_1 nvidia(POE) edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep ath10k_pci snd_pcm ath10k_core uvcvideo amdgpu snd_seq_midi snd_seq_midi_event ath snd_rawmidi kvm_amd btusb mac80211 btrtl btbcm btintel kvm joydev snd_seq videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 crct10dif_pclmul videobuf2_common ghash_clmulni_intel snd_seq_device bluetooth cfg80211 snd_timer videodev iommu_v2 aesni_intel gpu_sched crypto_simd ttm cryptd ecdh_generic glue_helper ecc mc rapl libarc4 ccp snd drm_kms_helper cec i2c_algo_bit input_leds hid_multitouch rc_core serio_raw acer_wmi efi_pstore fb_sys_fops sparse_keymap syscopyarea soundcore sysfillrect wmi_bmof sysimgblt k10temp mac_hid acer_wireless
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to recalculate rts/cts prot for vdev 0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to set cts protection for vdev 0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to set erp slot for vdev 0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to set preamble for vdev 0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to down vdev 0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to submit vdev param txbf 0x0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to recalc txbf for vdev 0: -108
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: device successfully recovered

```[COLOR=#000000]

This is the log around the "modules linked in" segment and I think you are right, problems are related to amdgpu it seems. 
```
~$ dmesg -T | grep -C 35 "Modules linked in:"
[p ápr  9 16:50:13 2021] kfd kfd: added device 1002:15d8
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: SE 1, SH per SE 1, CU per SH 11, active_cu_number 10
[p ápr  9 16:50:13 2021] [drm] fb mappable at 0x3EFBCA000
[p ápr  9 16:50:13 2021] [drm] vram apper at 0x3EF000000
[p ápr  9 16:50:13 2021] [drm] size 8294400
[p ápr  9 16:50:13 2021] [drm] fb depth is 24
[p ápr  9 16:50:13 2021] [drm]    pitch is 7680
[p ápr  9 16:50:13 2021] fbcon: amdgpudrmfb (fb0) is primary device
[p ápr  9 16:50:13 2021] Console: switching to colour frame buffer device 240x67
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: fb0: amdgpudrmfb frame buffer device
[p ápr  9 16:50:13 2021] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  450.102.04  Tue Dec 29 06:51:23 UTC 2020
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring gfx uses VM inv eng 0 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring sdma0 uses VM inv eng 0 on hub 1
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring vcn_dec uses VM inv eng 1 on hub 1
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 4 on hub 1
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 5 on hub 1
[p ápr  9 16:50:13 2021] amdgpu 0000:05:00.0: amdgpu: ring jpeg_dec uses VM inv eng 6 on hub 1
[p ápr  9 16:50:13 2021] EDAC amd64: F17h_M10h detected (node 0).
[p ápr  9 16:50:13 2021] EDAC amd64: Node 0: DRAM ECC disabled.
[p ápr  9 16:50:13 2021] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  450.102.04  Tue Dec 29 06:44:25 UTC 2020
[p ápr  9 16:50:13 2021] ath10k_pci 0000:04:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[p ápr  9 16:50:13 2021] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[p ápr  9 16:50:13 2021] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 1
[p ápr  9 16:50:13 2021] [drm] Initialized amdgpu 3.38.0 20150101 for 0000:05:00.0 on minor 0
[p ápr  9 16:50:13 2021] ------------[ cut here ]------------
[p ápr  9 16:50:13 2021] WARNING: CPU: 4 PID: 682 at drivers/gpu/drm/amd/amdgpu/../display/dc/core/dc_link.c:2546 dc_link_set_backlight_level+0x92/0xf0 [amdgpu]
[p ápr  9 16:50:13 2021] Modules linked in: nvidia_drm(POE) nvidia_modeset(POE) nls_iso8859_1 nvidia(POE) edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep ath10k_pci snd_pcm ath10k_core uvcvideo amdgpu snd_seq_midi snd_seq_midi_event ath snd_rawmidi kvm_amd btusb mac80211 btrtl btbcm btintel kvm joydev snd_seq videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 crct10dif_pclmul videobuf2_common ghash_clmulni_intel snd_seq_device bluetooth cfg80211 snd_timer videodev iommu_v2 aesni_intel gpu_sched crypto_simd ttm cryptd ecdh_generic glue_helper ecc mc rapl libarc4 ccp snd drm_kms_helper cec i2c_algo_bit input_leds hid_multitouch rc_core serio_raw acer_wmi efi_pstore fb_sys_fops sparse_keymap syscopyarea soundcore sysfillrect wmi_bmof sysimgblt k10temp mac_hid acer_wireless sch_fq_codel parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_logitech_hidpp hid_logitech_dj usbhid hid_generic
[p ápr  9 16:50:13 2021]  crc32_pclmul nvme ahci xhci_pci libahci i2c_piix4 r8169 xhci_pci_renesas nvme_core realtek i2c_hid video hid wmi
[p ápr  9 16:50:13 2021] CPU: 4 PID: 682 Comm: systemd-backlig Tainted: P           OE     5.8.0-48-generic #54~20.04.1-Ubuntu
[p ápr  9 16:50:13 2021] Hardware name: Acer Nitro AN515-43/Octavia_PKS, BIOS V1.08 12/24/2019
[p ápr  9 16:50:13 2021] RIP: 0010:dc_link_set_backlight_level+0x92/0xf0 [amdgpu]
[p ápr  9 16:50:13 2021] Code: 30 03 00 00 31 c0 48 8d 96 c0 01 00 00 48 8b 0a 48 85 c9 74 06 4c 3b 61 08 74 22 83 c0 01 48 81 c2 c8 04 00 00 83 f8 06 75 e3 <0f> 0b 45 31 ff 5b 44 89 f8 41 5c 41 5d 41 5e 41 5f 5d c3 48 98 48
[p ápr  9 16:50:13 2021] RSP: 0018:ffffb397c14ebd98 EFLAGS: 00010246
[p ápr  9 16:50:13 2021] RAX: 0000000000000006 RBX: ffff916fd9380000 RCX: 0000000000000000
[p ápr  9 16:50:13 2021] RDX: ffff916fd6fc1e70 RSI: ffff916fd6fc0000 RDI: 0000000000000004
[p ápr  9 16:50:13 2021] RBP: ffffb397c14ebdc0 R08: 000000000000003a R09: 0000000000000002
[p ápr  9 16:50:13 2021] R10: 000000000000000a R11: f000000000000000 R12: ffff916fdccb5400
[p ápr  9 16:50:13 2021] R13: 0000000000000000 R14: 00000000000049bd R15: 0000000000004901
[p ápr  9 16:50:13 2021] FS:  00007f9eb2633980(0000) GS:ffff916fe0b00000(0000) knlGS:0000000000000000
[p ápr  9 16:50:13 2021] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[p ápr  9 16:50:13 2021] CR2: 000055ad3a6c60a8 CR3: 00000003dbb34000 CR4: 00000000003406e0
[p ápr  9 16:50:13 2021] Call Trace:
[p ápr  9 16:50:13 2021]  amdgpu_dm_backlight_update_status+0xb9/0xd0 [amdgpu]
[p ápr  9 16:50:13 2021]  backlight_device_set_brightness+0x6b/0xd0
[p ápr  9 16:50:13 2021]  brightness_store+0x61/0x80
[p ápr  9 16:50:13 2021]  dev_attr_store+0x17/0x30
[p ápr  9 16:50:13 2021]  sysfs_kf_write+0x3e/0x50
[p ápr  9 16:50:13 2021]  kernfs_fop_write+0xda/0x1b0
[p ápr  9 16:50:13 2021]  vfs_write+0xc9/0x200
[p ápr  9 16:50:13 2021]  ksys_write+0x67/0xe0
[p ápr  9 16:50:13 2021]  __x64_sys_write+0x1a/0x20
[p ápr  9 16:50:13 2021]  do_syscall_64+0x49/0xc0
[p ápr  9 16:50:13 2021]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
[p ápr  9 16:50:13 2021] RIP: 0033:0x7f9eb34e11e7
[p ápr  9 16:50:13 2021] Code: 64 89 02 48 c7 c0 ff ff ff ff eb bb 0f 1f 80 00 00 00 00 f3 0f 1e fa 64 8b 04 25 18 00 00 00 85 c0 75 10 b8 01 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 51 c3 48 83 ec 28 48 89 54 24 18 48 89 74 24
[p ápr  9 16:50:13 2021] RSP: 002b:00007ffd6e91e548 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
[p ápr  9 16:50:13 2021] RAX: ffffffffffffffda RBX: 0000000000000003 RCX: 00007f9eb34e11e7
[p ápr  9 16:50:13 2021] RDX: 0000000000000003 RSI: 00007ffd6e91e600 RDI: 0000000000000004
[p ápr  9 16:50:13 2021] RBP: 00007ffd6e91e600 R08: 0000000000000003 R09: 0000000000000000
[p ápr  9 16:50:13 2021] R10: 0000000000000000 R11: 0000000000000246 R12: 0000000000000003
[p ápr  9 16:50:13 2021] R13: 000055ad3a6b02d0 R14: 0000000000000003 R15: 00007f9eb35bc8a0
[p ápr  9 16:50:13 2021] ---[ end trace 6d74529606dca6de ]---
```

I'll try to find solution on the other forums related to amdgpu. [/COLOR]

---

### Post by chili555 on 2021-04-09
> [drm] [COLOR="#FF0000"]Initialized amdgpu[/COLOR] 3.38.0 20150101 for 0000:05:00.0 on minor 0
------------[ cut here ]------------
WARNING: CPU: 4 PID: 682 at [COLOR="#FF0000"]drivers/gpu/drm/amd/amdgpu[/COLOR]/../display/dc/core/dc_link.c:2546 dc_link_set_backlight_level+0x92/0xf0 [amdgpu]
[Modules linked in: nvidia_drm(POE) nvidia_modeset(POE) nls_iso8859_1 nvidia(POE) edac_mce_amd snd_hda_codec_realtek snd_hda_codec_generic ledtrig_audio snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core snd_hwdep ath10k_pci snd_pcm ath10k_core uvcvideo amdgpu snd_seq_midi 
<snip>As we suspected.

> And actually, while I'm using ethernet cable I get these messages in dmesg:

```
[p ápr  9 17:51:51 2021] ath10k_pci 0000:04:00.0: wmi command 24579 timeout, restarting hardware
[p ápr  9 17:51:51 2021] ath10k_pci 0000:04:00.0: failed to read hi_board_data address: -16
[p ápr  9 17:51:54 2021] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to receive initialized event from target: 00000000
[p ápr  9 17:51:57 2021] ath10k_pci 0000:04:00.0: failed to wait for target init: -110
<snip>
```Was the wireless turned off at Network Manager, ideally Airplane Mode, when using the ethernet?

> still coming up - are these OK?
Code:
[p ápr  9 16:51:50 2021] ath10k_pci 0000:04:00.0: failed to receive scan abortion completion: timed out
[p ápr  9 16:51:50 2021] ath10k_pci 0000:04:00.0: failed to stop scan: -110
[p ápr  9 16:51:50 2021] ath10k_pci 0000:04:00.0: failed to start hw scan: -110

It is hard to tell. It isn't listed as a warning or error. We don't know if the system recovered. If, in spite of these messages, the wireless connects and passes traffic, then I'd say they are trivial.

Frankly, until amdgpu stops crashing, I'm not sure there is anything else to do with wireless.

---

### Post by nemethda on 2021-04-10
> [COLOR=#000000]Was the wireless turned off at Network Manager, ideally Airplane Mode, when using the ethernet?[/COLOR]

No it wasn't.

> [COLOR=#000000]Frankly, until amdgpu stops crashing, I'm not sure there is anything else to do with wireless.[/COLOR]

Understood, thanks!

---

### Post by fortifor44 on 2021-10-13
hi nemethda, What's your the current status regarding your issue?; Any improvements/solutions by now? I am curious, as I have been suffering from the same issue almost two years now...

---

