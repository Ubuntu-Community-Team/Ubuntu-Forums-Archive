---
title: "New 8.10 install with no Wifi"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by 3dmaker on 2008-11-17
Hello everyone, with most older editions of Ubuntu I was easily able to get my Broadcom chip to work by going to System>Adminstration>Restricted Drivers.

Now if I go there, there is only the ATI Graphics driver. Nothing else. I can't get wireless to work, and Synaptics cant seem to find bcm43xx-fwcutter or anything like that. What is this? Why isn't my wireless working anymore.

---

### Post by jnorthr on 2008-11-17
you will need to get the new firmware patch ucode5.fw (or something like this) in order to get your bcm43xx to work. I found this on another post in this forum so if we hunt around here we might find the original post cos it had a link to a site where they had already done the fwcutter bit and it was just download-install.

will look.

---

### Post by jnorthr on 2008-11-17
sorry could not find that link, but i have used it to make this system work by placing copies of ucode5.fw into these folders:

jim@tiny:~$ locate ucode5.fw
locate ucode5.fw
[B][COLOR="DarkOrange"]/lib/firmware/ucode5.fw
/lib/firmware/b43/ucode5.fw
/lib/firmware/b43legacy/ucode5.fw[/COLOR][/B]

then doing a reboot. It took several minutes for my router to finally 'see' my system so be patient. :popcorn::popcorn:

---

