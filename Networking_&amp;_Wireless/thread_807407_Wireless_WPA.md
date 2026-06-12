---
title: "Wireless WPA"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by ckippi on 2008-05-25
Hey

I have just installed Ubuntu 8.04. It has picked up the wireless card etc. When I select the wireless network it is asking for a WEP password, the thing is the wireless is locked down with WPA Personal.

If I try and hard set the settings it dosn't work either, just seems to slow the whole machine down.

Is there any updates that fix this? Is there away to download the updates to cd as I only have wireless access. Or is there another fix?

Many Thanks

Chris

---

### Post by regdabs on 2008-05-26
I had the same problem and what I did was go into network and change the request from WEP to WPA then entered the WPA password and it worked.  The only problem now is I have to re-enter the password every time I log off and back on again. The password is showing as being there but won't work until I delete it and then re-enter  Still working on that but at least I can use my wireless now.

---

### Post by myonta on 2008-05-26
I have a similar problem which I just posted about here: [http://ubuntuforums.org/showthread.php?t=807968]("http://ubuntuforums.org/showthread.php?t=807968")

~Jon

---

### Post by ckippi on 2008-05-26
Hey,

Thanks for the replies, I have tired setting in network but with no luck, sometimes it looks like it has connected but with no luck.

The wired thing is how it seems to hang the whole os when I enable the wireless and it seems to of connected.

I have read that you can install the windows drivers but without a internet connection this could prove a bit hard unless there are ways to install it from a cd.

Many Thanks

---

### Post by myonta on 2008-05-26
Do you know what chipsets you're running? I tend to have the most luck with Atheros and absolutely no luck with Broadcom or Realtek based.

I half wonder if the problem IS gnome-network-manager. I haven't tried it yet, but there is a how-to for setting up WEP/WPA unencrypted from the terminal: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Let me know if you figure something out,
~Jon

---

### Post by ckippi on 2008-05-26
What is the best way to check what chipset the card is using?

I know its a d-link card.

Many Thanks

---

### Post by myonta on 2008-05-26
***lspci*** seems to do the trick for me. Mine's a TRENDnet card and it comes up like this: ```
01:08.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

```I bought this card in particular because it's what [System76]("http://system76.com/") uses for their pre-built Ubuntu boxes.

Another way is to physically check the card itself for a chip maker and model. The way that was recommended to me, though, was to find out model number and exact revision (ie: rev 4.0C) and then google it. You need the revision because a lot of manufacturers change the chipset multiple times during the production of a single model (some companies even change them within a particular revision, but those tend to be the dollar-store variety).

Other than that, I don't know much about it. There's a response on the thread I started with links to a whole bunch of Wifi troubleshooting and howto docs ([here]("http://ubuntuforums.org/showthread.php?t=807968")).

~Jon

---

### Post by myonta on 2008-05-26
You can also try
[INDENT]***lshw -C network***[/INDENT]

---

### Post by ckippi on 2008-05-26
Ok, think I have tired everything !!! spent many hours on in, even tired using the windows drivers, going to run a network cable at some point. 

Not worth spending anymore time or money on it.

Thanks for all your help. Oh the card is using ACX 111 driver.

Many Thanks

---

