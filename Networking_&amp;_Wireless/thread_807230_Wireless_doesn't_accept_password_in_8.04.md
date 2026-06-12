---
title: "Wireless doesn't accept password in 8.04"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Peter K Nicol on 2008-05-25
I have followed many threads but I am no further forward. I have a working USB device (Netgear WG111v2) and I can see my network. I have a WEP passphrase. The signal is weaker than on Windows (50% as opposed to 88%) and as soon as I try to start Google, for instance, the signal drops to 0.  The passphrase is asked for again. The annoying part of this is that in 7.04 it worked perfectly but for an occasional dropped signal. In 7.10 it worked ok with lots of dropped signals. In 8.04 the signal is dropped immediately. I am sending this over my wired connection on the same network with no problem at all. Any ideas would be very much appreciated.

---

### Post by danpos on 2008-05-25
@Peter K Nicol

There's something about your issue at this **[launchpad thread]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/184788")**. Specifically **[this message]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/184788/comments/10")**.

Danpos.

---

### Post by lankforddl on 2008-05-25
Peter,

I use the same usb netgear wg111v2 with my dell laptop and it works great! 

First: the signal strength isn't very accurate. I tested connectivity with windows and ubuntu with the same netgear usb device and they reported almost similar conn/bandwidth/ etc.. The connection percentage in ubuntu is not accurate. 

Second: AppArmor would block my access when i first started using this wireless device and once I supplied the password for the default keyring request it worked fine. These details may not help you but it could get you moving in the right direction.

Do you establish a connection something like this: Take a look at the Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm 

danny@ubuntu1420:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"LANKFORD"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:0F:B5:1F:68:7E   
          Bit Rate=36 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've found that linux doesn't show the same si

---

