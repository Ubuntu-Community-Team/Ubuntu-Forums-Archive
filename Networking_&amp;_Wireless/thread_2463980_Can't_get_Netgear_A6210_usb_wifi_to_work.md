---
title: "Can't get Netgear A6210 usb wifi to work"
date: 2021-06-22
forum: Networking &amp; Wireless
---

### Post by seattle vic on 2021-06-22
I'm running 21.04 on an older desktop sitting in my garage where I use it as a file server for backups.  The integrated wifi adapter is only 2Ghz and I want to upgrade it to dual band so I found an old Netgear USB adapter but I can't get the driver to work.
I've tried a couple of drivers on github that require a make process; one finishes with a couple errors but doesn't work and the other gives a whole bunch of mkdir errors.  I probably should brush up on the Makefile stuff as I haven't had to use it in years.

Anyway what I seem to find is that Netgear doesn't support linux (how can that be?) and a lot of other people have struggled with this.  Is there a driver that I can just drop in without going through the make process?

Regarding the internal AP, when I run iwconfig, both are shown but if I run sudo iwlist scan, I get an error for the A6210 (wlx9c3dcff99353  Failed to read scan data : Resource temporarily unavailable).  This does beg the question of if/when I get the dual band unit to work, how do I turn off the internal AP?

Anyway, I'd like to fight my way through this but could use some guidance.  If I can't get this to work I guess I'll just buy a pcie unit from Amazon and hope that it comes with a supported driver...

Thanks in advance.

---

### Post by chili555 on 2021-06-22
>  what I seem to find is that Netgear doesn't support linux (how can that be?)Because Netgear themselves don't manufacture the wireless chip; they buy them in bulk from those that do, in your case, probably Mediatek, and then they put them in a shiny case and a colorful box and market them.

The usual way to disable the internal device is to blacklist its driver. Let's find out which:

```
lspci -nnk | grep 0280 -A3
lsmod | grep mt
```Post the results and we'll proceed.

> Is there a driver that I can just drop in without going through the make process?No, but we may be able to tweak the one you already have.

Note to searchers: Installing a possibly older, buggier driver is almost never helpful.

---

### Post by jeremy31 on 2021-06-22
I have a Netgear A6210 and it works fine on 20.04 with the 5.4 kernels.  See the wireless script link in my signature and post results

---

### Post by seattle vic on 2021-06-22
lspci -nnk | grep 0280 -A3:

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Dell Vostro 3470 [1028:020e]
	Kernel driver in use: ath9k
	Kernel modules: ath9k

lsmod | grep mt:


mt76x2u                28672  0
mt76x2_common          28672  1 mt76x2u
mt76x02_usb            24576  1 mt76x2u
mt76_usb               36864  2 mt76x02_usb,mt76x2u
mt76x02_lib            81920  3 mt76x02_usb,mt76x2u,mt76x2_common
mt76                   73728  5 mt76_usb,mt76x02_lib,mt76x02_usb,mt76x2u,mt76x2_common
mac80211             1028096  5 mt76,ath9k,mt76x02_lib,mt76x02_usb,mt76x2u
cfg80211              892928  7 mt76,ath9k_common,ath9k,mt76x02_lib,ath,mac80211,mt76x02_usb

... and thank you for your help :)

---

### Post by seattle vic on 2021-06-22
> **jeremy31 said:**
> I have a Netgear A6210 and it works fine on 20.04 with the 5.4 kernels.  See the wireless script link in my signature and post results

Hmmm, so you're saying mine should work with existing drivers already in the Kernel.

I ran the script you referenced and it pops out quite a bit of information.  I'll go through it and see if I can do anything with it, but I'm sure you can decipher it better than I.

Did I read that you now have the script results somewhere in this forum?  That's very cool.

Thanks...

---

### Post by chili555 on 2021-06-22
Let's blacklist the internal device:

```
sudo -i
modprobe -r ath9k
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
exit

```
Is there any improvement?

I suspect that both drivers trying to use mac80211 and cfg80211 is part of your issue.

---

### Post by seattle vic on 2021-06-22
> **chili555 said:**
> Let's blacklist the internal device:

```
sudo -i
modprobe -r ath9k
echo "blacklist ath9k"  >>  /etc/modprobe.d/blacklist.conf
exit

```
Is there any improvement?

I suspect that both drivers trying to use mac80211 and cfg80211 is part of your issue.

It worked, and in fact I think it always worked but I was thrown off by the sudo iwlist scan results where the new AP was 'unavailable' along with the fact that two AP's were still shown to be working.

I restarted the OS after the modprobe command (don't know if that's necessary) and I thought that the internal AP showed up with iwconfig, but I did it again and it's not showing up now.  Speed seems improved as I wanted with the 5G band, but I do still get the message: wlx9c3dcff99353  Failed to read scan data : Resource temporarily unavailable.  I'm getting about 45 Mb now.


Could that be a driver issue?  In any event it's working and I've learned some things.

Thank you very much.  This actually incentives me to dig into the whole wireless realm and learn some more.

Vic

---

### Post by seattle vic on 2021-06-22
I do have a question though.  What does it mean when the OS shows two AP's?  In this case a 2G and a 5G.  Which one is used for normal operations?

---

### Post by chili555 on 2021-06-22
> What does it mean when the OS shows two AP's? In this case a 2G and a 5G. Which one is used for normal operations?It means that your router is broadcasting on both bands, almost as if it was two different routers. In fact, I think you might have better luck if you accessed the administration pages of the router and changed the names, something like myrouter2.4 and myrouter5.

I'd suggest a few other changes, too. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

2.4 gHz is slower but has greater range. My mother-in-law, confined to her bed in her suite upstairs, can only see and connect to 2.4 gHz on her ancient phone. 5 gHz is much faster but shorter range. As there is often interference on the 2.4 gHz band from cordless phones, microwaves and even bluetooth, I recommend 5 gHz if possible.

Renaming the two bands on the router makes it possible to connect to *only* the 5 gHz band and disallow the wireless device from roaming, dropping, reconnecting, etc., endlessly.

I suggest that you make the recommended changes above and then let's see if there is improvement.

---

### Post by seattle vic on 2021-06-22
> **chili555 said:**
> It means that your router is broadcasting on both bands, almost as if it was two different routers. In fact, I think you might have better luck if you accessed the administration pages of the router and changed the names, something like myrouter2.4 and myrouter5.

I'd suggest a few other changes, too. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

2.4 gHz is slower but has greater range. My mother-in-law, confined to her bed in her suite upstairs, can only see and connect to 2.4 gHz on her ancient phone. 5 gHz is much faster but shorter range. As there is often interference on the 2.4 gHz band from cordless phones, microwaves and even bluetooth, I recommend 5 gHz if possible.

Renaming the two bands on the router makes it possible to connect to *only* the 5 gHz band and disallow the wireless device from roaming, dropping, reconnecting, etc., endlessly.

I suggest that you make the recommended changes above and then let's see if there is improvement.

I already had named the 2G and 5G bands different.  I use WPA2 and even though AES is not an option (neither is TKIP), the manual for my router (linksys WRT1900ACS) says it uses AES.  2.4 was set to mixed, I set it to b/g/n and the channel to 6.  Didn't really see much of a change for speed on the 2G band, though channel 6 seemed to be faster than 1 or 11.

On the 5G band, it was set to mixed and I moved it to ac only and that helped, but what 'really' helped was setting the channel width to 80 MHz.  That brought the speed at my laptop from about 50 Mbit to as much as 200.  I also played with the channels and it seems that channel 151, 5.805G is about the fastest.

Now, the server in the garage, which was what this exercise was for, is now running on the 5G band, but that's through an extender, but that did improve from about 10Mbit on the 2G band to 50 Mbit on the new 5G band with the Netgear A6210 usb device.  I was hoping for more but given the extender this may be all I can expect.  Nevertheless, I may invest in a PCIe card in the hopes that it will have some processing power that may do what the usb device cannot.  Any thoughts on that?

And lastly, any thoughts on why I still get the "Failed to read scan data : Resource temporarily unavailable" on this Netgear AP when running sudo iwlist scanning?

Thank you for your help!

---

### Post by chili555 on 2021-06-23
> And lastly, any thoughts on why I still get the "Failed to read scan data : Resource temporarily unavailable" on this Netgear AP when running sudo iwlist scanning?
I haven't any explanation. Sorry.

---

