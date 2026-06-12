---
title: "Wifi connected but no internet at certain (university) network ubuntu 16.04"
date: 2017-04-30
forum: Networking &amp; Wireless
---

### Post by blackbunny13 on 2017-04-30
After installing ubuntu 16.04 I can use wifi properly with my home router but get problem at university network. It shows that wifi is connected but actually no internet.


1.I have followed the following link but no internet.
[https://askubuntu.com/questions/653355/wireless-connected-but-no-internet-access?newreg=fc6caecf4eee4ed984d428025d07e05e](https://askubuntu.com/questions/653355/wireless-connected-but-no-internet-access?newreg=fc6caecf4eee4ed984d428025d07e05e)



**my university guideline to connect wifi......[https://www.urz.ovgu.de/urz/Unsere+Leistungen/Datennetz/Campus/WLAN/Anleitungen-p-1072.html](https://www.urz.ovgu.de/urz/Unsere+Leistungen/Datennetz/Campus/WLAN/Anleitungen-p-1072.html)


Result of the following commands are given below


   ```
 ping 8.8.8.8
    cat /etc/lsb-release; uname -a
    lspci -nnk | grep -iA2 net
    iwconfig
    rfkill list all
    lsmod


    2.ping 8.8.8.8
        ping 8.8.8.8 connect network is unreachable
    
    3.cat /etc/lsb-release; uname -a
        DISTRIB_ID=Ubuntu
        DISTRIB_RELEASE=16.04
        DISTRIB_CODENAME=xenial
        DISTRIB_DESCRIPTION="Ubuntu 16.04.2 LTS"
        Linux andypc 4.8.0-49-generic #52~16.04.1-Ubuntu SMP Thu Apr 20 10:55:59 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
    
    4.lspci -nnk | grep -iA2 net
    01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    	Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:3833]
    	Kernel driver in use: r8169
    	Kernel modules: r8169
    02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    	Subsystem: Lenovo Device [17aa:0901]
    	Kernel driver in use: ath10k_pci
    4.iwconfig
    wlp2s0    IEEE 802.11  ESSID:"WRS55"  
              Mode:Managed  Frequency:2.457 GHz  Access Point: 98:DE:D0:E5:6B:64   
              Bit Rate=1 Mb/s   Tx-Power=20 dBm   
              Retry short limit:7   RTS thr:off   Fragment thr:off
              Power Management:on
              Link Quality=52/70  Signal level=-58 dBm  
              Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
              Tx excessive retries:87  Invalid misc:1326   Missed beacon:0
    
    enp1s0    no wireless extensions.
    
    lo        no wireless extensions.
    
    5.rfkill list all
    0: ideapad_wlan: Wireless LAN
    	Soft blocked: no
    	Hard blocked: no
    1: ideapad_bluetooth: Bluetooth
    	Soft blocked: yes
    	Hard blocked: no
    2: hci0: Bluetooth
    	Soft blocked: yes
    	Hard blocked: no
    3: phy0: Wireless LAN
    	Soft blocked: no
    	Hard blocked: no
    
    6.lsmod
    Module                  Size  Used by
    ccm                    20480  2
    rfcomm                 77824  0
    bnep                   20480  2
    arc4                   16384  2
    rtsx_usb_ms            20480  0
    memstick               20480  1 rtsx_usb_ms
    uvcvideo               90112  0
    snd_soc_skl            65536  0
    snd_soc_skl_ipc        45056  1 snd_soc_skl
    intel_rapl             20480  0
    videobuf2_vmalloc      16384  1 uvcvideo
    videobuf2_memops       16384  1 videobuf2_vmalloc
    snd_soc_sst_ipc        16384  1 snd_soc_skl_ipc
    snd_soc_sst_dsp        32768  1 snd_soc_skl_ipc
    x86_pkg_temp_thermal    16384  0
    videobuf2_v4l2         24576  1 uvcvideo
    intel_powerclamp       16384  0
    snd_hda_ext_core       28672  1 snd_soc_skl
    snd_hda_codec_hdmi     45056  1
    snd_soc_sst_match      16384  1 snd_soc_skl
    videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
    snd_hda_codec_realtek    86016  1
    snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
    snd_soc_core          233472  1 snd_soc_skl
    videodev              180224  3 uvcvideo,videobuf2_core,videobuf2_v4l2
    coretemp               16384  0
    snd_compress           20480  1 snd_soc_core
    kvm                   598016  0
    ac97_bus               16384  1 snd_soc_core
    irqbypass              16384  1 kvm
    snd_pcm_dmaengine      16384  1 snd_soc_core
    media                  40960  2 uvcvideo,videodev
    snd_hda_intel          36864  5
    snd_hda_codec         135168  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
    snd_hda_core           86016  7 snd_hda_intel,snd_hda_codec,snd_hda_ext_core,snd_soc_skl,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
    ath10k_pci             45056  0
    ath10k_core           335872  1 ath10k_pci
    crct10dif_pclmul       16384  0
    crc32_pclmul           16384  0
    ghash_clmulni_intel    16384  0
    snd_hwdep              16384  1 snd_hda_codec
    aesni_intel           167936  4
    snd_pcm               110592  9 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_ext_core,snd_hda_core,snd_soc_skl,snd_hda_codec_hdmi,snd_soc_core
    aes_x86_64             20480  1 aesni_intel
    snd_seq_midi           16384  0
    snd_seq_midi_event     16384  1 snd_seq_midi
    ath                    32768  1 ath10k_core
    lrw                    16384  1 aesni_intel
    glue_helper            16384  1 aesni_intel
    hci_uart               98304  0
    btusb                  45056  0
    btrtl                  16384  1 btusb
    btqca                  16384  1 hci_uart
    btbcm                  16384  2 hci_uart,btusb
    snd_rawmidi            32768  1 snd_seq_midi
    btintel                16384  2 hci_uart,btusb
    ablk_helper            16384  1 aesni_intel
    cryptd                 24576  3 ablk_helper,ghash_clmulni_intel,aesni_intel
    bluetooth             557056  33 btrtl,hci_uart,btintel,btqca,bnep,btbcm,rfcomm,btusb
    mac80211              761856  1 ath10k_core
    cfg80211              581632  3 mac80211,ath,ath10k_core
    snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
    joydev                 20480  0
    input_leds             16384  0
    snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
    snd_timer              32768  2 snd_seq,snd_pcm
    ideapad_laptop         24576  0
    serio_raw              16384  0
    sparse_keymap          16384  1 ideapad_laptop
    ucsi                   16384  0
    tpm_crb                16384  0
    mei_me                 40960  0
    snd                    86016  22 snd_compress,snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_soc_core,snd_pcm
    mei                   102400  1 mei_me
    shpchp                 36864  0
    intel_lpss_acpi        16384  0
    soundcore              16384  1 snd
    mac_hid                16384  0
    intel_pch_thermal      16384  0
    intel_lpss             16384  1 intel_lpss_acpi
    acpi_pad               24576  0
    parport_pc             32768  0
    ppdev                  20480  0
    lp                     20480  0
    parport                49152  3 lp,parport_pc,ppdev
    autofs4                40960  2
    rtsx_usb_sdmmc         28672  0
    rtsx_usb               24576  2 rtsx_usb_sdmmc,rtsx_usb_ms
    amdkfd                139264  1
    amd_iommu_v2           20480  1 amdkfd
    radeon               1515520  1
    i915                 1314816  105
    psmouse               139264  0
    ttm                   102400  1 radeon
    i2c_algo_bit           16384  2 radeon,i915
    drm_kms_helper        167936  2 radeon,i915
    syscopyarea            16384  1 drm_kms_helper
    sysfillrect            16384  1 drm_kms_helper
    sysimgblt              16384  1 drm_kms_helper
    fb_sys_fops            16384  1 drm_kms_helper
    drm                   368640  9 radeon,i915,ttm,drm_kms_helper
    r8169                  81920  0
    ahci                   36864  3
    mii                    16384  1 r8169
    libahci                32768  1 ahci
    wmi                    16384  1 ideapad_laptop
    pinctrl_sunrisepoint    28672  0
    i2c_hid                20480  0
    video                  40960  2 i915,ideapad_laptop
    hid                   122880  1 i2c_hid
    pinctrl_intel          20480  1 pinctrl_sunrisepoint
    fjes                   28672  0
```

---

### Post by wildmanne39 on 2017-05-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by QIII on 2017-05-01
The link to your Uni's instructions further links here:  [https://www.urz.ovgu.de/Unsere+Leistungen/Datennetz/Campus/WLAN/Anleitungen/Linux+802_1X-p-1810.html](https://www.urz.ovgu.de/Unsere+Leistungen/Datennetz/Campus/WLAN/Anleitungen/Linux+802_1X-p-1810.html)

Have you satisfied those requirements?  

It would probably be much easier for you to speak directly to technical support at your Uni.  They are more likely to be able to help.  They know the network.

---

### Post by blackbunny13 on 2017-05-01
```
 I will follow your instruction
```

yes I satisfy all these requirements but no improvement. Tested with 2 different routers ....yes be connected with 2 different routers and get internet connection but same problem with university network

found this link (is it applicable for me?)
[https://askubuntu.com/questions/820828/connected-to-wifi-but-no-internet-16-04?rq=1](https://askubuntu.com/questions/820828/connected-to-wifi-but-no-internet-16-04?rq=1)

sudo cat /etc/network/interfaces gives result of 
```
 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
 
```

and "route -n" gave result 
```
 Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         141.44.220.1    0.0.0.0         UG    600    0        0 wlp2s0
10.1.1.1        141.44.220.1    255.255.255.255 UGH   600    0        0 wlp2s0
141.44.220.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
 
```

but do not know how to implement.

In a huge frustration

emailed them

---

### Post by Bucky Ball on 2017-05-01
> **QIII said:**
> It would probably be much easier for you to speak directly to technical support at your Uni.  They are more likely to be able to help.  They know the network.

+1. Definitely.

---

### Post by QIII on 2017-05-01
Bitte!  Wenden Sie sich an das Rechenzentrum.

---

### Post by blackbunny13 on 2017-05-01
emailed them and waiting for response

---

### Post by blackbunny13 on 2017-05-03
My problem is not solved yet got reply from University IT Center 
"[COLOR=#000000][FONT=Geneva]I don't get  your actual problem: You are connected to our wifi, you've got an IP address, the gateway and the DNS servers are set properly.[/FONT][/COLOR]
[COLOR=#000000][FONT=Geneva]Are you able to reach any web page?[/FONT][/COLOR]
[COLOR=#000000][FONT=Geneva]We block ICMP, so you won't get an echo response (ping) from e. g. google, but this does not mean you can't reach the Internet.[/FONT][/COLOR]"

What should I do now?

---

### Post by wildmanne39 on 2017-05-03
Please click on the wireless script in my signature and follow the directions to run it while trying to connect to the network that you are having issue with then paste the output to pastebin, then the link back here.

---

### Post by Bucky Ball on 2017-05-03
IT asked this:

> Are you able to reach any web page?

What was your answer to them and what was their reply? They are asking you directly what you are posting about here and will probably help you trouble shoot it on their system if you're not.

They've already stated you won't be able to ping out, so we could not know what other tweaks they've set up which may prevent you connecting. They'll know.

---

### Post by blackbunny13 on 2017-05-08
[https://pastebin.com/JWRZ2yDi](https://pastebin.com/JWRZ2yDi)

I have run your wireless info script when my laptop was trying to connect university wifi. Please check it.

My problem is not solved yet, eagerly waiting for your suggestion

---

### Post by blackbunny13 on 2017-05-08
I went to university IT center .... They were showing me that my PC is connected to university network...... I was showing them that I can not browse any webpage. They tried for 45 minutes but could not solve/identify the problem.

---

### Post by wildmanne39 on 2017-05-08
From what I see there are only a couple of things we can try but I am not real hopeful. How far are you from the AP because the link quality is just so low you have no internet, even though your computer is connected.

We are going to turn off power management, please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```
Reboot

I have researched your issue and in each case where it was solved the person bought a new router, there are some routers that linux do not like.

---

### Post by blackbunny13 on 2017-05-09
Thanks a lot.I tried it ....no improvement. 
I have run the following command and got some error and output of the command is in the pastebin link. 
[COLOR=#333333][FONT=Consolas]```
[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]dmesg | grep ath10k"
```[/FONT][/COLOR]
[https://pastebin.com/wXPKvs52](https://pastebin.com/wXPKvs52)

My knowledge/experience is not so much but I am still trying......I suspect that there is problem with Qualcomm Atheros Device because
 (these may not be valid reason)  when I installed ubuntu 14.04 , I got no wifi......searched and found that installing ubuntu 16.04 will solve this problem.....partially solved ...but new problem(this thread) raised 
and when I searched ....found that many people faced problem with "[SIZE=1][Broadcom Wireless Drivers]("https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers")" ......I guess "[/SIZE]Atheros Device" may have some unsolved problems

---

### Post by wildmanne39 on 2017-05-09
Yes your device has some issues, in the other output it did not show the firmware issue, I am not sure it will he4lp but we will change the firmware and see.

The reason your device did not work in 14.04 it was so new back then that the driver was not included in 14.04, but could be manually installed.

Give me a little time to get the firmware located, How far are you from the access point? are there walls and doors between the access point and your computer?
Thanks

---

### Post by wildmanne39 on 2017-05-09
Please do:
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```
Reboot and let us know if it is working, If I remember correctly this is 5ghz access point you are tying to connect too, if you can get them to say channel 40 because it is in the lower range it seems to work better.

---

### Post by blackbunny13 on 2017-05-09
I have installed firmware 1.158 through the following command because of the error (HTTP request sent, awaiting response... 404 Not Found
)......wifi did not work.....whatever thanks a lot.
```
wget https://launchpad.net/ubuntu/+source/linux-firmware/1.158/+build/9700625/+files/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb

```

I am trying in all my possible ways....if I get any improvement, I will post here

---

### Post by wildmanne39 on 2017-05-09
I just ran the commands and it showed the error then it said moved to another location and it download it, but it is a large file so it took some time.

---

### Post by blackbunny13 on 2017-05-09
```
wget https://launchpad.net/ubuntu/+source/linux-firmware/1.158/+build/9700625/+files/linux-firmware_1.158_all.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
```
I guess both are same  ....or I need to wget exactly from mirrors.kernel.org

---

### Post by wildmanne39 on 2017-05-09
Yes they are the same, please post the output of:
```
ls -al /lib/firmware/ath
dmesg | grep firmware | tail -n20
```
and the out put of the script again.
Thanks

---

### Post by blackbunny13 on 2017-05-09
please check the output
```
$ ls -al /lib/firmware/ath
ls: cannot access '/lib/firmware/ath': No such file or directory
$ dmesg | grep firmware | tail -n20
[    1.225358] i915 0000:00:02.0: Direct firmware load for i915/kbl_dmc_ver1_01.bin failed with error -2
[    1.225359] i915 0000:00:02.0: Failed to load DMC firmware [https://01.org/linuxgraphics/intel-linux-graphics-firmwares], disabling runtime power management.
[    1.232630] [drm] GuC firmware load skipped
[    1.829284] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x594f03)
[   10.153536] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:02:00.0.bin failed with error -2
[   10.153548] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   10.305475] ath10k_pci 0000:02:00.0: firmware ver WLAN.TF.1.0-00267-1 api 5 features ignore-otp crc32 79cea2c7

```

---

### Post by jeremy31 on 2017-05-09
> **wildmanne39 said:**
> I have researched your issue and in each case where it was solved the person bought a new router, there are some routers that linux do not like.

I think you are correct with this case and the ath10k device as I see
```
[ 2694.415287] ath10k_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 2694.415294] ath10k_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
```

Since the wifi equipment belongs to the University there is likely nothing we can do.

What can be done is to use a linux friendly USB dongle like the TP-Link WN722N 150 Mbps or replace the internal wifi card with one from Intel like the 7260 but you would need to contact Lenovo if you want to replace the internal card as they have a BIOS that won't allow them to boot with just any internal wifi card

---

### Post by wildmanne39 on 2017-05-09
> **jeremy31 said:**
> I think you are correct with this case and the ath10k device as I see
```
[ 2694.415287] ath10k_pci 0000:02:00.0 wlp2s0: disabling HT as WMM/QoS is not supported by the AP
[ 2694.415294] ath10k_pci 0000:02:00.0 wlp2s0: disabling VHT as WMM/QoS is not supported by the AP
```

Since the wifi equipment belongs to the University there is likely nothing we can do.

What can be done is to use a linux friendly USB dongle like the TP-Link WN722N 150 Mbps or replace the internal wifi card with one from Intel like the 7260 but you would need to contact Lenovo if you want to replace the internal card as they have a BIOS that won't allow them to boot with just any internal wifi card

Those error messages is what made be believe there is nothing we can do if there is not access to the router or replacement of it.

Thanks Jeremy31 for confirmation.

---

### Post by blackbunny13 on 2017-05-09
I will buy the router ASAP and notify you here....... thanks a lo[COLOR=#000000]t [/COLOR][SIZE=1][FONT=arial][[COLOR=#000000]QIII[/COLOR]]("https://ubuntuforums.org/member.php?u=628170")[COLOR=#000000] [/COLOR],**Bucky Ball[COLOR=#000000],[/COLOR]**[[COLOR=#000000]jeremy31[/COLOR]]("https://ubuntuforums.org/member.php?u=1924242")[COLOR=#000000] [/COLOR][/FONT][/SIZE][FONT=arial]**[COLOR=#000000]a[/COLOR]nd specially wildmanne39**[/FONT]

---

### Post by wildmanne39 on 2017-05-09
I thought it is an university router, that you do  not have access too or able to replace?

---

### Post by blackbunny13 on 2017-05-09
Yes It is university router/network and I don't have any option to replace
I thought [COLOR=#000000]Atheros wifi Device of my laptop has problem and [/COLOR][COLOR=#000000]* "TP-Link WN722N 150 Mbps"  will solve this problem (according to *[/COLOR][[COLOR=#000000]jeremy31[/COLOR]]("https://ubuntuforums.org/member.php?u=1924242")[COLOR=#000000]*)......Is not it? or I am understanding something wrong....*[/COLOR]

---

### Post by wildmanne39 on 2017-05-09
Okay that makes sense, in your last post you said your were going to get a new router so that confused me.

---

### Post by Hadaka on 2017-05-11
Hi, The wireless report shows the country code undefined, This can cause
connection failures and drops.
```
#Region: Europe/Berlin (based on set time zone)
#country 00: DFS-UNSET
```
Please Copy and Paste one line at a time to correct..
```
sudo iw reg set DE
sudo sed -i 's/=.*/=DE/' /etc/default/crda
```
The wireless routing table report indicates a server configuration with
some kind of forwarding..Flag = UGH
```
#Kernel IP routing table
#Destination     Gateway         Genmask         Flags
#10.1.1.1        141.44.220.1    255.255.255.255 UGH 
```
Please post the output of..
```
sudo ufw status
```
The wireless diagnostic report shows an active 5 Mhz connection, but the signal
to that access point is very weak.
```
#ESSID:"OvGU-802.1X"
# Quality=29/70  Signal level=-81 dBm 
```
please post the output of..
```
iwconfig
```
Please make an attemp to connect to the 2.4Mhz Guest connection.
```
# OvGU-Guest <MAC 'OvGU-Guest' [AC17]> Infra 1 2412 MHz 54 Mbit/s
```
If the connection is successful and you are able to make an internet connection,,then please do..
```
watch -n 1 cat /proc/net/wireless
```
Monitor the signal strength "Signal Quality" for while and see if there are any large swings in the numbers.
Please post the average range..i.e. 50/70... |"ctrl c" to stop the monitor
Please also post the output of..
```
cat /etc/network/interfaces
```
When complete please boot,remove any usb and wired connections,
*Verify the university connection is configured as "LEAP or PEAP" in the security tab.
then test the 5Mhz connection.
Thank You.

---

### Post by blackbunny13 on 2017-05-12
How to setup TL-WN722N at ubuntu 16.04 because can not find out instruction at tp link website...please read the content of following link

[http://forum.tp-link.com/showthread.php?96366-No-linux-drivers-available-for-TP-Link-TL-WN722N-V-2.0&highlight=TL-WN722N+linux](http://forum.tp-link.com/showthread.php?96366-No-linux-drivers-available-for-TP-Link-TL-WN722N-V-2.0&highlight=TL-WN722N+linux)

update....got one link trying
[http://www.tp-link.com/en/download/TL-WN722N.html#Driver](http://www.tp-link.com/en/download/TL-WN722N.html#Driver)

---

### Post by jeremy31 on 2017-05-12
The one I have is supported by the kernel and is shown in lsusb results as
```
Bus 003 Device 007: ID 0cf3:9271 Qualcomm Atheros Communications AR9271 802.11n
```
It uses the ath9k_htc kernel module

---

### Post by blackbunny13 on 2017-05-12
1.I have unzipped it
2.went to the folder using cd 
3.used the command sudo make install

but found this error....
```

:~/Downloads/tp/rtl8188EUS_linux_v4.3.0.8_13968.20150417$ sudo make install
"******************************************"
"NO SKRC,we will use default KSRC"
"******************************************"
install -p -m 644 8188eu.ko  /lib/modules/4.8.0-51-generic/kernel/drivers/net/wireless/
install: cannot stat '8188eu.ko': No such file or directory
Makefile:1373: recipe for target 'install' failed
make: *** [install] Error 1

```
I found no tutorial or help by googling.
Can you share any link  1.to install 2.to check and 3.how to use the [I]TP-Link WN722N  version 2 at ubuntu 16.04?
I have tried for one hour...but found nothing[/I]

---

### Post by blackbunny13 on 2017-05-12
[COLOR=#000000][COLOR=#DD4814][COLOR=#000000]dear [Hadaka]("https://ubuntuforums.org/member.php?u=1599436")[/COLOR][/COLOR] , I will try in your way after going campus tomorrow and update you about it[/COLOR]

---

### Post by jeremy31 on 2017-05-12
Can you post results for ```
lsusb
```
with the device plugged in?

If you see ```
ID 2357:010c
```
In the results, see
[https://askubuntu.com/a/912507/300665](https://askubuntu.com/a/912507/300665)

---

### Post by blackbunny13 on 2017-05-12
yes the device is plugged in and result is

```

:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:e500 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 04f2:b581 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 2357:010c  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have run the following command from the link given by you
```

sudo apt-get install git dkms
cd /usr/src
sudo git clone https://github.com/lwfinger/rtl8188eu.git
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
sudo modprobe 8188eu

```
now what should I do?

---

### Post by jeremy31 on 2017-05-12
I would ```
echo "blacklist ath10k_pci" | sudo tee /etc/modprobe.d/ath10k-blacklist.conf
```
Reboot and see how the USB device works

---

### Post by blackbunny13 on 2017-05-12
The device is working now. I will check it tomorrow at university campus network and update you.

---

### Post by blackbunny13 on 2017-05-13
[COLOR=#DD4814][COLOR=#000000]dear [Hadaka]("https://ubuntuforums.org/member.php?u=1599436")[/COLOR][/COLOR][COLOR=#000000] ,[/COLOR]Followed your instruction but no improvement
```

1.sudo ufw status
Status: inactive

2.iwconfig
wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlx18d6c71a5d9a  unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


enp1s0    no wireless extensions.


lo        no wireless extensions.

```

[COLOR=#000000]special permission/password is needed to connect to the 2.4Mhz [/COLOR][COLOR=#000000][FONT=&amp]'OvGU-Guest'. For students only [/FONT][/COLOR][COLOR=#000000][FONT=&amp]"OvGU-802.1X"[/FONT][/COLOR]

---

### Post by blackbunny13 on 2017-05-13
*[COLOR=#000000]Dear [/COLOR]*[SIZE=1][FONT=arial][COLOR=#C61919]**jeremy31,**[/COLOR][/FONT][/SIZE]*[COLOR=#000000]TP-Link WN722N is connected to university network and I can browse/download.....but getting [/COLOR]*[COLOR=#111111][FONT=Ubuntu] extremely low [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]wireless signal  with [/FONT][/COLOR]*[COLOR=#000000]TP-Link WN722N [/COLOR]*[COLOR=#111111][FONT=Ubuntu]in both of university network and home router network.[/FONT][/COLOR]

```

1.iwconfig
wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlx18d6c71a5d9a  IEEE 802.11g  ESSID:"OvGU-802.1X"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:25:5C:78:BF:90   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=15/100  Signal level=-68 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


enp1s0    no wireless extensions.


lo        no wireless extensions.


2. cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
wlx18d6c71a5d9a: 0000   27.  -64.  -256.       0      0      0      0      0        0


```

update: I am following instruction of this link 
[https://askubuntu.com/questions/389153/low-wireless-signal-with-tp-link-tl-wn725n-wifi-dongle/526113](https://askubuntu.com/questions/389153/low-wireless-signal-with-tp-link-tl-wn725n-wifi-dongle/526113)

---

### Post by jeremy31 on 2017-05-13
We can uninstall the module by Larry Finger and try one I made some changes to
```
sudo dkms uninstall 8188eu/1.0
sudo dkms remove 8188eu/1.0 --all
```


```
cd ~
git clone https://github.com/jeremyb31/rtl8188eu.git
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
```

Reboot and see if the signal strength improves

---

### Post by blackbunny13 on 2017-05-13
Everything is working fine. Thanks a lot

Update: problem started again

---

### Post by blackbunny13 on 2017-05-13
Update: T[I]P-Link WN722N was working with out executing commands of your  last post

Again network signal was low...so I tried them and....

got error!!!
```

sudo dkms remove 8188eu/1.0
Error! Invalid number of parameters passed.
Usage: remove <module>/<module-version> --all
or: remove <module>/<module-version> -k <kernel-version>

```
[/I]

---

### Post by jeremy31 on 2017-05-13
I edited the commands in the other post, they should work correctly

---

### Post by blackbunny13 on 2017-05-13
Sorry for late reply....just implemented your instructions.....device is working well.Thanks again.

---

