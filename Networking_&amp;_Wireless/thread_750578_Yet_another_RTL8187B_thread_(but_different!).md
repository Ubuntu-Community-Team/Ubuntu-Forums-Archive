---
title: "Yet another RTL8187B thread (but different!)"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by Shynd on 2008-04-09
Okay, I'm sure everyone here has had enough of this but I have yet another RTL8187B WiFi problem.  I've read nearly every post on every forum I could find and followed nearly every step out there.  I seem to have a very unique problem that is equally frustrating.

First, I have a [Gateway ML6232](http://support.gateway.com/s/Mobile/2007/Oasis/1015043R/1015043Rnv.shtml) notebook computer which has a USB Realtek WLAN adapter onboard.  Its device ID is 0BDA:8189.

When I had Linux Mint installed, I used the modified version of rtl8187b which can be found [here](http://www.datanorth.net/~cuervo/rtl8187b/).  It worked alright, but it had huge connectivity issues.  I'd only get 30% signal strength when sitting the laptop right next to the router and it went downhill from there.  I can't get the modified driver to compile under Ubuntu 8.04--something about a CFLAGS or EXTRA_FLAGS or something error (there were 2 total errors)--but I haven't really looked into it because the driver is such crap to begin with.

My main problem is as follows: using ndiswrapper (both the GUI version and command-line) I can get it to install and recognize my adapter (using the Win98 version of the RTL8187B driver available from realtek.com) and scan for wireless networks (my router shows up with 76% signal strength), but I cannot connect to any.  I've tried unsecured, WEP 64/128, WPA (which I doubted would work, anyway) and just about anything else I can think of.  I can't see why it will detect the networks but not connect.

Whenever I click to connect to a network from the wireless networks dropdown in the top-right, it asks me for the WEP key, I put it in, and then it does literally nothing but sit there at "Waiting for Network Key for the wireless network 'BKNet'..."  About 2-3 minutes later, it'll pop up asking for the key again.  I'll re-enter it, hit Connect, and nothing will happen.  Wired network works, wireless doesn't.


I've run **ndiswrapper -l** to make sure my device shows up, I've modprobed and all other kinds of stuff that I found in this forum and others, I just can't, for the life of me, get it to connect to the internet.  Like so many others have said, this is really the last thing keeping me from running Ubuntu on this laptop 100%.  Right now, I only use Ubuntu to watch movies on my laptop as I can't find WinXP sound drivers for my sound card.

I apologize for those of you rolling your eyes at ANOTHER RTL8187B post but I thank you for taking the time to at least read it and (hopefully) respond.  Any help is appreciated :)

-Shynd

---

