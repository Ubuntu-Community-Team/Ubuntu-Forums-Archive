---
title: "No wifi adaptef found"
date: 2018-05-06
forum: Networking &amp; Wireless
---

### Post by nicknamen on 2018-05-06
Hi,

suddenly my wifi stopped working. I tried in any way to adjust it but it did not work.

I cannot upload the wireless-info.txt cause apparently it exceeds the size limit. Here is the pastebin link: [http://paste.ubuntu.com/p/JvxmhT5yG4/](http://paste.ubuntu.com/p/JvxmhT5yG4/)

Thanks in advance for the help.

---

### Post by chili555 on 2018-05-06
> 1: phy0: Wireless LAN
	Soft blocked: no
	[COLOR="#FF0000"]Hard blocked: yes[/COLOR]This suggests that the hardware switch or key combination, sometimes called Airplane Mode, is set to turn off the wireless radio. Please find the switch and change it.

---

### Post by praseodym on 2018-05-07
Additionally, it loads a Broadcom driver, module wl.
```

sudo modprobe -rfv wl
sudo apt-get remove --purge broadcom-sta-dkms bcmwl-kernel-source
```
Rebot

---

