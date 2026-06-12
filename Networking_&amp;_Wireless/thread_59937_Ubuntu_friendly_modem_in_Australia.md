---
title: "Ubuntu friendly modem in Australia???"
date: 2005-08-25
forum: Networking &amp; Wireless
---

### Post by occy8 on 2005-08-25
Hi, I moved recently and have only dial up now.
I don't want to go through the trouble with my winmodem and like to buy a new or used external modem.
I'm in Australia and the main brands here are Netcomm and Swann and D-link.
If anyone has positive experience with any of their modems please list them here

thanks

---

### Post by tristan on 2005-08-25
You should have pretty much no problems with any of the above external modems (I use an old netcomm 33.4), just make sure that you use pppconfig to set it up initially (the ubuntu dialup networking tools are a bit of a dog), and then install gnome-ppp for your day to day diaup requirements.

---

### Post by moopere on 2005-08-25
[QUOTE=occy8]Hi, I moved recently and have only dial up now.
I don't want to go through the trouble with my winmodem and like to buy a new or used external modem.
I'm in Australia and the main brands here are Netcomm and Swann and D-link.
If anyone has positive experience with any of their modems please list them here

thanks[/QUOTE]

As Tristan says, any external modem should be fine, but make sure its 'serial'.  I've not seen any USB dialup models around but there probably are some.

I've used most of the Netcomm range and a fair number of dlink, Mitsubishi serial modems, all have been fine.

Cheers,
Craig

---

### Post by Unix_Wizard on 2005-08-26
[QUOTE=moopere]As Tristan says, any external modem should be fine, but make sure its 'serial'.  I've not seen any USB dialup models around but there probably are some.

I've used most of the Netcomm range and a fair number of dlink, Mitsubishi serial modems, all have been fine.

Cheers,
Craig[/QUOTE]
 What's wrong with USB? I'm thinking of buying a USB one but your statement puzzled me.

---

### Post by occy8 on 2005-09-03
hi guys
thanks for helping I received a swann smart2 in the mail, bought at ebay for less then 20 bucks incl postage. figured out how to connect in less then 2 hours all by myself 
hehehe had a great day :grin:

---

### Post by moopere on 2005-09-03
[QUOTE=Unix_Wizard]What's wrong with USB? I'm thinking of buying a USB one but your statement puzzled me.[/QUOTE]

Maybe nothing.  Trouble is that until recently almost all USB devices were at the *cough* cheaper end of the scale of products.  Given this, low end devices like modems tended to have almost no brains at all relying instead on binary blob firmware which is loaded at runtime and is expected to be interactive (via a 'driver') with the OS.  You can guess which OS this usually is.

Given this then, what chance do you have of getting such devices to work with so called 'unsupported' operating systems?  You might, but good luck.

In recent times, with a lot more USB devices around, there appears to be a fully functional market with the usual high, mid and low end devices for most types/catagories of product.  The same caveats as always apply though - make sure it will work under Linux before you buy - its a great way to weed out crap manufacturers (ie, don't buy their stuff, they go broke).

Cheers,
Craig

---

### Post by occy8 on 2005-09-03
> 
Originally Posted by Unix_Wizard
What's wrong with USB? I'm thinking of buying a USB one but your statement puzzled me. 


When I googled for hot to configure my modem I found this excellent instruction
from an isp who cares about Linux users. They talk about USB modems too
[http://www.melbpc.org.au/faq/linux_dial.html](http://www.melbpc.org.au/faq/linux_dial.html)

---

### Post by Drat on 2005-09-23
[QUOTE=tristan]You should have pretty much no problems with any of the above external modems (I use an old netcomm 33.4), just make sure that you use pppconfig to set it up initially (the ubuntu dialup networking tools are a bit of a dog), and then install gnome-ppp for your day to day diaup requirements.[/QUOTE]
 I used the Ubuntu networking to set up my dialup mdem initially but resorted to ppp config to increase the speed. This worked for a while but now reverts to the former. 
How do I disable the slower default or  load gnome-ppp?
Can it be reconfigured using ppp config?
Cheers,

---

