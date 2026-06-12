---
title: "USB ID for Linksys WUSB54GP v4"
date: 2005-10-19
forum: Networking &amp; Wireless
---

### Post by Florent on 2005-10-19
Hi all,

I have a USB wifi adapter: Linksys WUSB54GP v4 and two questions for you.
[LIST=1]
[*]Is it normal that it does not have a comment while using lsusb in Breezy ?
I only get the USB ID which is 13b1:0011
[*]It seems to be a Ralink chipset : [http://www.m0n0.ch/wall/list/showmsg.php?id=147/83](http://www.m0n0.ch/wall/list/showmsg.php?id=147/83) and [http://www.google.com/search?q=0x13b1+0x0011](http://www.google.com/search?q=0x13b1+0x0011) , but everyone is using Ndiswrapper to set it up. Is there a reason ? Is it a different chipset . What's the best way to install it ?
[/LIST]
Thanks for your help

---

### Post by william_nbg on 2005-10-19
I have the same card, 'g520+' with the acx111 chip. It worked fine under hoary without out any changes, although, no wep. In breezy It wasn't recognized in the install, but I simply copied by '/etc/network/interfaces' file over from Hoary and it works fine in Breezy. But sometimes when I boot-up it doesn't come on so I run a small script I made and it always comes on.

Script:

sudo /etc/init.d/networking stop
sudo modprobe -r acx_pci
sudo modprobe acx_pci
sudo /etc/init.d/networking start

paste the script in a text file and name it 'net_start.sh'
and then run 'sudo sh net_start.sh' in comand line.

Hope they work out this bug soon, because the rest of Breezy is running just fantistic on my box.

If not, think I'll get a card with a prism chip.:)

---

### Post by Florent on 2005-10-20
[QUOTE=william_nbg]I have the same card, 'g520+' with the acx111 chip. *(snip)* [/QUOTE]

I think you misplaced your answer. I'm talking about a Linksys product, not a DLink !
Nevertheless, good luck with your issue ;)

---

### Post by william_nbg on 2005-10-20
Sorry, I went to help someone else out, but when I went to submit my reply I somehow jumped to another thread. Maybe I clicked wrong somewhere.;)

---

### Post by tmattoneill on 2005-10-20
If anyone ever does come up with some help on this, can we know the answer for v1 as well?

---

### Post by mjo on 2006-03-17
Hi,

Is there ANYONE who has got this Linksys adapter to work?

[http://www.qbik.ch/usb/devices/showdev.php?id=3390]("http://www.qbik.ch/usb/devices/showdev.php?id=3390")

BR,
-- MJo
ps. 2 weeks, Dapper amd64/32bit tried, Breezy amd64 and now starting combat with  vanilla Breezy i386. Ndiswrapper, [http://rt2x00.serialmonkey.com/]("http://rt2x00.serialmonkey.com/"), [http://www.ralinktech.com/supp-1.htm]("http://www.ralinktech.com/supp-1.htm"),  nightbuilds among releases for all imaginable drivers (e.g. ural drivers also) tried. Still no wlan :-k

---

