---
title: "[SOLVED] Problems with Wireless network on Toshiba, detects networks but can not conn"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by mroski on 2008-10-11
HI Firends, I have a Toshiba Satellite A305D-SP6801 (AMD 64 and the same hardware all A305D have). This laptop has a Wireless network adapter from Atheros which as I have seen in Google it is one of the most problematics if not the most problematic for Ubuntu.
I've achieved after a lot of work to make it work and to detect wireless networks on ratio with this adapter (still can not believe this !) but when I thought everything was solved I found one new problem which Google couldn't solve.

When I click the network I would like to connect to, Ubuntu asks for the WPA password (this is correct, the network security is personal WPA), I type the password and it starts connecting, after a while it connects but I can not browse the net with firefox, not even Google works. After a while it asks me for the password again and a loop starts. I have tried to connect manually by inserting the ESSID and a static IP adress but I still can not browse the net.
I have checked the list of "Attached devices" which my router has but my computer does not appear in that list.

Does somebody have any idea?
Thanks !

---

### Post by biphtec on 2008-10-11
I have a similar issue... Toshiba with Atheros 9k.  I did modprobe and got my wireless addapter up and running, it detected the network, got connected to the net and dhcp worked, but no internet connection.  Did I miss a step?

---

### Post by mroski on 2008-10-11
New info. I have created a new wireless network by clicking the network icon and selecting that option. It appeared to be working fine but then I searched for that new network from another computer with Windows XP which was not far than 3 meters from my laptop and couldn't find the network.

Do you think it may be a problem with the controller?
I installed it with madwifi and now in System -> Hardware Controllers appears Atheros and some text, sorry but as I haven't got Internet in Ubuntu I am using another computer so I can not read what says. That controller appears as "In Use".

Any idea???

---

### Post by mroski on 2008-10-11
SOLVED !

The solution was much more than stup@#, the password of my Network has a 'ñ' and apparently Ubuntu could not connect to the network because of that 'ñ', changed that and now it works ! I just can not believe it !

---

### Post by biphtec on 2008-10-12
Nice work!  I wish mine was that easy.  I have to keep popping back and forth between vista and ubuntu and its getting old fast.  I'm going to use a thumb drive to copy and paste the typical barf code, maybe that will flag someones memory and get me a fix.  :)

---

### Post by mroski on 2008-10-13
If you can connect to the network then everything should be working fine (should).
What you can check is wether the router detects you or not, thats something important.
If I were you I would try to go to a mall or somewhere with free WiFi access and check if Internet works.

Why don't you open a new topic here?
Maybe someone with higer experience could help you better.

Regards.

---

