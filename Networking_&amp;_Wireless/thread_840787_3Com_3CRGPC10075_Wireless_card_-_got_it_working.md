---
title: "3Com 3CRGPC10075 Wireless card - got it working"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by JPaganel on 2008-06-25
I switched out my old 22Mbps SMC card in my backup laptop running Hardy Heron for a 3Com from my other laptop. 

The SMC was detected nicely and worked for a long time, but I got a bit tired of the speed limitation.

The 3Com card did not do anything at all when I first put it in. I did a bit of searching and found that there are no drivers for it and ndiswrapper is an option. 

I downloaded the 3Com drivers from here:
[http://webprd1.3com.com/swd/jsp/user/manual_download.jsp](http://webprd1.3com.com/swd/jsp/user/manual_download.jsp)

I got there from the main 3Com page. 

I used Archive Manager to extract the Driver folder. 

Then, I used Synaptic to install ndisgtk,ndiswrapper-common and ndiswrapper-utils-1.9

The graphical install of the 3Com driver worked perfectly.

I am now able to use graphical configuration for wireless networks, where I had to use command line for the SMC card. I didn't think that was a driver issue.

---

