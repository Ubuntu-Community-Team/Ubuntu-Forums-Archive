---
title: "evdo alltel + pantech modem simple how to"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by slick_8199 on 2008-07-12
Over the past week I have tried a lot of things to get my internet working in ubuntu with mediocre results. I installed gnome-ppp and it worked but I thought there  could be an easier way. (installing gnome-ppp without an internet connection sux I ended up in dependicy hell.) I wanted to find a way to do it in the future if I have to reinstall without having to boot to winblows.

Through gritted teeth and almost smashed laptop I have finely figured out how to get my pantech usb broadband evdo modem working (the easy way).

1) open terminal and type sudo wvdialconf
2) in terminal type sudo gedit /etc/wvdial.conf
3) after Init1 make it say ATX0.
   username is INSERTPHONE#HERE@alltel.net
   password is alltel

save and close
4) in terminal type wvdial

you should be on the internet now. make sure to uncheck work offline under file in the browser.


Sorry if this is not formated correctly I'm new.

---

