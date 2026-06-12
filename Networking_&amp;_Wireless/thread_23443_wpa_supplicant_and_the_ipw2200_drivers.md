---
title: "wpa_supplicant and the ipw2200 drivers"
date: 2005-04-02
forum: Networking &amp; Wireless
---

### Post by MacGyver on 2005-04-02
I'm having problems getting wpa_supplicant to work in my Ubuntu.  I have a dell inspiron 8600 laptop with an Intel 2915ABG wireless card.  The wireless AP is a linksys WRT54g.  Everything works well in Windows XP.

The ipw2200 drivers seem to work OK (see below), which is more than I could get in Fedora!  The networking config thing can see my AP so I'm assuming the drivers are ok.

```
root@macgyver:/home/sam/wpa_supplicant-0.3.8 # dmesg|grep ipw
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

```

However wpa_supplicant will not work.  I have setup the wpa_supplicant.conf as per the page on the wiki (which is not helpful at all).

This is my wpa_supplicant.conf
```
network={
       ssid="zzzzz24zzzzz"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="(my key)"
}

```

This is what happens when I run it
```
root@macgyver:/home/sam # wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'default'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Line: 1 - start of a new network block
ssid - hexdump_ascii(len=12):
     7a 7a 7a 7a 7a 32 34 7a 7a 7a 7a 7a               zzzzz24zzzzz
proto: 0x1
scan_ssid=1 (0x1)
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=18): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='zzzzz24zzzzz'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
Own MAC address: 00:0e:35:84:f4:b5
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=12):
     7a 7a 7a 7a 7a 32 34 7a 7a 7a 7a 7a               zzzzz24zzzzz
ioctl[SIOCSIWSCAN{,EXT}]: Operation not supported
Failed to initiate AP scan.
Setting scan request: 10 sec 0 usec
EAPOL: Port Timers tick - authWhile=0 heldWhile=0 startWhen=0 idleWhile=0
Signal 2 received - terminating
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_set_wpa: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported

```

It looks like it can see my AP fine but can't connect.  From googling I think that the problem is wpa support isn't compiled into the drivers. 

So, my question is how do I get the drivers to support wpa_supplicant, or am I doing something totally wrong  :-? 

Thank you for any help!

---

### Post by luca_linux on 2005-04-12
Try this (worked for me): sudo wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D ipw -d
Anyway you need ipw2200 driver at least version 1.0.2.

---

### Post by MacGyver on 2005-04-13
Thanks but that didn't work, same error :(  I have the latest ipw drivers also

---

### Post by luca_linux on 2005-04-13
Look here: [http://www.ubuntuforums.org/showthread.php?t=25942](http://www.ubuntuforums.org/showthread.php?t=25942)
Maybe you have to copy some modules from one directory to another.

---

### Post by MacGyver on 2005-04-22
[QUOTE=luca_linux]Look here: [http://www.ubuntuforums.org/showthread.php?t=25942](http://www.ubuntuforums.org/showthread.php?t=25942)
Maybe you have to copy some modules from one directory to another.[/QUOTE]

Thanks for your guide but no luck :( I'm seriously considering ditching this card and getting something else as NOTHING works.

I have tried
* many versions of the ipw driver and applicable firmware
* ndiswrapper, no luck here either, it just wont load the drivers (might try this again, not an ideal solution though)
*linuxant's driverloader, this just hard locks my system which is something nothing else has managed to do.

Please tell me I don't have to buy a different wireless card  :-|

---

### Post by dejitarob on 2005-04-22
No you don't need to buy a new wireless card. It works great as long as you properly  use the latest firmware and drivers. Here is a simple how-to [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by MacGyver on 2005-04-22
[QUOTE=dejitarob]No you don't need to buy a new wireless card. It works great as long as you properly  use the latest firmware and drivers. Here is a simple how-to [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]

Thanks but that's the guide I've already tried with no luck.  I'm pretty sure it's to do with me having the 2915 card not the 2200

---

### Post by MacGyver on 2005-04-23
An email from someone on the ipw2200 project pointed me [here](http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/4662).

That seems to be the error I'm getting but how the hell do I apply that patch file?  ](*,)

---

### Post by dejitarob on 2005-04-23
No, that email is regarding old drivers. I have the 2915ABG and it works great. What part from lica's guide are you getting stuck on? On your first post you are using the old .19 drivers not the latest ones.

---

### Post by MacGyver on 2005-04-24
[QUOTE=dejitarob]No, that email is regarding old drivers. I have the 2915ABG and it works great. What part from lica's guide are you getting stuck on? On your first post you are using the old .19 drivers not the latest ones.[/QUOTE]

OK, here's what happens.

 > Download firmware and install as per guide, goes fine.

 > Download latest driver (1.03) and run 'make' with no errors (I had to install package linux-headers-386) to be able to run 'make'.  Run sudo make install which goes fine too

 > Fix up the error with /kernel as per the guide, this goes fine

 > Apt-get install wpasupplicant goes fine

 > Set up the .conf, same as the guide but ssid and psk changed to mine

 > Reboot

 > Now I'm getting a different error  ](*,)  dmesg | grep ipw shows:
```
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

```

Also modprobe ipw2200 shows:
```
sam@macgyver:~$ sudo modprobe ipw2200
Password:
FATAL: Error inserting ipw2200 (/lib/modules/2.6.10-5-386/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

And of course wpa_supplicant won't work.

Help!  I don't really want to try driverloader as it killed my system last time and ndiswrapper won't work.  I'm going to try some of the older drivers and firmware in the hope they work.

edit > Is it possible my laptop's FN+F2 wireless settings are screwing something up? I have it set to 'on' (ignore keys) in the bios but have tried the other settings with no luck.

Oh well at least I have xmms working with mpc/m4a files :(

---

### Post by MacGyver on 2005-04-24
Trying the 0.19 version and the applicable firmware doesn't work either, modprobe ipw2200 doesn't give any errors but dmesg | grep ipw gives this!:

```
sam@macgyver:~/downloads/ipw2200-0.19$ dmesg | grep ipw
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection

```

Which looks like the same as above but worse

---

### Post by luca_linux on 2005-04-24
Try to delete all the modules of ipw2200 (so ipw2200.ko and ieee80211*.ko) in any directory.
Then install again the latest driver and copy the modules as suggested in my howto.
I think there's some old module somewhere on your system.

---

### Post by MacGyver on 2005-04-30
Bump... any ideas anyone?

---

### Post by makoto42 on 2005-06-28
That should exactly be the patch, the cause, is that for some reason the bundled ipw driver with the kernel would not work (my experience), so I went to 1.1.0 (ipw2100 for me), but the new build didn't help.  The two options are to apply the patch you were pointed to by the link [http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/4662](http://article.gmane.org/gmane.linux.drivers.ipw2100.devel/4662)

I did it by taking the ipw2100-source .dsc, orig.tar.gz, and diff.gz, doing dpkg -x on the .dsc file,
patch -p0 < <file given in link>,
then dpkg-buildpackage -rfakeroot -b
then I could dpkg -i ../ipw-source*deb
then cd /usr/src
tar zxvf ipw2100-source.tar.gz
module-assistant a-i ipw2100
boom, should have working drivers for wpa_supplicant 0.3.8
keep in mind you need the right kernel-headers

It seems that the defines from the .config in the kernel directory indicates the defines being set, but the build doesn't act that way.  An alternative to the patch above is to remove the check in the ipw2100 makefile for .config settings and force "external build" behavior, this also works.

---

### Post by nybble on 2005-06-28
[QUOTE=MacGyver]Thanks but that's the guide I've already tried with no luck.  I'm pretty sure it's to do with me having the 2915 card not the 2200[/QUOTE]

that should not be a problem, i have the 2915 card in my laptop, and i'm using the 2200...i used that guide, and it worked fine...

---

### Post by luca_linux on 2005-06-28
In fact ipw2200 driver supports both 2200 and 2915.

---

### Post by Sjoske on 2005-07-18
Old thread but maybe this will help

Encountered the same problem today. 
Did you download the latest 80211 subsystem ?. Without this the new ipw driver won't work.

Before you compile the new modules don't forget to unload the old ones with 
modprobe -r ipw2200 ieee80211.

Also, you need to edit the makefiles to point to the correct location.

Hope this helps.

---

### Post by piopawlu on 2005-12-28
I think I was suffering from the same problem you are. But I managed to make it work. What you need to do is:

1) add "CONFIG_DRIVER_WEXT=y" into the wpa_supplicant .config file
2) then "make" and "make install"
3) finally launch wpa_supplicant with following parameters:
"-D wext" e.g. "wpa_supplicant -i eth1 -c /etc/wpa_supplicant.conf -D wext -dd"
4) hope it works for you too

I don't know why it doesn't work with -D ipw, yet since it works I won't complain.

---

