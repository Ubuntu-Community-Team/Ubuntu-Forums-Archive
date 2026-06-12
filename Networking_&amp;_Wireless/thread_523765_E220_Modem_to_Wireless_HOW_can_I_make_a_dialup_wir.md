---
title: "E220 Modem to Wireless: HOW can I make a dialup wireless router?"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by utakubeta on 2007-08-12
I apologize if the information is posted somewhere else.

Here is my setup:
Huwei E220 "Modem" (supposed to be W/less broadband but is acting like a modem)
       configured to use the wvdial -C wvdial-huawei.config file
       MOVISTAR is the "ISP"
  WORK BEAUTIFULLY (slow as spit, but that&#347; because of the tower we have I think)

I am running it on Feisty with XUbuntu installed (I wanted less overhead)

I can see and play with my USB SMC card, but I am unsure how to make it into a router that OTHER computers can connect to to use internet. (I am fairly confident this part I can do on my own btw). 

Also how can I set up DHCP to give an IP to computers who connect via the wireless?

BUT... I also want to configure the box to connect as needed. That is use the dial script to connect, and after say 10 minutes of inactivity disconnect. I want to set this up so that I can behead the box and stow it away and forget about it, and it will not such my 3 Gig per month DL+UL limit dry in less than 30 days. (I know, at dial up speeds, im unlikely to do that anyway, but I don want it running 24/7 anyway.)

Many thanks for all your help in advance. I rather like Ubuntu and and thiiiiis close to dumping winblows as soon as I figure some other stuff out.

---

### Post by jpl888 on 2007-09-13
Oky doky here we go!

I'm sorry you had to wait 4 weeks for an answer to this post, basically what you're asking is quite advanced and I am 99% sure that USB SMC wireless card you have will not allow you to setup a wireless access point. 

If you want a wireless card that will do this then look to something like a Dlink G650 (which has an Atheros chipset), of course this assumes you have a cardbus slot and not an express card (I found that out the painful way). or for PCI US Robotics do a cheap compatible card (If you need that I will get you the part code).

You don't want to have the HSDPA modem disconnect on idle as it can take up to 30 seconds to connect and that would be slow for users. Better to configure the firewall so that it blocks all outgoing traffic except the stuff you really need and that will help keep you below your 3G allowance.

Other than that I will give you a general overview of what you need.

1. Madwifi drivers - for the wireless card
2. Hostapd - is the access point bit (only compatible with prism and atheros chipsets)
3. Shorewall - This is your firewall/router bit.
4. Time to get it right! - I am talking as a Gentoo user so, the devil will be in the details which are different between the OS's like init scripts and stuff.

If you want to know more ask specific questions and I will help you as best I can. I can talk from experience as my I have setup my laptop in this way.

---

