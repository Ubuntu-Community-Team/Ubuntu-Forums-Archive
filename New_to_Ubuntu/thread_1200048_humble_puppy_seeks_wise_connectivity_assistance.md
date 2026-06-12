---
title: "humble puppy seeks wise connectivity assistance"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by Albertint on 2009-06-29
Hi, I am a Ubuntu user, though recently I've been fiddling around with live USB distros. Most of them (Linux Mint, Knoppix, etc) work fine with the internet, Though Puppy Linux, no matter how many times I try, cannot browse the internet.

I'm using an inspiron 1525, with vista so I can't use the ndis drivers without knowing what my systems router is, and I even have eth0 showing in the menu, though even when it says it's functional (either when I enter the IP address or DHCP), it always says the connection failed on Seamonkey. What is the solution to this problem, I'm already pulling my hairs out of my head. :mad:

Oh, and the current router is a Netopia Cayman 3346, though I'm moving between houses (it's a laptop), so maybe a helpful solution you guys give me will hit two birds with one stone.

(on a side note, a similar problem occurs with DSL (Damn Small Linux), though through virtual PC I've successfully been on the internet before with DSL. Though it mostly had to do with the virtual PC being an all-in-one package that gave an instant gateway to features that otherwise would have required manual labor on a real system)

Oh, and I just remembered, in the connect options list, it says that eth0 is detected as a network interface, though no modem can be detected.

---

### Post by shel-hall on 2009-06-29
With the Puppy Linux liveCD, you have to explicitly connect (using the connect icon on the desktop), then test the connection (using the test button on the connect application), then get an address (using the DHCP button in the connect application).  It doesn't connect automatically, and, unless you save the connection settings, you have to do this each time you fire up the Pup.

-Shel

---

### Post by Albertint on 2009-06-29
When I said I tried everything, **I meant it**. Literally, I tried what you said, and no dice. It's a Live USB distro, by the way.

---

### Post by LewRockwell on 2009-06-29
shel-hall described what I was going to relate to start with

after you've selected "connect" and you've selected "internet by network or wireless LAN" then you should be at the "Interfaces" area

in that area it will list the interfaces it has discovered

here, on one of my machines I have "ath0" which is my PCMCIA wireless card with Atheros guts

I also have "eth0" which is the internal ethernet controller/interface

If you only show "eth0" in your interface area then Puppy is not recognizing your wireless

---

### Post by LewRockwell on 2009-06-29
which version of Puppy did you say you were using again?

I found this:

"puppy-4.1.2-k2.6.25.16-seamonkey (official release puppy) have recognized the NIC without problem. Foolishly, I got the Dell wireless 1395 and that has only loaded on the official 4.12 puppy and not on the lxde-pup."

so it seems that 4.1.2 may have worked for that particular person

---

### Post by LewRockwell on 2009-06-29
looks like your machine may have one of these Dell 1395 units:

[http://accessories.us.dell.com/sna/products/Wireless_WiFi/productdetail.aspx?c=us&l=en&s=biz&cs=555&sku=430-2801](http://accessories.us.dell.com/sna/products/Wireless_WiFi/productdetail.aspx?c=us&l=en&s=biz&cs=555&sku=430-2801)

and the technical specifications say it's only designed for XP/Vista

here's a thread on ubuntu troubles with that device:

[http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088)

.

---

### Post by sneeks on 2009-06-29
you may be better off with one of the puppy off-shoots,im sure simplicity linux has support for your card and a few others,also try macpup,there are also pet files for wireless devices if you do have probs.or if you think you may have done something wrong along the way have a look at one of my videos,they are also on youtube now but make sure you watch in HD .
[http://www.youtube.com/watch?v=ICGJIa0o1mA](http://www.youtube.com/watch?v=ICGJIa0o1mA)

---

