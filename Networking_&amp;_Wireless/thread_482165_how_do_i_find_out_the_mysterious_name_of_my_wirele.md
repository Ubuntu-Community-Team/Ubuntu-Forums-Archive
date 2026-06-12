---
title: "how do i find out the mysterious name of my wireless card ?"
date: 2007-06-23
forum: Networking &amp; Wireless
---

### Post by pfabrikant on 2007-06-23
hey !
i bought a second hand laptop (hp pavilion ze 5300) with an internal wireless card. 
now, ubuntu does not recognize the wireless card. I know i have to find the proper driver for it but the problem is that I don't know the name of the wireless card..
how can I found out the name ? I don't have the paper manual, and nothing is written on the external parts of the computer...
help anyone ? 
thanks a lot !

---

### Post by dardack on 2007-06-23
if it's not supported by ubuntu by default, you'll probably need to  use ndiswrapper, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

section 2.5 lists i think how to find it, i think you need to run:

lspci  or   lshw  something like that (i'm kinda new to linux my self)

---

### Post by raul_ on 2007-06-23
"ifconfig" should list your network devices

---

### Post by dardack on 2007-06-23
If i'm not mistaken, ifconfig only works if Ubuntu recognizes your wireless card and has a driver for it (my belkin didn't, so when i ran ifconfig i only saw LO and ETH0 (my wired connection)), so you would i think have to run lshw or lspci to find out what it is.

---

### Post by niteshifter on 2007-06-23
Well...
Go to hp.com - enter pavilion ze 5300 in the search box.This gets a buch of results, on that list:
Click the link "Software and Driver Downloads HP Pavilion ze5300 Notebook"
Now we have a choice: for XP or 2000. Doesn't matter, really. Let's try XP ...

It's a Broadcom. Which one? I dunno ... open the laptop and see. It's a mini-PCI card.

They also have the Service Manual available as a pdf.

You're welcome :p

Not being sarcastic here - there are lot of vendors that don't publish squat about thier products and it's' easy to assume that such info just isn't available. HP is not one of those vendors.

---

### Post by CREEPING DEATH on 2007-06-23
Trying to identify the card?  Try
```
lspci
```
That ought to help.

CD

---

