---
title: "Newbie wireless question (wired and wireless at same time?)"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by timzak on 2008-02-20
I have an old Dell laptop that has a wired network connection that I use for internet access.  I also have a wireless PCMCIA adaptor that I never bothered installing because my home network is wired.  However, I'd like to install the wireless adaptor for an upcoming roadtrip and wondered if it was possible to do this and connect either through the wired or wireless adaptor depending on what connection is available to me.

The laptop is running Ubuntu Gutsy.

Thanks in advance.

---

### Post by benfindlay on 2008-02-20
Both should work ok!

You can install  the PCMCIA adaptor, and if there is no wireless network available, it simply won't do anything. Plugging in the wired connection will still work however. Conversely, if wireless is available, then use it, and just dont plug anything into the wired connection!

Hope this helps!

---

### Post by timzak on 2008-02-20
Thanks for the quick response.  I'll try installing the wireless adaptor and see what happens.  Should it be straightforward, or will I need to do some tinkering?  In other words, do I just plug the adaptor in, turn on Ubuntu and it automatically configures it?  Or am I hoping for too much?

---

### Post by benfindlay on 2008-02-20
Depending on how well supported the chipset on the card is, it may work straight away. So just plug in and turn on (keeping your fingers crossed!)

If it doesn't work, this is no biggy; ndiswrapper is a great tool for getting wifi to work, but getting that sorted requires some command line work, which is often daunting to people. I can talk you through that if it doesn't just work straight away!

So plug in and we shall see!

Hope this helps!

---

### Post by timzak on 2008-02-21
Well, it seems to work all by itself.  I just plugged the Dlink AirPlus G card into the laptop, booted up, and it shows in network manager a couple of nearby wireless networks in my neighborhood.  So I am assuming that it works okay, I just don't have a wireless network to connect to to try it out yet.  

Is there anything special I need to do security-wise if my own network is not wireless?  I will only use the wireless portion at, say, a Starbucks, McDonald's, or a hotel room (if wired is not offered).  Do I need to secure things in this situation if I don't have a wireless router of my own?  Sorry if these are basic questions, but this is my first experience with wireless anything.

Thanks again!

---

### Post by benfindlay on 2008-02-21
You should be fine. Although its probably a safe bet to simply not have it plugged in unless you are planning to use it to connect to wifi. A wired network requires physical access to a connection, either the router/switch or an ethernet lead for a person to get onto it, so you should have no real worries!

Hope this helps!

---

