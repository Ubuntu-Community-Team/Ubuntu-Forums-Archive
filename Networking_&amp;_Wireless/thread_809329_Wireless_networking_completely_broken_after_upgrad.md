---
title: "Wireless networking completely broken after upgrade from Gutsy to Hardy"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by lashi on 2008-05-27
G'day everyone. I'm running 2.6.24-17 on x86-64 Ubuntu. My wireless is: 

 [ 2763.133660] wlan0: ethernet device 00:1a:73:98:a1:04 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[ 2763.134038] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


This all worked rock solid with Gutsy. And it worked about twice with a lot of finniking around under Heron (I just kept reconnecting until it finally connected). But since yesterday, it seems to be completely down. Here's what the syslog tells me:

May 27 07:15:10 epsilon NetworkManager: <info>  Device wlan0 activation scheduled... 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) started... 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0/wireless): access point 'Shambhala' is encrypted, but NO valid key exists.  New key needed. 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Shambhala'. 
May 27 07:15:10 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Shambhala' received. 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 27 07:15:18 epsilon NetworkManager: <info>  Activation (wlan0/wireless): access point 'Shambhala' is encrypted, and a key exists.  No new key needed. 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was '0' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 5368616d6268616c61' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 27 07:15:19 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:15:19 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 27 07:15:22 epsilon NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May 27 07:15:23 epsilon kernel: [ 2982.247388] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 27 07:15:24 epsilon avahi-daemon[5088]: Registering new address record for fe80::21a:73ff:fe98:a104 on wlan0.*.
May 27 07:15:33 epsilon kernel: [ 2987.251883] wlan0: no IPv6 routers present
May 27 07:15:49 epsilon NetworkManager: <info>  Supplicant state changed: 0 
May 27 07:15:50 epsilon ntpd[11020]: sendto(91.189.94.4) (fd=20): Invalid argument
May 27 07:16:09 epsilon NetworkManager: <info>  Activation (wlan0/wireless): disconnected during association, asking for new key. 
May 27 07:16:09 epsilon NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'Shambhala'. 
May 27 07:16:15 epsilon NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'Shambhala' received. 
May 27 07:16:15 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May 27 07:16:15 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May 27 07:16:15 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May 27 07:16:15 epsilon NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May 27 07:16:15 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May 27 07:16:16 epsilon NetworkManager: <info>  Activation (wlan0/wireless): access point 'Shambhala' is encrypted, and a key exists.  No new key needed. 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was '0' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 5368616d6268616c61' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May 27 07:16:17 epsilon NetworkManager: <info>  SUP: response was 'OK' 
May 27 07:16:17 epsilon NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May 27 07:16:56 epsilon ntpd[11020]: sendto(91.189.94.4) (fd=20): Invalid argument
May 27 07:17:01 epsilon /USR/SBIN/CRON[11738]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 27 07:17:06 epsilon sensord: Chip: coretemp-isa-0000
May 27 07:17:06 epsilon sensord: Adapter: ISA adapter
May 27 07:17:06 epsilon sensord:   Core 0: 61.0 C
May 27 07:17:17 epsilon NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
May 27 07:17:17 epsilon NetworkManager: <info>  Activation (wlan0) failure scheduled... 
May 27 07:17:17 epsilon NetworkManager: <info>  Activation (wlan0) failed for access point (Shambhala) 
May 27 07:17:17 epsilon NetworkManager: <info>  Activation (wlan0) failed. 
May 27 07:17:17 epsilon NetworkManager: <info>  Deactivating device wlan0. 
May 27 07:17:18 epsilon avahi-daemon[5088]: Withdrawing address record for fe80::21a:73ff:fe98:a104 on wlan0.
May 27 07:17:18 epsilon NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 

Basically, I tried creating my own wpa_supplicant.conf and trying to get it to associate, and it just doesn't. The network is is allright, because (a) it connected fine before and (b) it connects fine using my girlfriend's MacOSX.

Also, if I disable encryption, it works fine.

Does anyone have a clue how to fix this? It's ridiculously frustrating.

---

### Post by lashi on 2008-05-27
I forgot to give out the wireless endpoint information:

          Cell 01 - Address: 00:18:D1:96:1E:0C
                    ESSID:"Shambhala"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

---

### Post by lashi on 2008-05-27
I installed 2.6.22-14 from Fiesty. When I boot this kernel, the wireless works immediately. So, it's actually got to do with 2.6.24-16 and 2.6.24-17. Is there any differences to ndiswrapper on these kernels? I can't continue to use 2.6.22-14 because Hardy has screwed the sound somehow. I can't figure out what the hell is going on, because sound used to work fine in 2.6.22-14. The driver loads, the mixer sees everything, but nothing comes out of the speakers. Really, really weird stuff...

Anyone have issues doing wireless on these newer kernels?

---

### Post by EnlistedSquire on 2008-06-30
Hi lashi,

I'm having a very similar problem after the recent kernel upgrades - See [here]("http://ubuntuforums.org/showthread.php?t=836703") - but haven't had any joy fixing it. I can connect using TKIP, just no AES.

---

### Post by xenotech on 2008-07-02
I just recently made the upgrade from Feisty to Hardy, I was using OpenSUSE 10.3 in between the two distributions, off and on.

I'd like to say I'm having a similar problem except that I never needed to use the ndiswrapper for my ma311 wireless card in Feisty; it detected everything from a fresh install and I was on my merry way.

Apparently in hardy, this is not the case, and I'm having a devil of a time understanding why the support regressed. 

In any case, I'm switching back to feisty until someone posts some more details on the subject, I couldn't seem to find anything pertinent on the forums, other than a bug report that orinoco_pci has regressed to not support netgear's ma311 and that several people are having trouble with hostap_pci as well. The suggestion is to use ndiswrapper but I'm basically lost installing anything in linux without immediate access to the internet, from the computer I'm attempting to solve a problem with.. If anyone has any suggestions for me, I'd really appreciate it.

Edit: some more details of my problem, I've used the help file and it says "if you don't see Wireless Networking in your network manager, go to System -> Preferences -> Hardware Information" .. I have checked both System and Administrator sections, and there is no "Hardware Information" in the dropdown menu whatsoever. I've seen one entry on the forums of someone with a similar dilemma but he didn't describe any details as to how or where he found his device manager in hardy.

My problem is.. after using lshw or whatever it's called.. it SEEMS to detect my network card/drivers. It simply won't show any wireless networking options in the network manager, or wireless networks available.

I've been using Linux for about a year now, but I wouldn't consider myself experienced by any stretch. I've kinda been stumbling with great success for a while. This is one of my first major hiccups. I'd like to stay up to date with the versions, that's always been, in my experience, "a good thing". Am I wrong?

---

### Post by lashi on 2008-11-01
This issue has been resolved in my particular instance in both 8.04 and 8.10. Upgrading to Kernel 2.6.24-21, I noticed that it offered a proprietary driver from Broadcom. I installed this driver (wl.ko), and for this to automatically load, I deleted /etc/modprobe.d/ndiswrapper.

After a reboot (or if you're used to Linux a bit more, you can just modprobe -r ndiswrapper, modprobe wl), it works perfectly okay, and this driver in particular works with WPA2.

As I suspected (and I'm sure many others), the crux of this has to do with the interoperability with ndiswrapper and the kernel. For those of us who have: 

01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

I'm giving you a thumbs up, an better alternative exists. 

Also, I've upgraded to 8.10, and the networking and WPA2 authentication works with kernel 2.6.27-7-generic.

---

### Post by lashi on 2008-11-01
With regards to my last thread, to clarify for the novice users, you *need* to do a reboot after the kernel upgrade. But if ndiswrapper is still loaded by default, then you should delete/etc/modprobe.d/ndiswrapper and you don't have to necessarily reboot again, just do the modprobes.

Best of luck!

---

