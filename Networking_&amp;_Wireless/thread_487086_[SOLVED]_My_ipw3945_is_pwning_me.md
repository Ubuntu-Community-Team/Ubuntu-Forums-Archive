---
title: "[SOLVED] My ipw3945 is pwning me"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Dr. Octagon on 2007-06-28
I recently did a fresh install of Kubuntu Edgy 6.10 and have never been able to see my wireless card.  My notebook is a Dell Latitude d620 and the wireless card in question is an Intel PRO/Wireless 3945ABG.  I have tried various fixes and scoured numerous threads to no avail.  Help me please!

---

### Post by harty83 on 2007-06-28
I have the same card and am pretty sure I was using Edgy on my laptop before I upgraded to Feisty.  It works fine in feisty without doing anything.  But I can't remember if I had to do something in Edgy to get it work before.  

Try this:

Is the module loaded?

```
lsmod | grep "ipw3945"

```

You should see

```
ipw3945               118816  1 
ieee80211              34760  1 ipw3945

```

If not, modprobe it

```
sudo modprobe ipw3945
```

---

### Post by Dr. Octagon on 2007-06-28
This is what I get when I try and load the module.

```
 doctor@kubuntu:~$ sudo modprobe ipw3945

Password:

FATAL: Error inserting ipw3945 (/lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

sh: /sbin/ipw3945d: not found

FATAL: Error running install command for ipw3945


```

And this is my dmesg output.

```
dmesg | grep ipw

[17179580.740000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext

[17179580.740000] ipw3945: Unknown symbol ieee80211_wx_set_encode

[17179580.740000] ipw3945: Unknown symbol ieee80211_wx_get_encode

[17179580.740000] ipw3945: Unknown symbol ieee80211_txb_free

[17179580.740000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext

[17179580.740000] ipw3945: Unknown symbol ieee80211_wx_get_scan

[17179580.740000] ipw3945: Unknown symbol escape_essid

[17179580.740000] ipw3945: Unknown symbol ieee80211_freq_to_channel

[17179580.740000] ipw3945: Unknown symbol ieee80211_set_geo

[17179580.740000] ipw3945: Unknown symbol ieee80211_rx

[17179580.740000] ipw3945: Unknown symbol ieee80211_get_channel

[17179580.740000] ipw3945: Unknown symbol ieee80211_channel_to_index

[17179580.740000] ipw3945: Unknown symbol ieee80211_rx_mgt

[17179580.740000] ipw3945: Unknown symbol ieee80211_get_geo

[17179580.740000] ipw3945: Unknown symbol free_ieee80211

[17179580.740000] ipw3945: Unknown symbol ieee80211_tx_frame

[17179580.740000] ipw3945: Unknown symbol ieee80211_is_valid_channel

[17179580.740000] ipw3945: Unknown symbol ieee80211_get_channel_flags

[17179580.740000] ipw3945: Unknown symbol alloc_ieee80211

[17179906.008000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext

[17179906.008000] ipw3945: Unknown symbol ieee80211_wx_set_encode

[17179906.008000] ipw3945: Unknown symbol ieee80211_wx_get_encode

[17179906.008000] ipw3945: Unknown symbol ieee80211_txb_free

[17179906.008000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext

[17179906.008000] ipw3945: Unknown symbol ieee80211_wx_get_scan

[17179906.008000] ipw3945: Unknown symbol escape_essid

[17179906.008000] ipw3945: Unknown symbol ieee80211_freq_to_channel

[17179906.008000] ipw3945: Unknown symbol ieee80211_set_geo

[17179906.012000] ipw3945: Unknown symbol ieee80211_rx

[17179906.012000] ipw3945: Unknown symbol ieee80211_get_channel

[17179906.012000] ipw3945: Unknown symbol ieee80211_channel_to_index

[17179906.012000] ipw3945: Unknown symbol ieee80211_rx_mgt

[17179906.012000] ipw3945: Unknown symbol ieee80211_get_geo

[17179906.012000] ipw3945: Unknown symbol free_ieee80211

[17179906.012000] ipw3945: Unknown symbol ieee80211_tx_frame

[17179906.012000] ipw3945: Unknown symbol ieee80211_is_valid_channel

[17179906.012000] ipw3945: Unknown symbol ieee80211_get_channel_flags

[17179906.012000] ipw3945: Unknown symbol alloc_ieee80211


```

And when I run this one:

```
dmesg | grep Wireless

[17179582.776000] wlan0: ethernet device 00:1b:77:29:84:86 using NDIS driver: netw39x5, version: 0x10048, NDIS version: 0x501, vendor: 'Intel(R) PRO/Wireless 3945ABG LAN Card Driver', 8086:4222.5.conf


```

---

### Post by harty83 on 2007-06-28
Just to make sure.  Do you have the linux-restricted-modules for your kernel installed?

```
sudo apt-get install linux-restricted-modules-2.6.17-11-generic
```

---

### Post by Dr. Octagon on 2007-06-28
I found a thread elsewhere about how to install ndiswrapper, and now I can see the interface (eth1) but it will not detect any networks.  I am thinking about upgrading to Feisty but I just got beryl rockin' on here and it looks great.

---

### Post by harty83 on 2007-06-28
If you have installed the restricted modules, you should have native drivers your card.  I would try that rather than working with ndiswrapper.

I have compiz fusion installed on Feisty and everything is working great for me.  What type of graphics card do you have?

---

### Post by harty83 on 2007-06-28
Couple compiz fusion screenshots on Feisty.  FYI in case you don't know, compiz fusion is the future of beryl which is no longer developed.  Compiz and beryl combined to make compiz fusion.

Did you get that wireless working?

---

### Post by Dr. Octagon on 2007-06-28
I have a Nvidia NVS 110m w/ 256.  I just got this laptop for work and it's a HOSS compared to my last one.  2.33 Core 2 Duo, 4GB, 160GB, and no effing wireless:mad:  Oh well, I kinda got scared off by Feisty the first time I tried it, but it was in it's early stages.  Thanks for your help.

---

### Post by Dr. Octagon on 2007-06-29
And now no wireless in Feisty. :(

---

### Post by chili555 on 2007-06-29
The ipw3945 is very well supported and easy to set up. I'm answering this post using mine.

Do you have *linux-restricted-modules* installed? Open a terminal and do:```
dpkg -l | grep restricted
```If you are using Gnome, can you select System-Administration-Restricted Driver Manager and check off the Intel Pro Wireless driver? Finally, what does```
iwconfig
``` tell us?

A last possibilty is the rf_kill switch is on. Check with:```
sudo cat /var/log/messages | grep -i kill
```

---

### Post by Dr. Octagon on 2007-06-29
I tried this:
```
doctor@kubuntu:~$ dpkg -l | grep restricted

ii  linux-restricted-modules-2.6.20-15-generic 2.6.20.5-15.20                         Non-free Linux 2.6.20 modules on x86/x86_64

ii  linux-restricted-modules-common            2.6.20.5-15.20                         Non-free Linux 2.6.20 modules helper script

ii  linux-restricted-modules-generic           2.6.20.15.14                           Restricted Linux modules for generic kernels
```
Then I executed this:
```
doctor@kubuntu:~$ iwconfig 

lo        no wireless extensions.



eth0      no wireless extensions.




```

But I still can't see my eth1.

---

### Post by harty83 on 2007-06-29
Just to make sure.  I'm only saying this because it has happened to me before (yes I admit it).  Does your laptop have a wireless on/off button?  My compaq does and I got headache one day figuring out what was wrong with my wireless when I realized it was turned off!

---

### Post by Dr. Octagon on 2007-06-29
Nah, I've done the same thing before but unfortunately it is not to blame this time.  I wish it was.

---

### Post by stchman on 2007-06-29
> **Dr. Octagon said:**
> I recently did a fresh install of Kubuntu Edgy 6.10 and have never been able to see my wireless card.  My notebook is a Dell Latitude d620 and the wireless card in question is an Intel PRO/Wireless 3945ABG.  I have tried various fixes and scoured numerous threads to no avail.  Help me please!

The 3945 works out of the box with Feisty.  My dad has a 7600Go and a 3945 video cad in his laptop and both work perfectly under Feisty.

---

### Post by harty83 on 2007-06-29
Okay so you are using kubuntu and I'm not for sure if it comes with a restricted mangager (at least I can't find one in my installation).  

Try installing gnome's and lets see if it recognizes the card:

```
sudo apt-get install restricted-manager
```

Doesn't look like it is dependent on anything gnome specific other than synaptic so you shouldn't get a bunch of gnome apps along with it.

Once installed hit alt-f2 and type ```
kdesu restricted-manager
```

Post back on what you get.

---

### Post by Dr. Octagon on 2007-07-02
"In order for this computer to function properly, Ubuntu may be using driver software that cannot be supported.

Because the software is proprietary, it cannot easily be changed to fix any future problems."

It says that my Intel PRO/Wireless 3945 driver is enabled but is not in use.

---

### Post by Dr. Octagon on 2007-07-02
I installed Ubuntu Feisty and everything looks good.  Oh yea, Compiz Fusion rules.  Thanks for the help!

---

### Post by harty83 on 2007-07-02
I'm glad its all working for you!

Alan

---

