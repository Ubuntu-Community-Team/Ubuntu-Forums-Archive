---
title: "ath0 has wrong mac address"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by slowpoke115 on 2008-04-13
Hi all, when I boot my computer my wifi card has the correct mac address:

ifconfig | grep -a HW
ath0 Link encap:Ethernet HWaddr 00:15:AF:67:96:24
wifi0 Link encap:UNSPEC HWaddr 00-15-AF-67-96-24-00-00-00-00-00-00-00-00-00-00

Now if I destroy and put ath0 in monitor mode the following happens:

ifconfig ath0 down
wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor
ifconfig | grep -a HW
ath0 Link encap:UNSPEC HWaddr 06-15-AF-67-96-24-40-E2-00-00-00-00-00-00-00-00
wifi0 Link encap:UNSPEC HWaddr 00-15-AF-67-96-24-00-00-00-00-00-00-00-00-00-00

In managed mode it shows this:
ath0 Link encap:Ethernet HWaddr 06:15:AF:67:96:24
wifi0 Link encap:UNSPEC HWaddr 00-15-AF-67-96-24-00-00-00-00-00-00-00-00-00-00

Notice the weird unholyness, basically it works at boot time and the addy is correct then when I make a change, the mac address is entirely (I say entirely its the first and last few digits) different!

Any ideas on fixing this? I've tried macchanger (works until I reboot) and ifconfig ath0 hw ether blah, also works till I reboot. It's a real pain as I can't connect to anything and I'm not keen on changing the mac every 5 minutes :(.

Thanks for the help :)

---

### Post by mrsteveman1 on 2008-04-13
I was gonna blame the driver (and i still may), but the first 3 bytes of a MAC are the manufacturer, they shouldn't ever change unless you change them.

The sole exception i can think of for a driver changing the mac address depending on the mode, is perhaps so that it appears to all connected layer 2 devices as a different device, perhaps to avoid weird issues later on.

I dunno, it's definitely the driver. Have you checked around on the madwifi site for bug reports?

---

### Post by slowpoke115 on 2008-04-14
One guy had a similar issue on the mad wifi forum, although the ticket was closed as they blamed human intervention. I should mention that this has previously worked without ANY problems and I have changed the mac address before (potential problem here...).

Is there a config file or something that has mac addresses in? I was thinking it could be that my wifi0 mac is wrong and my ath0 address is correct, but the way I understand it the ath0 gets all its details from wifi0 to make a VAP.

Thanks for your help anyway, I may well consult those mad wifi chaps for some assistance.

---

### Post by The Tronyx on 2008-04-14
Try using this syntax with the appropriate information for your card and interface(s).
```

sudo ifconfig eth0 down hw ether 00:00:00:00:00:09
sudo ifconfig eth0 up

```

---

### Post by slowpoke115 on 2008-04-14
Tried that, it works until I reboot and comes with a few problems when packet injecting (AP needs to be in monitor mode and mac cannot be changed).

I've no idea how it became different to wifi0 in the first place.

---

### Post by Junglizer on 2008-04-14
It's b/c its being put into monitor mode. It shouldn't make any difference, and I'm not specifically sure what the direct cause of this is, but it is b/c you are putting it into rfmon mode. It only seems to happen with a handful of cards.

---

### Post by slowpoke115 on 2008-04-14
It's only just started happening :( The madwifi forum have said nothing about this. I'm not keen on changing the mac every 2 seconds. Is there no reasoning or solution behind this at all, it's a real pain in the ***! I know it worked once as I was able to connect to my access point and now I have to spoof my mac before i connect to anything and packet injection is impossible :(.

---

### Post by Junglizer on 2008-04-14
You shouldn't actually be connecting to anything if you're in mon mode anyways..?

---

### Post by slowpoke115 on 2008-04-14
OK, heres the problems i'm having and would like to change:

1. Packet injection is almost impossible impossible.
2. Connecting to networks previously available is only pobbile when I change the mac address

Now some points

1. This used to work without any problems at all.
2. Aircrack comes up with errors when it didn't used to :(.
3. The MAC is wrong and there's no reason for it to be wrong.
4. its annoying.

---

### Post by slowpoke115 on 2008-04-15
Got it! It needed the -bssid flag at the end of wlanconfig, weird. I'm certain I havent always had to put that :S.

---

### Post by manca on 2008-05-13
COuld you please how exactly u solved this, because I am having problems with ath0 changing mac to 06?!

---

### Post by manca on 2008-05-13
just tried with uniquebssid option and it still does not work :((

---

### Post by the_bloods_city on 2008-05-14
i have the same problem like u i have one wireless card but it give me two interface (ath0 - wifi0) and the wifi0 has wrong mac and i cant change it

but i solved this problem by using ( windows wireless driver) and now its give one interface (wlan0) and every thing cool 

i upload it for u
first install the common then the utils the ndisgtk

---

