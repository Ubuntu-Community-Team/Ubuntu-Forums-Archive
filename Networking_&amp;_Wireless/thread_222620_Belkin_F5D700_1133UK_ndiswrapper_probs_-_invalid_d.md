---
title: "Belkin F5D700 1133UK ndiswrapper probs - invalid driver"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by ironfistchamp on 2006-07-25
Hey all

I am trying to get the Belkin F5D700 1133UK Wireless card to work on my bros machine. I just converted him and don't want to loose him now. Anyway I heard that the CD drivers work. I get them off. I have three files 

bcm43xx.cat 
bcmwl5.inf
bcmwl5.sys

I tried to install it with ndiswrapper 1.21. Invalid driver. Crap. So I try to remove it. Driver not installed. Double crap. How can I uninstall this driver. An interesting thing I found is that all the files are empty so I will need to copy them over again.

So yeah how can I remove them properly? Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-07-25
Ok got rid of the driver reinstalled and hardware was detected. Next problem is this. When I issue 


sudo iwlist eth1 scan

I get 

eth1      Interface doesn't support scanning : No such device

The interface does exist (enabled in networking) and it should support scanning as it is wireless. Can anyone help now?

Thanks

Ironfistchamp

EDIT: eth1 doesn't show up in network tools. Shouldn't wireless cards be called wlan0 or something like that?

---

