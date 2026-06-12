---
title: "Wifi card can see other networks but not my own any explanation?"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by A*p on 2007-06-16
This is just odd, I am putting a wifi card in my sisters new computer, I have taken the wifi card out of her old machine which was running Ubuntu 6.06 LTS and put it into a new one with Feisty 7.04. When I goto network manager the card can see 3 of my neibours wifi networks but none of my two.

Both of my networks are displaying the ssid's one is protected and the other is open.  My laptop running edgy can see all of the networks fine.

I can see my networks and get the connection to work by turning roaming off and selecting configure with DHCP when I go into the properties of the wifi device.

***Does anybody know why the card could not see my networks in the first instance?***

Just to recap my networks were on chann 11 and chan 7 both had differend SSID's and were transmiting their name.

---

### Post by NilsE on 2007-06-16
Try changing your broadcast channel on your router to include 6 and see if it finds it.

---

### Post by A*p on 2007-06-16
I tried Chann 6 and that did not work either, the access points that I was using are from different manufactures one is a mixed *b/g* unit and the other an *b* only unit

I did get the connection working but only by turning roaming off (which I assume is the avahi stuff) then selecting from the available networks from the wifi device properties page, my networks were shown so the wifi card was able to see them.

Anyway I have just dropped off the PC at my sisters so sadly I cannot try any further testing.  But this was defiantly an odd thing.  I know for sure that their is nothing wrong with any of the Wireless AP's that I use.

---

