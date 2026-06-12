---
title: "feisty : bug in wireless-tools : cant set essid ??"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by gruadp on 2007-05-01
I did a clean install of ubuntu feisty 7.04 and tried for two days to make wlan working with ubuntu networkmanager explicit config or the new "roaming profile". 
I failed.

On the other hand it took me 2 minutes to manually establish the connection with iwlist and iwscan. Strange ...

So when I use the roaming-profile the connection-applet shows my network and I click it and need to enter my hex-pass-phrase for my 128-bit WEP and then the icon changes from "black screen with orange triangle" to "black screen without treeangle" or to "stair-like icon that seems to indicate the link-quality".  Whatever triggers each of these icons,  the connection does not work and iwconfig reveals that the essid is set but the encryption not.

I post the syslog-entries from the moment I enter the passphrase:

```

---------------------------------
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0) New wireless user key for network 'goldFisch1' received. 
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May  1 22:09:23 music NetworkManager: <information>^IActivation (wlan0/wireless): access point 'goldFisch1' is encrypted, and a key exists.  No new key needed. 
May  1 22:09:23 music NetworkManager: <information>^ISUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant^I' 
May  1 22:09:24 music kernel: [ 1664.312000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'AP_SCAN 1' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'ADD_NETWORK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was '0' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 ssid 676f6c64466973636831' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_key0 <key>' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'SET_NETWORK 0 wep_tx_keyidx 0' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: sending command 'ENABLE_NETWORK 0' 
May  1 22:09:24 music NetworkManager: <information>^ISUP: response was 'OK' 
May  1 22:09:26 music avahi-daemon[4672]: Registering new address record for fe80::20f:b5ff:fe4d:d08d on wlan0.*.
May  1 22:09:26 music NetworkManager: <WARNING>^I real_act_stage2_config (): Activation (wlan0/wireless): couldn't monitor the supplicant. 
May  1 22:09:26 music NetworkManager: <information>^IActivation (wlan0) failure scheduled... 
May  1 22:09:26 music NetworkManager: <information>^IActivation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May  1 22:09:26 music NetworkManager: <information>^IActivation (wlan0) failed for access point (goldFisch1) 
May  1 22:09:26 music NetworkManager: <information>^IActivation (wlan0) failed. 
May  1 22:09:26 music NetworkManager: <information>^IDeactivating device wlan0. 
May  1 22:09:26 music kernel: [ 1666.340000] ndiswrapper (set_essid:60): setting essid failed (C0000001)
May  1 22:09:26 music avahi-daemon[4672]: Withdrawing address record for fe80::20f:b5ff:fe4d:d08d on wlan0.
May  1 22:09:26 music dhclient: receive_packet failed on wlan0: Network is down
May  1 22:09:26 music NetworkManager: <WARNING>^I nm_device_802_11_wireless_set_essid (): error setting ESSID to '' for device wlan0: Invalid argument 
-----------------------------------

```


Whats going on here?

with 

```

iwlist wlan0 scan
iwconfig wlan0 key restricted 0123456789ABCDEF0123456789
iwconfig wlan0 essid goldFisch1
iwconfig wlan0 key restricted 0123456789ABCDEF0123456789
dhclient3 wlan0

```

things work like a charme. (I do the key-command twice, cause I never know if its supposed to be before or after the essid-part)

If its interesting: my wlan-card is WG511v2 and I use ndiswrapper.  Using ndiswrapper with the new ubuntu still is a pain. First ndiswrapper does not come with the CD (even if it says otherwise in the help). One needs to download it on a different machine and then manually copy and install it to the machine to get it working (and to get first internet-contact).

Then the "windows wireless driver" - application in system -> administration was not able to handle the driver. It always said : "hardware not present" even ndiswrapper -l told otherwise and it obviously works (I write this posting over the wireless connection I'm talking about)

To be honest : I expected more from new ubuntus wireless-support. Especiall because "roaming" and "wireless" was one of the big words in the roadmap to feisty. I'm quite used to linux/laptops/wireless and still it took me some tinkering and manual configuration until I managed to get internetaccess. A non-expert user wil defintely fail here. And when I look at the other postings here : many people have similar problems.

And last : I didnt find a way in PLACES->"connect to server" to mount any nfs-share. This also needs to be done manually in fstab. 

Plus the fact that I still cant get my screen-resolution higher than 800x600 (offtopic I know) doesnt make me too happy with feisty.  ubuntu 6.10 worked better with graphics and wireless to me. (but it had several bigtime bugs in the server-packages, especially the cruel one in the imap-package that imho still is open, but I didnt check lately)

So  - sorry for the complaints. Maybe someone will nevertheless try to help me :)

thnx
peter

---

### Post by Sensei_V on 2007-05-01
Looks like your post got cut off... and just before you got to the good stuff, too... oh, looks like you got it up now

I had similar problems, except the icon tended to stay as two blue globes with a swirly thing around them for a while while it was trying to connect.  This is where mine usually got stuck before trying to connect to a local open network.  Try clicking on signal strength (stair-like) icon and see if it tells you what network you are connected to.  I also had the same weirdness with ndiswrapper and ndisgtk, but my wireless works just fine now that I have security set up.

One thing I found helpful for troubleshooting was to disable wireless security on my router.  When I could connect that way, I knew the problem was with security, not with drivers or association issues.

What finally worked for me was, almost by accident, after I entered my WPA password as prompted by the NetworkManager applet in roaming mode, I was asked to enter a password for a newly created "default" keyring.  While trying to recreate this scenario, I found that if a user account already has a keyring named "default" then NetworkManager is more likely (although not guaranteed) to ask for access to this keyring and store your password there.  Now every time I login, I am asked for my  keyring password and the wireless connection just works.

I mentioned that I was more likely to get NetworkManager to access the keyring because I usually had to make several attempts at connecting before it worked, usually either disabling wireless by right-clicking the NM-applet or logging out and back in again.

As for the screen resolution, my screen was all chopped up and I only had 800x600 until I applied the first code snippet from [this thread posting.]("http://ubuntuforums.org/showthread.php?t=167670#5")  After that, I had full 1600x1200.

---

