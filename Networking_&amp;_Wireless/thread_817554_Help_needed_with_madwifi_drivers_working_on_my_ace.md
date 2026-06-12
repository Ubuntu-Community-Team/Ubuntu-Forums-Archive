---
title: "Help needed with madwifi drivers working on my acer aspire 4720z with ubuntu 8.04"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by arunvir on 2008-06-03
First, I need to thank all people in this forum for the help they have provided. I was or wasn't (BCOZ I DONT KNOW) able to install the new madwifi drivers for the Atheros 5007EG on my acer aspire 4720z correctly. I know one thing for sure now - I got something to work. But I might need help in understanding how the stuff actually works or whether it works.

I did just some initial researches here and there and finally found the things that told me that I atleast got my madwifi installation correct. I'm attaching the proof's for it. 

Kindly look into the attachments for them.


The things that are confusing me right now are:-

1) Is my card turned on right from the time ubuntu is booted?.
If so how can I confirm that whether it is on ?
( A small help with the terminal commands) Any command for turning my card on or off from the terminal.


2)I find that the soft switch nor the LED is functioning in my acer laptop. Does this mean the driver ain't working (for the moment) or is there something more I got to tweak to get them working?

Note: My current situation: Living in my grandma's house in native place.I practically have no access to any wireless networks for the next  month till I get back to my college or city. I bought this laptop a week before. 

Previous experience with wireless networking in ubuntu:- Nil.

My reason for meddling:- just my curiosity, to know whether I'm doing things right.

Any help will be greatly thanked and appreciated.

The madwifi drivers I installed:- madwifi-nr-r3366+ar5007.tar.gz
:confused::confused::confused::confused:

---

### Post by kleugers84 on 2008-06-03
Hi, I too have an Acer Aspire laptop with the same Atheros wireless networking card. I was working on this last night in installing the madwifi drivers. My iwconfig looks the same as yours now after installing the drivers. It seems to recognize the card, but I cannot see any wireless networks. At work now, but will be playing with it some more later tonight.

To help with your questions:
1 - yes, the card is initialized when you boot up ubuntu, not sure how you can turn off/on through terminal.

2 - The networking LED on your laptop probably will not work with ubuntu, from what I can tell the button is mapped to the Acer software in Windows. The card is just always on, unless there is a way to disable it through a terminal command.

---

### Post by arunvir on 2008-06-03
thanks!!!!!!!!!!!

So lets continue sailing on the same boat until some titanic passes us by!!

(meaning When some one really super great in these helps both of us out.)

With respect to mapping the soft switch, I read on a forum post that it can be done. But requires mapping of some modules to the key and the LED. 

(I really dont know where this mapping has got to be.)

---

