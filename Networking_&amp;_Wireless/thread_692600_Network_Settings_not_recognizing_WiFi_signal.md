---
title: "Network Settings not recognizing WiFi signal"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by vootpig on 2008-02-09
Hi,

Running Feisty; I have a WiFi network broadcast throughout my home, and although other devices capable of WiFi interaction recognize the signal in the area where my computer is, my computer itself will not pick up on the network.

The network is completely open, not restricted / hidden / whatever.

My computer has a Realtek 8201CL PHY network chip, but when I go to "Network Settings" on the box it shows only options for a wired / modem connection. The wireless signal is not getting picked up.

Can someone tell me what's wrong and how to fix it?

---

### Post by Bubba64 on 2008-02-10
Is the computer able to run with a ethernet plug in and if you click on DNS in the network does it show the DNS server and domain. I am assuming this chip which I couldn't find any info on when I googled it is a wireless setup.

---

### Post by evymetal on 2008-02-10
If there is no wireless device showing then it's probably because your computer isn't recognising your wireless adapter, rather than because the signal isn't getting there.

To check this is the case, can you post the output from running "ifconfig" in the terminal.


Not (personally) sure how to fix these problems on Ubuntu (I'm in the middle of the same problem after a kernel update) - but problems like this on Linux/BSD are generally due to the fact the wireless card manufacturers don't release drivers for these operating systems - so the developers have to try and guess how to make them work.

Hopefully some friendly forum member should have some experience setting up your network card if this is what the problem is.

---

### Post by FrankVdb on 2008-02-10
If your wireless card is not supported under Linux, there is a chance that you can use its  Windows driver by wrapping it with ndiswrapper. Check your configuration first. Using a Windows driver under Linux is only a last-resort solution.

---

