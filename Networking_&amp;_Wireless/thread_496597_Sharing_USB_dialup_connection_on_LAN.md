---
title: "Sharing USB dialup connection on LAN"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by oberdober on 2007-07-09
Hello everyone :) I have been trying to share my dial up internet connection (braodband wireless,Telstra 3G) using a USB connection as that is all that is available. I can connect to the internet using the modem but then my network connection won't work. I have tried masquerading and NAT techniques and they don't seem to work (I'd say the reason is doesn't work is my dopey fault...). I have also tried using firestarter and I can't get that to work either. It either says that there is an unknown network problem, or it shows no errors and I cannot connect to any other computers on the LAN. My setup is:

Maxon BP3-EXT wireless USB modem (Dial up) (Dynamic network address)
Ubuntu Feisty server box 
Belkin router (192.168.2.0/24) (LAN gateway IP 192.168.2.1)

I would LIKE to share the connection with:
OpenSUSE 10.2 box
OpenSUSE 10.2 laptop
2 Win XP boxes
Ubuntu Feisty box
Ubuntu Feisty server box

The box that the modem is connected to:
eth0 
192.168.2.2
255.255.255.0
127.0.0.1 (If i change this to anything else I lose the internet connection)

ppp0
Details automatically assigned from ISP

Any suggestion would be greatly appreciated, thanks :)
Cheers, Ober.

*EDIT* Oh, I forgot to mention that I am using kppp for the dialup connection.

---

### Post by t4thfavor on 2007-07-09
what is stopping you from using ipcop to share that connection? I use my motorazr to share a cdma connection, which can't be much different.

Other than that, I don't really know what else you could try other than maybe you had nat set up incorrectly.

Sorry if I was no help, but nobody else even tried.

---

### Post by oberdober on 2007-07-09
Fear...... is what is stopping me i guess, it took me two days to get the modem working and about a week of research beforehand. I'd say our connections would be similar if not the same, so I guess if no-one else has any other suggestions I might have to bite the bullet and ditch Ubuntu for ipcop :( Do you use pon and poff to start the modem? if you do is there any way I can can copy the scripts that kppp uses? I cannot seem to find where it stores the dial up scripts. I do have webmin on the modem box but I can't make head nor tail of those settings....
Thanks for responding by the way :)
Cheers, Ober.

---

