---
title: "Setting up laptop to use wireless at College"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by mcar2185 on 2007-09-25
I go to a public university and just installed Ubuntu on my laptop as my OS. I'm wanting to set up the laptop so that I can browse the internet using my university's wireless. In order to use their wireless connection, I need to use network settings without data encryption and Firefox must auto detect proxy settings. I figured out the Firefox part of it, but don't know how to set up a connection without data encryption. How do I do this?

---

### Post by pluviosity on 2007-09-25
Do you have roaming mode enabled?  That made life a lot easier for me at my college.

---

### Post by Lord Illidan on 2007-09-25
Does your university have any public howtos? If so we can see what you need to change.

Basically, it's all about roaming mode.

---

### Post by mcar2185 on 2007-09-25
[http://www.umflint.edu/its/helpdesk/quicknotes/QN65.htm](http://www.umflint.edu/its/helpdesk/quicknotes/QN65.htm)

I had to disable Roaming because it causes my wireless light to go off (I use a Compaq v6000 series laptop).

---

### Post by mcar2185 on 2007-09-26
Anyway to get College Wireless to work on a laptop that doesn't allow roaming?

---

### Post by Lord Illidan on 2007-09-26
Ok, so no roaming.

Did you register your MAC address?

If so, it should be a piece of cake if Ubuntu supports your wifi card.

If you are using NetworkManager, then just double click on the icon in the notification area, select Connect to other Wireless network, and then enter **80211net**.for network name, and leave wireless security to none.

Then, open firefox, click Edit, Preferences, Advanced, Network, Connection Settings, and enter this link [http://cache.umflint.edu/cache.pac](http://cache.umflint.edu/cache.pac) in the Automatic Proxy Configuration Url.

This might prove helpful : [http://www.umflint.edu/its/helpdesk/quicknotes/QN15.htm](http://www.umflint.edu/its/helpdesk/quicknotes/QN15.htm)

---

### Post by mcar2185 on 2007-09-26
Yeah, I've been using this laptop for wireless at college using Vista, so the MAC is registered.

My wifi card appears to be supported, as I installed a package allowing the card to work.

I'll try what you suggested when I go back to college in a few minutes. Hopefully it works. Thanks.

---

### Post by wirelessmonkey on 2007-09-26
After you get your wireless working, send them an email to let them know how much you enjoy your traffic being insecure. Mac Auth Bypass is not useful for wireless networks.  

Sorry, had to rant for some reason.

Best of luck.

---

### Post by Lord Illidan on 2007-09-27
Did this work?

---

### Post by mcar2185 on 2007-10-05
Yup, got it working. Thanks.

---

### Post by natedogg624 on 2008-02-20
[SOLVED]

bringing this back...

just installed ubuntu OS and so far it is pretty sweet.  only thing is that i am trying to set wireless up.  

here is the HOWTO from my college:
[http://8help.osu.edu/2672.html#example](http://8help.osu.edu/2672.html#example)

it says that they don't support linux, but unless it has open source client then it should work.

i can see my wireless when i look at the wireless networks in my area, i just don't know what to input to set it up.

---

