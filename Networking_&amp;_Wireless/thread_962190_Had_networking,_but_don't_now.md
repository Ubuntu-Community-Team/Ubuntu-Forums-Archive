---
title: "Had networking, but don't now"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by GrayMagiker on 2008-10-29
I have a desktop with 7.10 on it.  Up until earlier this week it was doing great, and had no problems.  

Then I decided to install winXP on a separate partition.  I had the partition already set up from the Ubuntu install, but never got around to loading XP in it :)   

Anyway, after I installed Windows I tried to install the networking driver in windows, as it was not recognized by default.  This caused windows to be unbootable.  

This also caused Ubuntu to be unbootable.  I reinstalled grub and booted linux, and connected to the internet as well, before the incident with the windows drivers, so I know that wasn't the issue.  

When I removed the network cable and changed it for a new one, Ubuntu booted, but could not connect to the internet.  I know the cable is good, I tested it with the laptop I am posting this from.  

Now Ubuntu boots, but cannot connect to the internet.  I do not see the LAN interface in the Network Manager.  I cannot connect to the internet with either the 7.10 live CD or the 8.04 live CD.  

I know that it is unlikely that installing the windows driver broke the Ubuntu install, but the timing was just to convenient to ignore.  One minute Ubuntu boots and connects to the internet, install a Windows driver, and now Ubuntu can't connect to the internet.  

Most likely, the on board network card on the mother board is broken, right?  Perhaps just bad timing (the hardware broke at just the right time?)  

Thought I would post this to see what people's advice is.  I have attached the output of 'lspci' and 'lspci -n' run on the broken machine, if it helps.

---

### Post by bzachd on 2008-11-01
GrayMagiker,

Could you make your own loop back connector and test the functionality of that on-board eth?

Just an idea..

Zach

---

