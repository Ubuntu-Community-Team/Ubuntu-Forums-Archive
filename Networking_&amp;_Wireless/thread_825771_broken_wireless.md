---
title: "broken wireless"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by jdwood83 on 2008-06-11
I have been running Ubuntu on my laptop for a year now, and I have had no problems connecting to the internet until now. I went away for a week (for my honeymoon) where I had no internet access, and when I came back I had 81 updates to install. Since that completed a few days ago, I have had no internet. I checked the normal stuff (iwconfig, etc) and my wireless card is not listed. I then noticed that my System/Administration/Hardware Drivers says that the wireless card is 'not in use.' I tried reinitializing it with no luck there. Is there anything I can try before reinstalling Hardy (which I'd rather not do)??

~$ iwconfig
lo    no wireless extensions

eth0  no wireless extensions

(my normal wireless card was listed under ath0)


Any help would be greatly appreciated!

---

### Post by superprash2003 on 2008-06-11
connect your laptop to a wired connection.. and go to the hardware drivers and ENABLE it.. it normally requires an internet connection..

---

### Post by jdwood83 on 2008-06-11
I tried that and still nothing. It seems like the computer just does not read the card as there at all; I am almost beginning to wonder if there is a power issue with the wireless port (though I was still receiving and sending packets before the shutdown/restart of the lappy after the aforementioned update).

---

