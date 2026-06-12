---
title: "Installing Lubuntu 19.10 on Asus X205T - no nvram files in /sys/firmware/efi/efivars"
date: 2020-01-24
forum: Networking &amp; Wireless
---

### Post by unilynx on 2020-01-24
I'm trying to install Lubuntu 19.10 on an Asus X205T, but I get stuck installing Wifi drivers

All guides I can find (eg [http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/comment-page-2/](http://www.jfwhome.com/2016/01/04/latest-steps-to-install-ubuntu-on-the-asus-t100ta/comment-page-2/)) at some point want me to copy a nvram file from the 'efivars' directory, eg

cp /sys/firmware/efi/efivars/nvram-74b00bd9-805a-4d61-b51f-43268123d113 /lib/firmware/brcm/brcmfmac43340-sdio.txt

but this file is not there. I haven't got any file starting with 'nvram-' in efivars, although I have files starting with 'Setup-', 'UsbSupport-' etc. 

Attempting to download this file from the web and writing it to the specified location doesn't help either. Errors from dmesg suggest that the driver is actually looking for "brcmfmac43340-sdio.ASUSTeK COMPUTER INC.-X205TA.txt" but giving the random files I downloaded that name doesn't help either. And the latter name hardly turns up any hits on Google, so I think I'm on the wrong track.

So I think I do need these 'nvram-' files. Any idea on how to get them to appear, and what I'm missing if I don't see these?

(i've tried unmounting and remounting the efivars, but that didn't make the nvram files appear either)

---

