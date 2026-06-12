---
title: "Help needed with Edgy, AR5212 802.11abg NIC (rev 01) wifi setup."
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by Saul Zaddik on 2007-01-09
Hello,

After reading this forum's threads and trying the steps outlined without success, I seem to be so close to the answer. Close, does not make it work though. I need step-by-step help. May I tell you what my Toshiba laptop has:

~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11Ta  ESSID:""  
          Mode:Managed  Frequency:5.8 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.
 
~$ lspci
02:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

02:09.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (LOM) (rev 03)

~$ dmesg | less
[17179584.556000] ath_hal: module license 'Proprietary' taints kernel.
[17179584.556000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

The above is from a fresh install of Ubuntu 6.10. I have learned how to install Ubuntu with success. I have re-installed Ubuntu 12 times on this machine due to trying things found here and in the newsgroups. 

The access point does not associate. I can get static wireless access to my wireless system at home. My work requires the ability to browse and access multiple wireless system using WPA. I can not take the time at work to tweak each wireless system's settings for access. The wireless subsystem on my machine must start with Ubuntu's start. Yes, I am a new user of Linux, after many, years of Windows. 

One other question. How do I turn off the smilies?

Saul

---

### Post by Saul Zaddik on 2007-01-10
Is everyone else stumped?

---

### Post by tturrisi on 2007-01-10
enable the multi-universe repos in Synaptic, then install the linux-restricted-modules for your kernel.  reboot.

---

### Post by Saul Zaddik on 2007-02-10
Thank you!

---

### Post by pointym5 on 2007-02-23
> **tturrisi said:**
> enable the multi-universe repos in Synaptic, then install the linux-restricted-modules for your kernel.  reboot.

Not really an option for those with nothing but wireless ...

---

