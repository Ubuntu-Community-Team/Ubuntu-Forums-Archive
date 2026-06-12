---
title: "Adding cable modem &amp; wireless router"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-02-26
Hi...quick question for anyone.


I have a fresh install of Ubuntu Edgy.


I want to add a Motorola Surfboard cable modem & Netgear WG614 wireless router.


Will Ubuntu auto-recognize the modem? 

After that, should I be able to log into the wireless router address, from a browser?

Thanks! 
:popcorn:

---

### Post by dmizer on 2007-02-27
your problems will not be the modem or router.  your problem will be if your wireless card will work or not.  if you know that your wireless card works, you have nothing to worry about.

however ... i strongly urge you NOT to do your router configuration from a wireless card.  this is a one time proceedure ... even if it's inconvenient, you're best bet is to use a direct connection to your router with an ethernet cable.

you will end up with this configuration:

surfboard -> router -> ubuntu

in the above layout, as long as your wireless card works, your surfboard modem and router will be invisible to ubuntu.  modems and routers are hardware with their own drivers and software.  they function separately and independantly of operating system.  so it doesn't matter if you plug in a linux computer, a windows computer, or a mac ... sun ... anything, it still performs the same function.

---

