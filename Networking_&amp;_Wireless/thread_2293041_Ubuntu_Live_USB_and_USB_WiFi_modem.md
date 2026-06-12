---
title: "Ubuntu Live USB and USB WiFi modem"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by peter206 on 2015-09-02
As linux newbie I am desperately trying to test and then install Ubuntu on my PC. I have a simple ZTE MF60 uFi aces point/modem that works perfectly fine with internet access in any windows but not in Live USB Ubuntu. When I try to connect to my WiFi with my WEP2 password in Live USB Ubuntu it keeps asking for it over and over. It won't connect to the wifi. I tried to set up WiFi connection manually but with no success. I searched extensively on internet for proper solutions but there are no specific and clear instructions on how to fix this. Without access to internet I simply can't use Ubuntu. 

I am really fed up with windows so I would appreciate any dedicated help. Don't make me go back to the dark side.  Tell me what info do you need and I'll post it ASAP.

---

### Post by Bucky Ball on 2015-09-02
Welcome. Wireless, and graphics for that matter, will not always work 'out of the box' from a live boot. Ironically, sometimes they will work fine then you'll have problems once you install Ubuntu. 

Many drivers are included in the Ubuntu kernel, but not all. Some hardware needs third-party, proprietary drivers which, for legal reasons, cannot be included in the Ubuntu kernel, once the system is installed. For this you will need to get online with a cable (if you did that now you may be offered a driver if you do an update when online with a live session).

To start with, I suggest you boot from the live media, open a terminal, and post the output of this command between code tags (see the last link in my signature).

```
sudo lshw -C network
```

---

### Post by peter206 on 2015-09-02
Thanks for prompt response! 
Here is the output of your command. I would like to point out that I have no classic option for wired connection ( no standard UTP cable connectors ) on my USB modem with access point. Therefore I have no access to internet while in Ubuntu Live USB. However everything works fine in windows.  

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network              
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:9d:b0:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:38 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e8:de:27:67:9d:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:fe900000-fe97ffff memory:fe980000-fe98ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wwan0
       serial: ce:89:50:bd:6c:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=qmi_wwan driverversion=22-Aug-2005 firmware=WWAN/QMI device link=no multicast=yes


```

---

### Post by Bucky Ball on 2015-09-02
Odd. Perhaps post the output of the wirelessinfo script in my signature. Your wireless appears to have the correct driver installed and is enabled. I'm curious about the last entry, though. What is the device wwan0?

---

### Post by peter206 on 2015-09-02
> **Bucky Ball said:**
> What is the device wwan0?

I suspect its my usb modem. I will disconnect it from PC, run the command again and get back to you.

Yes, the last entry was my modem connected trough usb cable. I run your script but unfortunately it didn't return anything. I guess it is not working from usb drive. Can I run some commands manually for more information?

---

### Post by Bucky Ball on 2015-09-02
I'm a little confused. You had the modem plugged directly into your computer? The modem should be plugged directly to the cable or ADSL line. The modem is also an access point/router?

The modem/router should provide a wireless signal you then connect to via the wireless device on your local machine. When you right click the Network Icon, do you see any available networks? Is 'Enable Wireless' enabled there?

Leave the modem out of calculations for the moment and try to connect directly to whatever you have the network cable plugged into (the cable from the outside world that should be plugged into a modem/router/access point.

---

### Post by peter206 on 2015-09-02
I have a USB **3G - mobile internet modem** with integrated access point and router. I don't have ADSL or cable internet. You can see it in [this link]("http://www.amazon.com/ZTE-MF60-Hotspot-worldwide-T-Mobile/dp/B005IDLYK4"). 

Its never directly connected to any PC via USB since you can adjust all settings directly trough browser (http:// 192.168.0.1). As I said before everything works fine in windows machines but I simply don't know how to get it work in Ubuntu.

I am really sorry for confusion.

I would like to try manually setup my wireless connection directly in Ubuntu. Can somebody point me to a good YT video or DETAILED documentation on what to insert in edit wifi connection dialogue? Specifically I am interested in ipv4 settings and ipv6 settings. Where do i get info for BSSID, cloned MAC adress, DHCP client ID? Do I need to put that in? Additional DNS server? Additional search domains? Require ipv4 adressing for this connection to complete, routes settings. 

Please, I am desperate to switch to linux but without internet access I can't.

---

### Post by Bucky Ball on 2015-09-02
Click on the Network Manager icon and select 'Edit'. Do you see a wireless entry there? If so, edit it. If not, add one.

IPv6: Set to ignore;
IPv4: Depends if you are using a static IP address or not. You will need to find out if your modem is sending you an IP via its DHCP server. If it is set to 'Automatic', leave it like that for now. Untick 'require IPv4 addressing' if it is ticked.

Under the 'Wifi' tab set the SSID as the name of your network (which will be set in the modem/router).
Forget about BSSID and cloned mac. Not relevant for this. Mode = Intfrastructure. MTU = auto. 

Security tab: set it up with the correct security type and password.

General tab: first two options ticked.

That's it. If you want/need to use a static IP, that's straightforward, too. Ask if you hit any brick walls but you might also like to do a little research [here]("http://ubuntuforums.org/showthread.php?t=2221294") as it's about the same wireless card: product: AR9485 Wireless Network Adapter. Try running some of the commands the user there did to see if the issues are the same..

---

### Post by peter206 on 2015-09-02
> **Bucky Ball said:**
> Ask if you hit any brick walls but you might also like to do a little research [here]("http://ubuntuforums.org/showthread.php?t=2221294") as it's about the same wireless card: product: AR9485 Wireless Network Adapter. Try running some of the commands the user there did to see if the issues are the same..


Man you have no idea how much research I did to fix this. The problem I have that all solutions are custom to users hardware. Your suggested is for Asus laptop and installed Ubuntu, not Ubuntu live USB. The other problem is that everyone helping assumes you have some sort of access to internet while you troubleshoot your internet connection in Ubuntu. Like download new driver and update them. Another assumption is that everyone have Ubuntu already installed. What is killing me is that this same wireless adapter is working fine in windows 8. No problem. And I am not alone.There are a lot of people with this same ( old ) problem and it is trivial to me why this is not already fixed. 

To be bit sarcastic no wonder linux is virus free since no on is actually connected on the net. :-) 

Anyway can you please guide me to fix this adapter driver. What should I do first. Should I install Ubuntu with dual boot and then try to fix the adapter or it can be done on Live USB? While waiting for your reply i'll try these two commands:

```

sudo rfkill list all
sudo rfkill unblock all


```

Thanks for help.

---

### Post by Bucky Ball on 2015-09-03
> **peter206 said:**
> Should I install Ubuntu with dual boot and then try to fix the adapter ...

Yes. Very little point getting it going on the live USB, if you can, as on reboot you'll need to do it all again. Changes are not kept after reboot on the live media.

---

### Post by peter206 on 2015-09-03
> **Bucky Ball said:**
> Yes. Very little point getting it going on the live USB, if you can, as on reboot you'll need to do it all again. Changes are not kept after reboot on the live media.


Ok I am going to install Ubuntu on my PC now. I hope you will help me with Qualcom Atheros driver setup after install since the thread you pointed me to is specific for Asus notebooks/laptops. 

I am really looking forward to finally ditch windows and start learning Ubuntu. :-)


Thanks for your support and help.

---

### Post by Bucky Ball on 2015-09-03
Well, it makes little difference it is ASus computer on the link. The card is what we're worried about and you haven't tried what was there to see if you have the same issues with wireless. Without the wireless script it is harder to help, but we'll give it a go. As I say, from your output, the Atheros looks like it is up and running which is why I am having problems figuring why you are not connecting.

Hopefully a wireless guru can help. Good luck.

---

### Post by peter206 on 2015-09-03
Can you please explain to me how to run this Wireless Info Script. I downloaded it on installed Ubuntu and did everything from the offline step but it doesn't output anything. How can I run it manually and directly from terminal? Is there a list of commands from the script I can run manually in terminal?
  
> *[COLOR=#800000]Also, the script is NOT COMPATIBLE with "**sh**" (will produce incomplete result if run with sh). So if you have to run it via terminal, please run it without **sh** or with **bash** (e.g. - "./wireless_script" or "bash wireless_script")[/COLOR]*

---

### Post by jeremy31 on 2015-09-03
Check the wifi security setting on the ZTE device, you want WPA2-PSK only with no TKIP.  Reboot the ZTE after saving the setting and then Ubuntu should connect

---

### Post by Bucky Ball on 2015-09-03
> If you can't connect to internet -

* Download the script on another computer by right-clicking this link, and choose to "Save" the link target.
* Copy the downloaded file to your Ubuntu Desktop (see the "NOTE 2" below) and,
* run it from there as follows -

1) Right-click the downloaded file > click "Properties" > go to "Permissions" tab > tick the "Execute" checkbox > close the box.

2) Double-click the file > select "Run" in the opened dialogue box. Provide your password when asked.
[NOTE 1: Since Ubuntu 13.04, Text Files open up in text editor even if they are made executable. To change this-
Open any folder > go to Files > Preferences > Behavior tab > select "Ask each time" option under "Executable Text Files" section.]

3) A fresh new file "wireless-info.txt" (or "wireless-info.txt.tar.gz" file, if the text file size exceeds 19.5 KB) will be created in the same directory where you have run the script from. Attach it or copy-paste its contents (as described above) in your next post.

That's it. Download the file and 1,2,3. You need to look in the same folder you have downloaded the wirelessinfoscript to for the resulting file (probably your 'Desktop' folder according to the instructions above). 

The link to download the file is on the link. Run the script with only the wireless USB dongle you are trying to fix plugged in and ethernet cable (which, from memory, you don't have).

---

### Post by peter206 on 2015-09-03
I followed the instructions to the letter. The only thing this script does is 

> ###### wireless info START #####. That's it. Nothing else. It doesn't ask for password or anything else. :-(

> **jeremy31 said:**
> Check the wifi security setting on the ZTE device, you want WPA2-PSK only with no TKIP.  Reboot the ZTE after saving the setting and then Ubuntu should connect

Thanks for suggestion but I already have that. I even tried without any security but it didn't work. :-( 

The damn thing works in windows and its present in Ubuntu. It has to be something simple. Do you use that same device?

Since i can't run the damn wireless script I run some commands manually. Let me know if you need anything else.

```

peter@3DC:~$ sudo lshw -C network
  *-network              
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: 74:d4:35:9d:b0:87
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:38 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e8:de:27:67:9d:30
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:fe900000-fe97ffff memory:fe980000-fe98ffff

peter@3DC:~$ dmesg | grep ath
[    1.137838] Loaded X.509 cert 'Magrathea: Glacier signing key: ###########################'
[    5.866544] device-mapper: multipath: version 1.7.0 loaded
[    6.494957] ath: EEPROM regdomain: 0x21
[    6.494960] ath: EEPROM indicates we should expect a direct regpair map
[    6.494962] ath: Country alpha2 being used: AU
[    6.494963] ath: Regpair used: 0x21


peter@3DC:~$ rfkill list
0: phy0: Wireless LAN
      Soft blocked: no
      Hard blocked: no

peter@3DC:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
      Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
      Kernel driver in use: r8169
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
      Subsystem: Qualcomm Atheros Device [168c:3118]
      Kernel driver in use: ath9k

peter@3DC:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1
uas                    24576  0
usb_storage            69632  2 uas
bnep                   20480  2
rfcomm                 69632  0
bluetooth             491520  10 bnep,rfcomm
snd_hda_codec_realtek    81920  1
snd_hda_codec_generic    69632  1 snd_hda_codec_realtek
snd_hda_codec_hdmi     53248  1
arc4                   16384  2
ath9k                 147456  0
snd_hda_intel          32768  5
kvm_amd                61440  0
snd_hda_controller     32768  1 snd_hda_intel
kvm                   479232  1 kvm_amd
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
snd_hda_codec         143360  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
amdkfd                 81920  1
snd_hwdep              20480  1 snd_hda_codec
amd_iommu_v2           20480  1 amdkfd
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
radeon               1552384  4
crct10dif_pclmul       16384  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
crc32_pclmul           16384  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
mac80211              708608  1 ath9k
ghash_clmulni_intel    16384  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
cfg80211              524288  4 ath,ath9k_common,ath9k,mac80211
aesni_intel           172032  0
snd_timer              32768  2 snd_pcm,snd_seq
aes_x86_64             20480  1 aesni_intel
snd                    86016  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
ttm                    94208  1 radeon
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
drm_kms_helper        126976  1 radeon
dm_multipath           24576  0
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
drm                   344064  7 ttm,drm_kms_helper,radeon
scsi_dh                16384  1 dm_multipath
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
8250_fintek            16384  0
i2c_piix4              24576  0
serio_raw              16384  0
k10temp                16384  0
i2c_algo_bit           16384  1 radeon
edac_core              53248  0
fam15h_power           16384  0
edac_mce_amd           24576  0
video                  20480  0
shpchp                 40960  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
pata_acpi              16384  0
hid_generic            16384  0
usbhid                 53248  0
hid                   110592  2 hid_generic,usbhid
psmouse               114688  0
pata_atiixp            16384  0
ahci                   36864  5
libahci                32768  1 ahci
r8169                  81920  0
dm_mirror              24576  0
mii                    16384  1 r8169
dm_region_hash         24576  1 dm_mirror
dm_log                 20480  2 dm_region_hash,dm_mirror

peter@3DC:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        ################

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
    PeroWiFi:        Infra, ##############, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    Kastelic:        Infra, ##############, Freq 2412 MHz, Rate 54 Mb/s, Strength 29


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        #############

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


peter@3DC:~$ iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
lo        no wireless extensions.


```

---

### Post by jeremy31 on 2015-09-03
> **peter206 said:**
> Thanks for suggestion but I already have that. I even tried without any security but it didn't work. :-( 

The damn thing works in windows and its present in Ubuntu. It has to be something simple. Do you use that same device?

I have a ZTE Unite hotspot and the same wifi card in one of my laptops.  Does your hotspot have the ability to check for updates?

---

### Post by Bucky Ball on 2015-09-03
> **peter206 said:**
> I followed the instructions to the letter. The only thing this script does is 

. That's it. Nothing else. It doesn't ask for password or anything else. :-(

Then you probably have created the file. 

* Did you look in the same folder as you have the wireless script in for the output .txt or .tar.gz file??? *

My guess is that it may have little to do with your wireless card and everything to do with the config on your modem. When you click the network icon on Ubuntu do you see any networks at all, just not yours?

Jeremy has the same hardware as you by the looks so he may be able to add some fresh ideas.

---

### Post by peter206 on 2015-09-03
> **jeremy31 said:**
> I have a ZTE Unite hotspot and the same wifi card in one of my laptops.  Does your hotspot have the ability to check for updates?

Like hotspot firmware update? No. I am guessing ZTE should not be the main problem since Ubuntu can't connect to other unsecured WiFi network as well but it can perfectly fine in windows. On top of this I can't run the wireless script in my PC ether. I don't know what to do anymore. I like Ubuntu, I even tested on it Blender3D. Its great and blazing fast compared to windows but without internet connection its pretty much useless. My greatest fear is that I will have to install the spywindows 10 again. :-(

---

### Post by Bucky Ball on 2015-09-03
So you can see other networks, just not yours? If so, I suggest you boot to Windows and check out the settings for wireless there. Write them down exactly. Boot back into Ubuntu, click Network Manager and edit the wireless connection and check they are exactly the same, re. security type and password, IPv4 settings, etc.

It is odd, though, as it should see your network. If it can see others and not yours that suggests something at the modem end. But if you say it works fine with Windows ... :-k

---

### Post by peter206 on 2015-09-03
> **Bucky Ball said:**
> Then you probably have created the file. 

* Did you look in the same folder as you have the wireless script in for the output .txt or .tar.gz file??? *

My guess is that it may have little to do with your wireless card and everything to do with the config on your modem. When you click the network icon on Ubuntu do you see any networks at all, just not yours?

Jeremy has the same hardware as you by the looks so he may be able to add some fresh ideas.

In Ubuntu I can see the only two wifi networks from which one is mine. Once I try to connect to my secured wifi or the other one unsecured, it will stop in the middle of the connection process and get back asking again for password which is already filled in authentication dialog box. It looks like as if the program doesn't have necessary data to connect. 

I literally took the script (copy/paste) and put it on my desktop so the script should output on my desktop. Right? Nothing. To be extra sure I put in my home directory. Nothing. For some reason the script doesn't execute properly. Maybe it's alive and it doesn't like me. :-)

---

### Post by Bucky Ball on 2015-09-03
> **peter206 said:**
> Maybe it's alive and it doesn't like me. :-)

Ha. Maybe. :)

Well, at least we know the card is actually working, to a degree, and seeing networks. 

Perhaps try this:

> I went to Preferences --> Desktop Session Settings, and on the Automatically Started Applications tab, I selected GPG Password Agent, and all is well. Passwords are now stored normally.

From [here]("http://ubuntuforums.org/showthread.php?t=780544&page=2"). It seems to be forgetting the password as soon as you hit return, so maybe worth a try.

You have set up the wireless configuration as I mentioned before, the general tab has 'Automatically connect to this network' and 'All users may connect to this network' ticked? 

Also, try deleting the wireless entry in Network Manager, reboot. When it tells you network connections are available, choose yours and add password. That should select the correct security and set up a new wireless entry for your wireless. Any different?

Our tweaking may have done something we've missed to the current wireless profile. Or it may just work. :-k :)

---

### Post by peter206 on 2015-09-03
> You have set up the wireless configuration as I mentioned before, the general tab has 'Automatically connect to this network' and 'All users may connect to this network' ticked? 

Its ticked by defoult. 

> Also, try deleting the wireless entry in Network Manager, reboot. When it tells you network connections are available, choose yours and add password. That should select the correct security and set up a new wireless entry for your wireless. Any different?

Unfortunately no. :-(

From [here]("http://ubuntuforums.org/showthread.php?t=780544&page=2"). It seems to be forgetting the password as soon as you hit return, so maybe worth a try.

> Never the less, I thought the solution might be useful for some people. I went to Preferences --> Desktop Session Settings, and on the Automatically Started Applications tab, I selected GPG Password Agent, and all is well. Passwords are now stored normally.

Excuse my noob question. **Where** do I access **Preferences --> Desktop Session Settings? **All I have is system settings.:o

---

### Post by Bucky Ball on 2015-09-03
Ok, older version. My mistake. Sorry. 

Try in Session and Startup> Application Autostart. You should have that in Unity.

---

### Post by peter206 on 2015-09-04
> **Bucky Ball said:**
> Ok, older version. My mistake. Sorry. 

Try in Session and Startup> Application Autostart. You should have that in Unity.

Also ticked by default. 


So I guess this is it. Back to dark side and spywindows. Yesterday i tried with Fedora and the problem still persists. Since so many people have the same or similar problem I suspect linux is not capable properly handling wifi. I will try to install OpenSuse just to be sure I did everything humanly possible to switch to linux. 


Very disappointing. :-(

---

### Post by Bucky Ball on 2015-09-04
Ubuntu is more than capable of using wifi. Millions use it without issue. It is the manufacturers that are the problem as if they create hardware with no facility for it to run on Linux, our hands are tied. 

For all we know, we could be missing something simple. I am no expert, and none of the wireless gurus have posted on this thread to help.

Generally, when buying hardware, I make certain the hardware is going to work. Having said that, your wireless card is working (as you can see networks). Your problem is you can't connect to any and that shows a different issue (NOT incompatable hardware, which, while I understand your frustration, makes you remarks about Linux and wireless redundant). 

Anyhow, good luck, and hoping one of the wireless experts spots this and can help. :)

---

