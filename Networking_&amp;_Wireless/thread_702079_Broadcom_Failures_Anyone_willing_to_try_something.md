---
title: "Broadcom Failures? Anyone willing to try something?"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by Presto123 on 2008-02-19
Mainly, this is for the sake of sanity for all of you who have had headache after headache with this wireless driver and have resorted to fighting with Ndiswrapper, even on 7.10.

I initially had issues with it and could not get Ndiswrapper work correctly on 7.04, but with my new 7.10 install, I had no problems doing it via the Restricted Drivers Manager.

So, I have no idea what I did differently than all those that I have attempted to help with no success. What I do know is that I have three specific restricted modules that could be the missing bit.

What I need is a couple of people to go through a fresh install following these two things:

One person to install via my addition to the wiki located here: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29?highlight=%28WifiDocs%2FDevice%29)

One to install via the above wiki with the addition of installing "linux-restricted-modules-2.6.22-14-generic" in Synaptic prior to enabling the card.

I would be the sap to do this, but I have a lot of extra stuff that I would prefer to not lose.

Any takers? Winner gets an imaginary cookie. :)

The computer I am running it on is the Compaq Presario C571NR (C500 Series, of course) and an Intel Pentium dual-core processor. LSPCI for the card shows it as: ```
Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
```

---

