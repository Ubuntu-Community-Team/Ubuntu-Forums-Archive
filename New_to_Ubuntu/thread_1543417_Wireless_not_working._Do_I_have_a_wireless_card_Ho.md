---
title: "Wireless not working. Do I have a wireless card? How can I find out?"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by dissembly on 2010-08-01
Hi all,

I recently got a small 10" laptop with Ubuntu (Karmic Koala) pre-loaded, and, according to the invoice and the order i placed, a wireless card: Either "Wireless LAN 802.11b+g+n Half MiniCard module" or "Intel WiFi Link 1000 1x2 802.11b+g+n" - i do not know which. (I ordered it online, and ticked the box that said "802.11 b/g/n Wireless" - it did not specify further which of the "802.11 b/g/n" cards it was.)

So i've started it up, and everything seems to be working fine, except that there seems to be no automatic detection of the wireless card.

The little wireless network icon shows no "bars", and when i click on it, the menu says:

"
Wired Network
   disconnected
_____________
VPN Connections ->
"

There is no "Wireless Network" option.

So i thought, maybe it is a driver issue. (I have heard that sometimes there are "proprietary drivers" and you need to load them into Ubuntu yourself; and when i search for hardware drivers, it returns the message "there are no proprietary drivers on this system".)

So i've spent the last day and a half going through tutorials for the purpose of installing wireless card drivers; this the most recent one i've found, there are others i've been to that i have not understood at all:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

In section 3.2, it says "3.2. Identifying Wireless Adapter"

But i don't understand how I am to tell which of the things listed (when i enter "lspci" os "lsusb" in Terminal) is a wireless card. Can Ubuntu even tell me which one is a wireless card if it doesn't have the driver necessary to identifying a wireless card?

The information returned from "lspci" is roughly:

Host bridge
VGA compatible controller
Display controller
Audio device
PCI bridge
PCI bridge
PCI bridge
USB Controller
USB Controller
USB Controller
USB Controller
USB Controller
PCI bridge
ISA bridge
SMBus
Network controller
System peripheral
SD Host controller
System peripheral
Ethernet controller

I can make a guess that things like "Audio device", "Ethernet controller" and "VGA controller" are not wireless cards, but in general, I have little idea of what any of these are. I couldn't rule any of them out as being a wireless card, with my level of knowledge. But the tutorial, and all the tutorials i've found, seem to depend on me knowing what wireless card (or what "chipset"?) I have.

And now I am wondering if the place i ordered the laptop from perhaps did not give me the model I ordered (i.e. with the integrated "802.11 b/g/n" option). I have sent an e-mail off to them to check on this, but had no response as yet (it's the weekend), and if they did make a mistake, i am worried they will respond with something like "Mail the laptop back to us and we'll see" - which would be a MASSIVE pain in the ****, especially if it turns out the wireless card was there somewhere all alone - i'm sure you can imagine. (I've been waiting for this machine for a while, and already spent a few hours learning and configuring it, and loading my personal data (90 gigs worth) onto the hard disk.)

Then there are a couple of other questions i have:

For example, step 3.1. requires you disable any wireless drivers already installed. How do i know if i even have one already installed? And if i disable it, and then it turns out that the driver was not my problem (or NDISWrapper does not work, or something like that), is there an easy way for me to restore things back to normal?

And then in section 5 it says "Compiling the latest version of NDISWrapper" - but, i thought that was what the whole tutorial was about? This really confused me.

Can anybody help me? Perhaps clarify these last two questions, or point me in the direction of a more dumbed-down, hand-holding tutorial? 

And, how do i figure out whether or not i have a wireless card, and if so, what kind?

Any help appreciated.

- David

---

### Post by jtarin on 2010-08-01
> Network controller
What other info does it give for this listing.


You could see if dmesg might be able to tell you the kind of wireless card you have.
You could try this command in a terminal
 ```
dmesg | grep -i "wireless"
```

On the off-chance its a USB device
```
lsusb -v
```

---

### Post by dissembly on 2010-08-01
Thank-you for replying so quickly.

The full line for "network controller" says:

05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

I tried the command:
dmesg | grep -i "wireless"...but it just took me back to the command prompt, without returning any information.

lsusb -v
That returns information on five "Bus"es, which all say "hub" somewhere in their descriptions, so I am guessing those are the available USB connections to my computer (on the outside, there is one ethernet plug, two USBs, one blue 15-pin connector and one SD slot - i am guessing those are the five buses?), and one mouse.

---

### Post by jtarin on 2010-08-01
OK,,,you've got a Realtek 8172...I don't have time now but I suggest you do a Google for "Realtek 8172 module Linux" and see what module you need to load to get this working. When you have determined the module issue the command ```
lsmod
```to see if its loaded or not. If not you will need to use the command ```
modprobe modulename
``` to load it.

---

### Post by dissembly on 2010-08-01
Ahhhhhhhhhhhh!!

I searched for it then, and, among other things, found this:

[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

...which looks to be exactly what i need.

Thank-you so much for pointing me in the right direction! I really appreciate that. I think i should be able to figure it out from here with the link above and the commands you provided.

Thank-you again for the fast and helpful replies. :)

---

