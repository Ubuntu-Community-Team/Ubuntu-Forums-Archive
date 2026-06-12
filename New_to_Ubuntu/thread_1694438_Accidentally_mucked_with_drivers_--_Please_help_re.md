---
title: "Accidentally mucked with drivers -- Please help reset!"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by bladerunner060 on 2011-02-24
Okay, so I'm running a fully updated 10.10 on an Alienware M11x. Everything worked pretty much fine out of the box, though some of my function keys don't work and the wireless frequently does the constant-dropping thing that seem sot be a common issue on various models. It would generally let me get what I needed to get done done, though I might have to manually reconnect to get it to know it had disconnected itself. 

BUT THEN

I recently ran some updates and yesterday, my wireless card wouldn't see any networks. I knew for a fact that there were at least 2, so I tried to troubleshoot. I then installed some packages (it's a Broadcom card), some backports etc. I rebooted, and I went from Wireless as an option, just with no networks visible, to Network Manager not even showing Wireless as an option, only hardlines. 

It still sees the card in lspci (02:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
08:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01), it just doesn't exist as far as NM is concerned. 

I logged into my Windows partition, and it had the Wifi off, but the function keys work so I turned it on there, and it worked fine. I logged back into Ubuntu, and uninstalled the backports that I had installed (I couldn't remember the couple other packages I'd installed, because I am dumb.), and I've now rebooted several times with still no wireless. 

I'm officially stuck! Any help would be appreciated. 

And if there's some way to reinstall ubuntu, without messing with my Windows partition, that would be a good nuclear option, but I don't know how to do that. 
)

---

### Post by TBABill on 2011-02-24
```
sudo apt-get install --reinstall broadcom-kernel-source
``` Then go back to System>>Administration>>Additional Hardware and if the STA driver is activated, remove and reactivate if it is not working. Then restart. May get you going again.

---

### Post by bladerunner060 on 2011-02-25
Didn't work. I'm still wirelessless. Any other thoughts?

---

### Post by bladerunner060 on 2011-02-26
I fixed it!

The STA driver was the one that worked originally (apparently). After the suggestion above didn't work, I decided to try to run with STA as the proper driver (since it listed my model specifically, I figured it might have been the one that originally worked)...I rooted through my Synaptic, trying to disable anything I might have enabled, and found that I had apparently enabled backports. Disabling that, as well as disabling anything besides STA that had broadcom, bcm, or wireless in it (that wasn't obviously unrelated) seems to have fixed it! Woot! I'm really glad...because I really wasn't relishing the idea of a reinstall.

---

