---
title: "Need help 802.11n using Ubuntu"
date: 2006-08-03
forum: Networking &amp; Wireless
---

### Post by rcbikerider on 2006-08-03
](*,)If anyone is able to provide some assistance here it would be greatly appreciated.  I'm at the point of just yanking Ubuntu because I'm unable to connect using any of my hardware at home.  I've got a linksys 802.11n wireless card PCI card, I can't even get the card recognized.   Does anyone have any ideas?  Somewhere I can at least start looking for a solution - I'm still new to Ubuntu.

Thanks much,

---

### Post by cranemd on 2006-08-07
I am new to Ubuntu also but this worked for me.  I have d link dir 635 802.11n and wireless notebook adapter that works great.  This may work for you.

1.  Need to update repositories.  To do this go to [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) and follow the instructions to update the repositories.
2.  Go to synaptic package manager and download ndiswrapper,  ndisgtk, and gnome network manager.
3.  Use the disc that came with your wireless adapter and save the driver to your computer. Mine was called net5416.inf
4.  Next go to system -> administration -> windows wireless drivers and click on install new driver. find the driver you saved to your computer. 

This is all I did with a new install and it worked great.  Speeds of 300.  If you have already installed programs like wifi radar and others you may need to delete them first.

---

