---
title: "Intel Centrino Advanced-N 6235 / Dell XPS 15"
date: 2013-11-29
forum: Networking &amp; Wireless
---

### Post by Rachel_Bunker on 2013-11-29
Hi, I was recently given a Dell XPS 15 L521X as a holiday gift.  Now that I have Ubuntu up and running (a project unto itself), I need help with the wifi.  It is not good in either Windows 7 or in Ubuntu.  My wireless card is an Intel Centrino Advanced-N 6235.  The problem is that in order to get a connection, I have to be in the living room (the room where we keep the router).  It doesn't work in any other room in the house.  If I do manage to get connected in the other rooms, it just cuts out.  I read that this model laptop often has wifi issues, but I haven't read about any fixes.  Any advice would be greatly appreciated.

---

### Post by heir4c on 2013-11-29
What about other WiFi cards? 
Maybe it is not the WiFi card but the router who is not strong enough.

---

### Post by Rachel_Bunker on 2013-11-30
I don't think it is the router since 4 other laptops, 3 gaming consoles, 5 smartphones, a smart TV, and 2 tablets are connected to the router without any issues.

---

### Post by chili555 on 2013-11-30
I suggest you try the infamous trick for these devices. Please open a terminal and do:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

---

### Post by Rachel_Bunker on 2013-11-30
It worked!  Thank you so much!

---

### Post by chili555 on 2013-11-30
Awesome! Glad it's working. Please mark the thread solved so the searchers will find it. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by heir4c on 2013-11-30
> **chili555 said:**
> I suggest you try the infamous trick for these devices. Please open a terminal and do:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

It's very interesting to read it is solved.

But, what does this command? Can you explain it a little bit. I think that there are more people with low speed wifi-connection who can benefit of this.
Is it something to do with the channel 11 you disable? (what I can make out of it by seeing '11n' and 'disable')
ThanX in advance!

---

### Post by chili555 on 2013-11-30
> **heir4c said:**
> It's very interesting to read it is solved.

But, what does this command? Can you explain it a little bit. I think that there are more people with low speed wifi-connection who can benefit of this.
Is it something to do with the channel 11 you disable? (what I can make out of it by seeing '11n' and 'disable')
ThanX in advance!The driver iwlwifi has a problem with 802.11N as implemented by some router manufacturers. I suspect that there is a lot of finger-pointing going on ("No, my way is right and your way is wrong!"). The temporary solution is to use a driver parameter in iwlwifi to disable 802.11N capabilities. 

This is ONLY applicable to iwlwifi and another iwlxxx driver. If you are not using iwlwifi, this is not appropriate for you.

From *modinfo iwlwifi*: ```
filename:       /lib/modules/3.11.0-13-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
<snip>
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
```For what it's worth, my Intel 6200 works perfectly at N speeds with a Linksys EA6300 router.

Most people don't really care much about N speeds since they aren't streaming 4K video to watch on a laptop.

---

### Post by Rachel_Bunker on 2013-11-30
I have to reopen this thread because it turns out that the problem is not solved after all.  It worked once, but it didn't keep working, so now I'm back to the square one.

Perhaps it was never really solved to begin with.  It occurred to me that perhaps it makes a difference that the laptop connected to the router just fine in the living room and then I carried it (open) to my bedroom so it never disconnected.

---

### Post by chili555 on 2013-12-01
Here are a few things you might try. First, let's set the regulatory domain explicitly. Sometimes, the driver assigns a one size (maybe) fits all CRDA. Let's set it for certain. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1](http://en.wikipedia.org/wiki/ISO_3166-1)  Then set it:```
sudo iw reg set XX
```Where XX is your actual country code. For example, I would set:```
sudo iw reg set US
```Does that help you connect? If so, we'll make it persistent.

Second, the driver suite often connects and then drops if it doesn't hear a probe response from the router quickly. Let's extend the time:```
sudo -i
echo "options mac80211 probe_wait_ms=3000"  >>  /etc/modprobe.d/mac80211.conf
exit
```Reboot. Any improvement?

Next, is the behavior the same with the router set to other, less populous channels, like channels 1 or 11? My super-duper go-fast router has an Auto channel mode where it selects the best channel on the fly. If yours does the same, I suggest you try with and without Auto channel.

Finally, if these steps don't help, please let us review your log after you tried and failed to connect:```
cat /var/log/syslog | grep -e wlan -e iwl -e etwork | tail -n25
```

---

### Post by Rachel_Bunker on 2013-12-03
Sorry it took me so long to respond!  I have an uncle in the ICU and I rushed across the country to be with him and the only electronic device that I took with me was my iPhone.  Anyway, enough about my personal life and back to the computer.

This morning, I tried all the steps connected and still no luck so here is my log.

```
Dec  3 10:02:22 rachel-XPS-L521X NetworkManager[797]: <info> (wlan0): IP6 addrconf timed out or failed.
Dec  3 10:02:22 rachel-XPS-L521X NetworkManager[797]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Dec  3 10:02:22 rachel-XPS-L521X NetworkManager[797]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Dec  3 10:02:22 rachel-XPS-L521X NetworkManager[797]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Dec  3 10:02:26 rachel-XPS-L521X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15 (xid=0x1dccb74c)
Dec  3 10:02:41 rachel-XPS-L521X dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20 (xid=0x1dccb74c)
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <warn> (wlan0): DHCPv4 request timed out.
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 2095
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> Marking connection 'bunker' invalid.
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <warn> Activation (wlan0) failed for connection 'bunker'
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> (wlan0): deactivating device (reason 'none') [0]
Dec  3 10:02:47 rachel-XPS-L521X avahi-daemon[473]: Withdrawing address record for fe80::c685:8ff:fe45:bed3 on wlan0.
Dec  3 10:02:47 rachel-XPS-L521X avahi-daemon[473]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::c685:8ff:fe45:bed3.
Dec  3 10:02:47 rachel-XPS-L521X avahi-daemon[473]: Interface wlan0.IPv6 no longer relevant for mDNS.
Dec  3 10:02:47 rachel-XPS-L521X kernel: [  204.447602] wlan0: deauthenticating from 00:22:3f:6f:ff:62 by local choice (reason=3)
Dec  3 10:02:47 rachel-XPS-L521X NetworkManager[797]: <info> (wlan0): supplicant interface state: completed -> disconnected
Dec  3 10:02:47 rachel-XPS-L521X wpa_supplicant[1225]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Dec  3 10:02:49 rachel-XPS-L521X avahi-daemon[473]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::c685:8ff:fe45:bed3.
Dec  3 10:02:49 rachel-XPS-L521X avahi-daemon[473]: New relevant interface wlan0.IPv6 for mDNS.
Dec  3 10:02:49 rachel-XPS-L521X avahi-daemon[473]: Registering new address record for fe80::c685:8ff:fe45:bed3 on wlan0.*.

```

---

### Post by chili555 on 2014-01-30
I wish I had better news for you. Please check here: [https://communities.intel.com/message/192239#192239](https://communities.intel.com/message/192239#192239)

This is evidently a known issue, even in Windows. Please note that the thread is 68 (!!) pages long and on page 68, there is still no solution except replacing the card. If you have that option, I recommend it.

I'm sorry I can't be of further assistance.

---

### Post by denied on 2014-08-01
Well i did a fast fix (though u get max 54mbit) went into my router and set the mode to BG-mixed instead of doing NG-mixed. Its a shame since i have 100mbit but i rather have that for now until a proper sollution comes along.

---

### Post by ozangulle on 2014-08-13
> **chili555 said:**
> I suggest you try the infamous trick for these devices. Please open a terminal and do:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

I'm using a Sony VAIO with Intel Centrino Advanced-N 6235. I was having the same slow wifi problem and this code solved it. Thanks!

---

