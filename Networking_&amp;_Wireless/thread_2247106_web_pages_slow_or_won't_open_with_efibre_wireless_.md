---
title: "web pages slow or won't open with efibre wireless network"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by Mickser_52 on 2014-10-05
Hi I'm visiting my daughter who recently had a fibre network/ router installed. It's working fine for window users including myself with my dual booting laptop. The problem is that when I try to use ubuntu it is very slow or won't open pages. Some times it is quicker than others. On one occasion I managed to open a speed test page which told me the laptop speed was 18 mb/s. This is a lot faster than my own wlan connection at home but for some reason everything is so much slower than at home. I set network manager to ignore Ipv6 as this helped before but it made no difference. Any help would be appreciated as I have been hoping to change to the same fibre network provider in the near future

---

### Post by Mickser_52 on 2014-10-05
Sorry should have mentioned I am running Ubuntu 14.04 and have an Intel(R) Centrino(R) -n 2230 wireless card

---

### Post by Mickser_52 on 2014-10-05
here is the result of the Wireless info script[ATTACH=CONFIG]256971[/ATTACH]

---

### Post by jeremy31 on 2014-10-05
If you have control of access point named eircom01490194 change the security to WPA2-AES only, in network manager settings for that access point change IPv6 settings to disabled and lets see if this helps```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
``` reboot and see if it works better

---

### Post by Mickser_52 on 2014-10-05
Hi thanks for your reply. Unfortunately I am only visiting this house and do not want to start changing their router settings. I had already set IPv6 to **ignore** to little effect. I will try the iwlwifi editing and see if that helps. At the moment everything is working perfectly, which happens from time to time. 

If I do eventually change to the fibre network I will change the WPA settings if necessary.

---

### Post by Mickser_52 on 2014-10-06
Hello again. problem has reappeared this morning. Wifi worked fine initially but then it slowed down for no obvious reason. Here is the present content of iwlwifi if that is of any help.

> # /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8

---

### Post by varunendra on 2014-10-06
A fresh report of the wireless_script would be more helpful.

By the way, two obvious reasons for possible slowing down are - 1) the WPA/WPA2 mixed mode, 2) the channel getting too crowded .... plus a few more things that you may not have control over, for example 'WMM' (under QoS) dictating the traffic in the router.

---

### Post by Mickser_52 on 2014-10-06
Thank you. Here is a recent wireless_info text.
[ATTACH]256979[/ATTACH]

In relation to traffic on channel, would that not also affect Windows performance as well? I know very little about wireless networking so a lot of these terms are meaningless to me.

---

### Post by varunendra on 2014-10-06
If the report is indeed a fresh one, you can see yourself (under "module parameters" section) that the value of "11n_disable" is '0' again, not '8' as was recommended. And I don't see the suggestion of jeremy31 applied in the 'iwlwifi.conf' file either. Please try what he originally suggested again. I can't say how it got reset, but a simple update or default actions of the OS definitely can't do it.

---

### Post by Mickser_52 on 2014-10-06
Apologies, I seem to have sent two reports in my last post. The first was my original report, the second of the two, at the bottom, is the "fresh report" as of this morning.

With regards to Jeremy31 suggestions: the line "options iwlwifi 11n_disable=8" has been added to iwlwifi.conf
                                                        :Ipv6 is set to Ignore in network manager for that connection.
                                                        : It was not possible to alter someone elses wpa settings.


This is a little academic at the moment as I have now returned home and back to my own wlan network which although much slower opens pages almost immediately. My concern is that if I do opt for the fibre package which is being offered to me (identical to the one I have been using over the last two days) that I will encounter similar problems on my own internet connection. Is it related to the fibre optic connection, the zyxel F1000 router which comes with it, Quality of service, traffic ?

In the meantime I have a perfectly functioning connection, if a little slow, and these are all problems for a later date.

Thanks again for your and Jeremy's time.

---

### Post by varunendra on 2014-10-06
I think the part of the router that interfaces with the local network is almost completely isolated with the part that interfaces with the ISP side or the internet.

The OS (Ubuntu) only deals with this part that interfaces with your local network, and I think that remains the same regardless of you are using a copper connection or an fibre optic one. So if Ubuntu is happy with the settings of this LAN side part of the router, it should remain good, or will only become better with more bandwidth available from the other part.

If you face any problems at all, they can be dealt the same way as with the copper cable connection.

That being said, I must warn you that these are just my personal assumptions based on *some* (not super mature) fundamental knowledge and experience. I personally believe you should be good with the upgrade, but can't guarantee that. :)

---

### Post by Mickser_52 on 2014-12-09
To update this thread: I have recently upgraded to the fibre network which I mentioned in earlier posts and found exactly the same problems as before. I took all the advice given earlier in relation to wpa2-aes only etc. and it made no difference. The internet connection was continuously intermittent at best. On further research I found others were having similar if not identical problems with 14.04 wireless connections. Further suggestions there were followed and to make a long story short, two changes have been made which (fingers crossed) are working at present. 1. set iw reg to (in my case) IE and 2. in iwlwifi.conf set disable=1.

I will not set this post to solved yet until it is working consistently

---

