---
title: "belkin wireless card not recognized"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by chrjacks on 2008-12-23
hi everyone. i posted this before but didnt get a workable answer. probably because i didn't give enough info. 

i have a belkin f5d7010 v4 pc card wireless modem. i have used ndiswrapper and to my knowledge i have installed the card. if i run a "ndiswrapper -l" i get:
bcmwl5 : driver installed 
device (14E4:4318 ) present (alternate driver: ssb)

i got the right driver from the belkin website and i believe i have installed it correctly but now the lights aren't on on the pc card and i can't see the wlan device in the network tools.

i am using ubuntu 8.10 (intrepid)

if you have any help this would be great because i've only just started using ubuntu and would love to be able to get into it a little more. i've got no internet on my ubuntu machine because of this problem. i'm posting this from my Eee pc (which, if all goes well, i may setup to run a dual boot system)

thanks in advance and let me know if you need any more information

---

### Post by lord_lethris on 2008-12-23
Take the wireless card back to the shop and get a different one.

Thats the easiest solution, trust me.  Even thought the card itself works excellent under a windows environment, Linux doesn't have the proper support for the chipset on this particular card. :(

**[CENTER]_[SIZE="4"]OR[/SIZE]_[/CENTER]**

If your feeling adventurous.  activate 3rd party/development downloads and look for "windows wireless device" in "add and remove"

then, download the "old" drivers and use this program to install them.

NOTE - Very few people have got this to work.  I got it working once, for about 2 months, then a Kernal update killed the cards drivers and its never worked since.

---

### Post by chrjacks on 2008-12-23
wow thats not the answer i hoping for. but thanks anyway. i'm a real newbie as far as linux/ubuntu goes so i'm not sure how in-depth i should get into it.

the card is about 3-4 years old so taking it back to the store isnt an option. it was the one i had for ages so i was hoping it would work with minimal effort. oh well... back to square one.

if there is any other options that people know of i'd love to hear them too

---

### Post by kestrel1 on 2008-12-23
I had a Belkin card, but gave up trying to get it working under Linux.
Another card would be a better option. Belkin are not that reliable anyway, even under Windows.

---

### Post by chrjacks on 2008-12-23
thanks everyone. the thing worked for long enough when i needed it to in windows but now it seems destined for the garbage. any recommendations for a new pc card?

---

### Post by chrjacks on 2008-12-23
or should i go with usb?

---

### Post by lord_lethris on 2008-12-23
do a search for compatable USB Dongles, and then pick one.

Netgear seem to work.

FTR, each to his own.  I like belkin stuff, not had any problems with it till I started using Linux.  Now everything I have thats Belkin, doesnt seem to work :(.  Shame really, My Nostrom pad is awesome for games, but I cant use it in linux :(

(slowly loosing faith in linux)

---

