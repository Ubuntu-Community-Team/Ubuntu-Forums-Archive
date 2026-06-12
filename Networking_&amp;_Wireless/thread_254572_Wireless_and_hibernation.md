---
title: "Wireless and hibernation"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by cookfromfrozen on 2006-09-10
Hi.

I have a PCMCIA card based on the Atheros chipset.  I have WPA support working through wpasupplicant.

My /etc/network/interfaces file is similar to the following:

```

iface ath0 inet dhcp
pre-up wpa_supplicant -B -w -i ath0 -Dmadwifi -c /etc/wpa_supplicant.conf

```

Now, when I put my laptop into hibernation, when I bring it out of hibernation, it brings the interface back up but doesn't reconnect to my access point.  I have to manually restart networking by doing:

```

sudo /etc/init.d/networking restart

```

Is there any way I can make it refresh the wireless connection after coming out of hibernation?

Thanks.

---

### Post by spd106 on 2006-09-10
I found that back on breezy Network Manager was able to reconnect after suspend. I think that was because it liked to scan for APs every couple of minutes, causing my Atheros card to disconnect. Then reconnect after the scan. Sadly this became too annoying for normal use since the internet connection would also be dropped every two minutes. I think this has been improved in the madwifi-ng driver.

From the posts i've read on this forum suspend is still very patchy in Ubuntu. Maybe Edgy will work be better.

---

