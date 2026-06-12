---
title: "Help with Ubuntu 13.10 and intel 4965 AGN card. N network not visible."
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by murtaza2 on 2014-03-02
Hi All,

Really frustrated with an issue with my wireless network. Recently I have noticed that my Vostro 1500 with a AGN 4965 card is not finding any 5 GHZ networks and is not able to connect to my 5GHZ network either. It finds the 2.4 GHZ network and works fine. Can someone help with this issue and if there is any solution?

thanks,
Ken

---

### Post by varunendra on 2014-03-03
Welcome to the forums Ken!

Intel AGN4965 is an ancient card that belongs to the age of Roman Empire. :P

Okay, more seriously - it belongs to the time when the N-channel support was experimental and was not properly implemented. As such, it has "Draft-N", not "N" support. (refer to this [official document]("http://www.intel.com/content/dam/www/public/us/en/documents/product-briefs/next-gen-wireless-n-brief.pdf"))
Ofcourse when such devices come out, the first OS to get support for it is the almighty windows. Linux comes last, when the vendors get free from all their money-making exercise.

The firmware that Intel released for the AGN4965 card was buggy since the beginning and Intel never cared (or found time) to fix it. After all, who has time to waste with an experimental card when more advanced, properly designed ones have come down the line?

**Bottomline -** Don't expect this card to support modern features with Linux drivers. I doubt if even with Windows drivers it can properly support 5GHz.

---

### Post by murtaza2 on 2014-03-18
Hi Guys,



I upgraded to 13.10 few months ago and since then my Vostro 1500 with the 4965 AGN wifi card hasnt been able to detect my N network. Prior to to the update I was always connect to the N network at 5 MHZ. 

I have searched through the web and this form without any luck. Hoping someone here can help me get my network card working again on the N network.

Here is some info:

0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub0: phy0: 

Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Thanks,
Murtaza

---

### Post by chili555 on 2014-03-21
We wonder if there was a firmware upgrade that was actually, in your case, a downgrade. Let's see what you have there:```
ls -al /lib/firmware | grep 4965
```What firmware is the driver requesting?```
modinfo iwl4965 | grep firmware
dmesg | grep iwl
```My N router switches to the 5 GHz band as it, in its wisdom, decides it needs. If the 2.4 GHz band is quiet, that's all it does. Is that your situation or do you have a different SSID for 5 GHz and it won't connect at all?

---

### Post by murtaza2 on 2014-03-21
Hello,

Thanks for your reply. I understand its an old card but it was working until 13.10 and it would be nice If there was a way to keep it working. Any advice on what u can try?

---

### Post by varunendra on 2014-03-21
> **murtaza2 said:**
> Hello,

Thanks for your reply. I understand its an old card but it was working until 13.10 and it would be nice If there was a way to keep it working. Any advice on what u can try?

I saw your other thread and had discussion about this with our most knowledgeable wireless-guru - chili555, and he thinks it is possible your card can indeed provide that kind of support. Please reply to his post in your other thread : [http://ubuntuforums.org/showthread.php?t=2212019](http://ubuntuforums.org/showthread.php?t=2212019)

Meanwhile, I'd request the mods to merge the threads as they discuss the same topic.

---

### Post by bapoumba on 2014-03-21
Threads merged.

---

### Post by murtaza2 on 2014-08-20
I have a separate SSID for 5 GHZ. It doesn't show any 5 GHZ networks when searching...from what I remember 5 GHZ networks were listed before but since the upgrade they have not been displaying.

---

### Post by chili555 on 2014-08-20
> **murtaza2 said:**
> I have a separate SSID for 5 GHZ. It doesn't show any 5 GHZ networks when searching...from what I remember 5 GHZ networks were listed before but since the upgrade they have not been displaying.Please show us:```
sudo iwlist wlan0 scan
dmesg | grep iwl
```

---

