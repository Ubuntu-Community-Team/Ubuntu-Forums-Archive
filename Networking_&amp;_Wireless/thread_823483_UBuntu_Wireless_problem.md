---
title: "UBuntu Wireless problem"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by blackvaio on 2008-06-09
Hi,

I've just installed latest Ubuntu 8.x on my sony vaio tz31wn/b, but i am not able to connect to internet. I've put the WEP key for my broadband internet in the Network settings, but it doesn't seem to work. I am new to Ubuntu and don't know much.

Can anyone please help, what am i doing wrong?

Thanks for help

PS: I've already enabled the wireless on my desktop and it works fine with windows vista. The wireless card is Intel.

---

### Post by rlzyoner on 2008-06-09
Run the following command and please post the output.

*iwconfig*

Then ensure that your wireless adaptor is enabled by running 

*sudo ifconfig wlan0 up *

*Replace wlan0 with the name of your wireless adaptor*

Let me know how that goes

---

### Post by blackvaio on 2008-06-09
Hi,
Thanks for the reply.

Here is the output of iwconfig command:

lo              no wireless extensions.
eth0            no wireless extensions.
wmaster0        no wireless extensions.
wlan0           IEEE 802.11g ESSID: "O2" Nickname:""
                Mode:Managed Frequency:2.412 GHz  Access Point: Not-Associated
                Tx-Power=27 dBm
                Retry min limit:7   RTS thr:off    Fragment thr=2346 B
                Power Management:off
                Link Quality:0  Signal level:0   Noise level:0
                Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
                Tx excessive retries:0  Invalid misc:0  Missed beacon:0


whereas executing command sudo ifconfig wlan0 up

doesn't return anything. How can i get the name of my adaptor to replace wlan0 ?

Thanks again for your help.

---

### Post by rlzyoner on 2008-06-09
wlan0 seems to be the name of your wireless adaptor.

Maybe check out the following link.
It's for setting up your connection manually.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

