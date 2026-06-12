---
title: "Atheros Wireless whats going on?"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by Willot on 2008-07-24
I have an acer laptop with the atheros ar2430 and it seems theres a few issues with it. Im using the madwifi drivers and for the most part there seem to work.

I don't know alot about Linux but I thought Id post a couple of observations i've made about the problem in hope this might lead someone with a bit more knowledge about it to have a eureka momment.

There are infact I think two problems.

1) the little switch on the laptop that manually turns on/off the wireless. The little light will be on using Linux drivers whether the wireless is on or not. If the laptop looses power for any reason(flat battery or whatever) the wireless will switch off but the light will still be on when you startup again. Leading you to think the wireless is on when its not. You know this has happened because the wireless Network option will disappear in network manager. (If you look in the error logs too you see an error that talks about the OS finding a driver for a wireless thing but NOT finding a wireless thing for it to hook up to IE the wireless adaptor is OFF). Try Unpowering your laptop. Then power it back on again and while the ubuntu screen is coming up to the desktop Flick the switch on the laptop. Hopefully the Wireless option will appear in network manager.

2) Once you get wireless neworking working The wireless connection appears connected but theres no action from any browses or routers or whatever. In my area there are a couple of other wireless networks besides mine although weak. If I connect to one of those (or try too I dont have the passwords) then unconnect and reconnect to MY wireless network. Everything Starts working. This must be some sort of Kernel error.

Now I could be completely wrong about this stuff. But these things seem to work for me.

I also think the wireless area is a MAIN area that needs ALOT of attention. Ubuntu (or any distro really)) will for the most part for average users find its home on laptops. Laptops are used for Web browsing, Email,word processing,spreedsheet stuff and other things on the go. Not much usually as gaming platforms. However a Major feature of notebooks/laptops today is WIRELESS, so if ubuntu cant work reliability with wireless it will never find a home there
despite the fact it does all the stuff people want on a laptop.
Even tho Vista Sux Balls. Im considing going back to it because 
A) when I turn on my notebook.....wireless works straight away.


Please I REALLY want to bugger MS Vista off my notebook!


:)

---

