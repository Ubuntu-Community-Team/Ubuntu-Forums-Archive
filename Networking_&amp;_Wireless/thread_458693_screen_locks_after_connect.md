---
title: "screen locks after connect"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by rapa_xd on 2007-05-29
I use wireless connection, and I have RT61 installed and configured.
So, when I start ubuntu, I always have to change the channel and the SSID for the connection works correctly.

But, when I connect and load the page in the browser, some seconds after...puff...screen locks and I have to "reset" computer.

What can i do? :(

Please, help me.
Thanks.

---

### Post by timefortea on 2007-05-30
I am getting a similar problem: I have an Edimax 7108PCg which seems to use the rt61 driver. When I boot from the Ubuntu Feisty CD and the desktop eventually starts, I click on the NetworkManager and key in my network settings. Once I click ok, the NetworkManager icon in the taskbar swirls for a couple of seconds, then the machine appears to completely lock up. 

I just bought this card believing it worked well with Linux (openforeveryone.co.uk sells it as a Linux friendly card) because Feisty seems to have a problem with my other card, a NetGear MA401 (there seems to be a problem with the Orinoco driver). Can anyone recommend a PCMCIA card that actually works, out of the box, with Feisty?? 

Thanks.

---

### Post by chili555 on 2007-05-30
> NetGear MA401 (there seems to be a problem with the Orinoco driver)Easily solved, usually. The problem is that the orinoco *and* hostap *and* prism2 drivers all load and end up fighting for world domination instead of getting busy on emails, instant messaging, torrents, etc. If you:```
lsmod | grep orinoco
lsmod | grep hostap
lsmod | grep prism
```you may see that all three are loaded. Simply *sudo gedit /etc/modprobe.d/blacklist* to add:```
blacklist prism2_<what_you_found>
```It may be prism2_cs or otherwise. You can leave off the .ko extension. After a reboot, your orinoco card should be happy.

---

### Post by unisol on 2007-05-30
i have an rt61 wireless card also with feisty, and when i try to connect it freezes my computer. akso i have wpasupplicant installed but it is not a choice when trying to connect.

---

### Post by timefortea on 2007-05-31
chili555: many thanks for the info but I had tried that without success. The last time it worked was on the last beta of Feisty (3?), with the prism modules blacklisted but when I installed the released version, it sadly did not work. A trawl of the forum and a few links to bugs seemed to suggest an issue with this chipset, so I threw the towel in and bought the Edimax card because I believed this chipset would be ok... sadly not :(

Long ago I would have spent as long as it took to get it going but I don't really have the time any more. If there is a PCMCIA card that works out of the box, I will gladly buy it. Does anyone use NetworkManager? A lot of posts related to wireless problems seems to say to turn it off. It's been around for a while so I wonder what hardware it works with.

So that's prism and rt61 out - what's next? :)

---

