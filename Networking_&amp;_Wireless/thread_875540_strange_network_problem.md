---
title: "strange network problem"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by daberger on 2008-07-30
the old laptop running xubuntu has no problem connecting to the network with on the 802.11g frequency, but roaming anywhere in the house more than ten feet from the router ( i have an excellent router which gives me 100% in this ten feet) drops my internet even though it shows that i am still connected to the network. i had this problem with windows to and it is making me very aggragaveted.

and on a sidenote is it possible to access the files on my networked windows computer from xubuntu? i looked for a network folder but did not find one

---

### Post by cariboo on 2008-07-31
Don'tknow about your wireless problem, but if you are having the same problem in windows on the same laptop, I would suggest it is a problem with the wireless card.

As far as networking with windows, of course. If you have your shares setup on your windows computer and you are in  the same workgroup, Ubuntu defaults to WORKGROUP so it is probably easier to do it in Windows :) Go to Control Panel-->System-->Computer Name and click the Change button, change the workgroup name to match the one in Ubuntu.

To change the workgroup name in Ubuntu:

```
sudo apt-get install samba
```

Edit /etc/samba/smb.conf to match the windows workgroup.

Jim

---

### Post by daberger on 2008-07-31
i know its not a problem with the wireless card because i changed the card before and i still had the same problem.

---

### Post by caljohnsmith on 2008-07-31
Are there any other computers in the house using the wireless network? And if so, do they have any problems?

Are there any devices that could be causing interference? Older cordless phones use approximately the same 2.4 GHz band that 802.11 does, and I know from experience that they can interfere.

---

### Post by linux6994 on 2008-07-31
I would load up prismstumbler via Synaptic it is a utility that will show you the other networks that are in your area (channel, encryption and strength). Wireless routers right out of the box usually run on channel 6 (1 through 11 are available) and if you have a neighbor running on the same channel then you will get interference no matter what OS you have. Try changing the wireless channel on your router to channel 11 and see if your range gets better. Best channel seperation 1,6,11 or 1,3,6,9 11 if things are really crowded.

Good Luck.

---

### Post by daberger on 2008-07-31
caljohnsmith: yes i have probably about ten other devices using wireless and they all work flawlessly and my cordless phones operate in a higher frequency. however i am not sure about cell phones but i really doubt it.

linux6994: since other devices in my house work flawlessly that would be rather futile. but if it makes you happy i can change to channel 11


also i forgot to mention that this laptop used to get internet from twice as far and has degraded over time. so it may be a problem with the motherboard in which i wont be surprised bcuz it is a very old comp

---

