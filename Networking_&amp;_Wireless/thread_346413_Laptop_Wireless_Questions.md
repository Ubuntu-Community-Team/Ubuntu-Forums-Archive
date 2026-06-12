---
title: "Laptop Wireless Questions"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by ziadoz on 2007-01-25
I'm planning to dual boot Ubuntu and Windows XP on my Compaq Presario v5214 laptop. Setting up the dual boot isn't really an issue, I've done it a few times before. My main worry about installing it on my laptop is the wireless networking aspect. My home wireless network is WPA so I'd really need to be able to get this working if possible. I would also like to be able to scan for hotspots if possible (for university and stuff). 

I wondered if anyone had any experiences with this particular laptop, or any advice in general as to how I could achieve both of my goals. There is some documentation on the hardware of my laptop here:

[http://h20195.www2.hp.com/V2/default.aspx?status=obsolete&segment=ho&country=uk&lang=en&pn=Mobile%20Products/Compaq%20Presario%20V5200%20Notebook%20PC%20series/RE308EA#ABU]("http://h20195.www2.hp.com/V2/default.aspx?status=obsolete&segment=ho&country=uk&lang=en&pn=Mobile%20Products/Compaq%20Presario%20V5200%20Notebook%20PC%20series/RE308EA#ABU")

Cheers for any help. :)

---

### Post by rmartz on 2007-01-25
I am running both on my v2000 and it works fine. I had a BCM4318 wireless card, so I had to do a little work to get it up and running. Then I installed wifi-radar and it detects hot spots and allows me to enter WEP or WPA stuff as needed. 

I even use it to connect wirelessly to my wife's desktop and steal internet access from her WinXP dialup connection since she hogs the line and ignores my whining.

Hope you have fun getting it going.

Peace.

---

### Post by Zinnin on 2007-01-25
I am running a v5000, and I am having problems with the button for wifi, the v2000 has the same wifi button, how did you get it to turn on?

---

### Post by rmartz on 2007-01-26
You will need to run scanmodem and find out which netowrk adapter you have. There are a couple of posts that contain the instructions to do this. You can use the search feature and find the info. If it was like mine, I have the BCM4318 adapter. I had to install the ndiswrapper which is a tool that allows you to use the windows based drivers for the adapter.

Once you find out which adapter you have, you can do a search and find instructions as to how to set it up.

Hope that helps and I will watch to see if you need any more help.

Peace.

---

### Post by rmartz on 2007-01-27
I gave you some incorrect info. You don't need to use scanmodem. That is to ID a modem. Got a little mixed up late at night. Sorry. Here is the correct info:

You can identify your wireless card with:

sudo lspci -vv

entered in a terminal window.

It will give you a lot of info. You can scan through and find the type of wireless network adapter, then search the forums for instructions as to how to install the correct drivers.

---

