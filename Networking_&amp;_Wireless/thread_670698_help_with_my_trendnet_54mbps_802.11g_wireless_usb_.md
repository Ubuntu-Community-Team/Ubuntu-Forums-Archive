---
title: "help with my trendnet 54mbps 802.11g wireless usb 2.0 adapter  3.1"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by darkmdbeener on 2008-01-17
i know theres alot  just like this one but none helped me.. i ended about near killing the computer which would of been bad because its not mine and im broke. right now im reinstalling it... but after i would like to know how to get that thing to work thanks. and its realtek not the sis chipset.
thanks 
beener

Edit:

should also say im running kubuntu

thanks

---

### Post by darkmdbeener on 2008-01-18
i hate bumping but i need this fixed.sorry

---

### Post by darkmdbeener on 2008-01-19
used ndiswrapper with the RTL8187B driver at [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)
then used 

sudo modprobe ndiswrapper 

and no wlan0 came up 

so did
sudo modprobe -r ndiswrapper 
sudo modprobe ndiswrapper

and everything fixed.

---

