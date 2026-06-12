---
title: "more detail regarding iwl3945, dell d630"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by abelew on 2008-05-28
I am among the users having difficulty with the iwl3945 on a Dell running x86_64.  It works intermittently.

some examples of failures include the following messages from the kernel:
May 28 11:24:36 iconoclast kernel: [    2.925940] wlan0: No STA entry for own AP 00:0f:66:b8:47:1c
May 28 11:24:36 iconoclast kernel: [    2.925964] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
May 28 11:24:36 iconoclast kernel: [    2.948516] wlan0: Initial auth_alg=0
May 28 11:24:36 iconoclast kernel: [    2.948526] wlan0: authenticate with AP 00:15:c7:29:bf:7f
May 28 11:24:36 iconoclast kernel: [    2.949696] wlan0: Initial auth_alg=0
May 28 11:24:36 iconoclast kernel: [    2.949701] wlan0: authenticate with AP 00:15:c7:29:bf:7f
May 28 11:24:36 iconoclast kernel: [    3.011996] wlan0: authenticate with AP 00:15:c7:29:bf:7f
May 28 11:24:36 iconoclast kernel: [    3.014598] wlan0: authenticate with AP 00:15:c7:29:bf:7f
May 28 11:24:37 iconoclast kernel: [    3.026293] wlan0: authentication with AP 00:15:c7:29:bf:7f timed out

  When this occurs, I can still scan the AP successfully.  This is after removing any WEP/WPA passphrase from the router and attempting to use both the default iwl3945 and that provided by the linux-backports-modules package.

  When eventually it does work, I receive the following:
[  536.355045] wlan0: associated
[  536.356757] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  536.362127] wlan0: Initial auth_alg=0
[  536.362132] wlan0: authenticate with AP 00:0f:66:b8:47:1c
[  536.363737] wlan0: RX authentication from 00:0f:66:b8:47:1c (alg=0 transaction=2 status=0)

  but cannot transfer data at > 20k / second.  Using another laptop I have no problems receiving a full speed connection.

 Suggestions?

---

### Post by chili555 on 2008-05-28
May I please see your *iwconfig wlan0*? Thanks.

---

### Post by abelew on 2008-05-29
Currently the wireless connection using iwl3945 is working, though at a maximum speed of ~20k/second.

```

wlan0     IEEE 802.11g  ESSID:"ngo"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:0F:66:B8:47:1C   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=84/100  Signal level=-49 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon: 0

```


otherwise the iwconfig would look the same with the exception of the link quality which would show up as 0/100 even if a iwlist scan shows the network as visible.

  If it is relevant, I disabled hal/dbus/network manager/etc quite some time ago and instead have a script which performs the network initialization on login/resume.  For this particular network these commands end up including:

dhclient -r wlan0 (conditionally)
iwconfig wlan0 enc off
iwconfig wlan0 essid ngo
ifconfig wlan0 10.0.0.10 netmask 255.255.255.0
route add default gw 10.0.0.100

---

### Post by chili555 on 2008-05-29
Would you please add this to your script:```
iwconfig wlan0 rate auto
```If this works well for you, we can talk about easier ways to do all this.

---

### Post by abelew on 2008-05-29
Greetings,
  I have previously done that as well as hard coded the rate to 11M, neither has an effect.  But for the sake of this discussion, I have done so again.

  As for easier methods of initializing the wireless network, I am rather happy with my perl script, it has a nice AppConfig config set up for the many different types of wireless and wired networks I use and takes 0.01<x<1.0 seconds to run as opposed to the significant amount of time for every other network configuration utility I have thus far run across.

Before I forget, the AP is set to full speed.

---

### Post by chili555 on 2008-05-29
This may be a bit of a stretch, but let's try:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```See if this has any effect on your ability to associate with the AP or any effect on speed.

---

### Post by abelew on 2008-05-29
Greetings again.  I had already tried that.  However in the spirit of fun I just tried it again and sadly was unable to associate to the network until I rebooted the box.

On a whim I just tried reloading with hwcrypto=1 and am now pushing what appears to be an increased maximum of 30kb/second, still no where near what I once had, but interesting.

---

