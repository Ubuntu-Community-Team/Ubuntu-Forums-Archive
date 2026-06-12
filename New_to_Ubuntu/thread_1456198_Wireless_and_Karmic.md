---
title: "Wireless and Karmic"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by DM was on fire! on 2010-04-16
Hey kids. Remember me~? From earlier?
You 'member...

I played around with my 9.10 Karmic CD, and it was all rainbows and sunshine and happiness.
...then I had to try and configure my wireless.
It recognizes the card, yay. It recognizes our network, yay. But when I go to connect, I provide the WEP key. It connects and connects...and then it asks for the WEP key again. I provide it, and it connects and connects...and then it just turns into a never-ending circle of misery and woe. 
So what's up? Is it something with our network, or the card, or...?
Give me a moment, I'll provide the type of card it is. The router is a Linksys Wireless G...something or other.

*ETA*; It's [this](http://homesupport.cisco.com/en-us/wireless/lbc/WUSB54GP) lovely creature, first edition software.

I have every bit of information next to me, including the MAC address. But it doesn't seem to be working.

---

### Post by TheNerdAL on 2010-04-16
Did you update your wireless card drivers?

---

### Post by DM was on fire! on 2010-04-16
How would I go about doing that when I have no method of connecting to the internet on this computer? c:

---

### Post by teward on 2010-04-16
you hook your system up to the modem/router/internet with an ethernet cord to update.

---

### Post by MrWES on 2010-04-16
> **DM was on fire! said:**
> Hey kids. Remember me~? From earlier?
You 'member...

I played around with my 9.10 Karmic CD, and it was all rainbows and sunshine and happiness.
...then I had to try and configure my wireless.
It recognizes the card, yay. It recognizes our network, yay. But when I go to connect, I provide the WEP key. It connects and connects...and then it asks for the WEP key again. I provide it, and it connects and connects...and then it just turns into a never-ending circle of misery and woe. 
So what's up? Is it something with our network, or the card, or...?
Give me a moment, I'll provide the type of card it is. The router is a Linksys Wireless G...something or other.

*ETA*; It's [this](http://homesupport.cisco.com/en-us/wireless/lbc/WUSB54GP) lovely creature, first edition software.

I have every bit of information next to me, including the MAC address. But it doesn't seem to be working.

I've always had better luck with WICD.

[https://help.ubuntu.com/community/WICD]("https://help.ubuntu.com/community/WICD")

---

### Post by TheNerdAL on 2010-04-16
> **TrekCaptainUSA said:**
> you hook your system up to the modem/router/internet with an ethernet cord to update.

+1 Yeah do that.

---

### Post by DM was on fire! on 2010-04-16
> **TrekCaptainUSA said:**
> you hook your system up to the modem/router/internet with an ethernet cord to update.

The way the house is set up, I can't do it.
Would it be possible to download the .deb or the .rpm to a thumb drive and install it that way?

---

### Post by Zintha on 2010-04-16
> **DM was on fire! said:**
> The way the house is set up, I can't do it.
Would it be possible to download the .deb or the .rpm to a thumb drive and install it that way?
I don't mean to question you but its hard to think of a setup where its not possible even in the short term.

My routers a little stuck behind stuff and all that but I could shift my PC + a screen out there for 20 minutes and sure it would be in peoples way for a little bit but its possible in the short term.

---

### Post by DM was on fire! on 2010-04-16
No, it's fine.
The way our house is set up, the router is in the living room while our computer is in another room quite some feet away.
I wouldn't be able to carry the router here because there's no phone jack in here and the cables aren't that long, nor would I be able to get the computer set up in there because I would have to unplug everything. :c

---

### Post by anewguy on 2010-04-16
Do you by chance have MAC filtering on the router and didn't add your computer's MAC (not IP) address to the list?

Dave ;)

---

### Post by DM was on fire! on 2010-04-16
No, the MAC filter is disabled. 

Although if it helps any, our WEP encrpytion is sixty-four bits/ten hex bits; and I noticed the only option I had was for 128 bits.

---

### Post by anewguy on 2010-04-17
I'm on Windows right now so I can't check it to see.  In a previous release it let you choose between 64 and 128 bit when setting up a connection, but I honestly don't remember right now with 9.10.  I use WPA-PSK and MAC filtering.

You could try temporarily turning off encryption at the router so you have an "open" network and then just try connecting without any password/passphrase.  If that works, turn on encryption again but try a different password (perhaps 64 bits, or may try WPA instead since WEP can be cracked *VERY* quickly).  Go into network manager, remove any connection that may currently be remembered for your network, then try setting up a new connection and then try connecting again.

Also - is your router broadcasting the SSID?  If not, you must set up the connection manually in network manager and then try connecting.

Dave ;)

---

### Post by DM was on fire! on 2010-04-17
I'm pretty sure when I tried it on Puppy, when I could connect to the network it would pop the SSID up. But on Ubuntu I'm not sure.

I'll have to ask my dad if he can do that. But I'm sure he's so tired of me being on Windows he won't say no. XD

---

