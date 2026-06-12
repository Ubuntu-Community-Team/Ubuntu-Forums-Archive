---
title: "Need help with my wireless"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by bloodhacker2 on 2008-03-03
OK guys i have a acer aspire 3680 with ubuntu 7.10 on it but i need to know how to get the drivers for my wireless to work on this laptop.
i don't know what kinda driver it will take so i was thinking there got to be sum kind of command that will show me all my hardware and that will allow me to post it on hear. is there???

---

### Post by zxscooby on 2008-03-03
typing lspci in the terminal will list your devices.

---

### Post by sqlyee on 2008-03-03
I have an Acer 3680-2633 that came with an Atheros card. I too am running Gutsy Gibbon. I was never able to get wireless working on this machine. I tried all kinds of things, including many of the recommendations from this forum. I tried using the Gnome desktop as well as using the terminal with no success. I tried ndiswrappers with no success as well as MadWifi. Finally, I read about someone just using a PCMCIA wireless card. I decided to do the same thing. I checked to see what cards were giving the most success and decided on the D-Link DWL-G650. I found the card on ebay for something less than $15. As soon as I plugged it in my wireless was working, and has been working ever since. That was about 3 months ago. I haven't looked back since.

---

### Post by zxscooby on 2008-03-03
ive had alot of luck with atheros cards. the broadcoms are the tricky ones.

---

### Post by PreviousN on 2008-03-03
Indeed, atheros is more supported in linux than broadcom. Some of them, using madwifi you can do packet injection even. 

May I suggest this tool:
[http://wifix.sourceforge.net/download.html](http://wifix.sourceforge.net/download.html)

To get, first open a terminal:
sudo apt-get install subversion
mkdir wifix #this will make a directory in your home folder called wifix.
cd wifix
svn co [https://wifix.svn.sourceforge.net/svnroot/wifix/trunk/wifix](https://wifix.svn.sourceforge.net/svnroot/wifix/trunk/wifix) wifix
cd wifix
./wifix #this runs the program which comes precompiled/without need for compiling. 

It'll scan your hardware, and try to grab drivers for your card. If it doesn't work, it points you to ndiswrapper. If that happens, don't give up, just try something else.

---

