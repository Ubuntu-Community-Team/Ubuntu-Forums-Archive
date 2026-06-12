---
title: "wireless upgrade/wep key help"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by summersource on 2010-02-21
After a recent upgrade I gave my Dad my Gateway ML6230 and a Linksys wireless router Model WAP11  ver 2.6  2.4 GHz  802.11b, I had not used that particular router in a few years. I sent him a link to upgrade the firmware but I was wondering if there were any drivers that we needed to install within the wireless card of the Gateway to support this upgrade? Of course Gateway support was not much help when it came to Linux. He is running Ubuntu 10.9 32 bit.
Also I have no idea where the WEP key is to that router how to I reset to create a new network?

---

### Post by 2hot6ft2 on 2010-02-21
To reset the router.
A hard reset 30/30/30.

The 30/30/30 hard reset means with the router plugged in push and hold the reset button for 30 seconds.
While still holding the reset button in, unplug the routers power and continue holding the reset button for 30 seconds.
Still holding the button in plug the power back in and continue holding the reset button for 30 seconds.

So you have to hold the button in for at least 90 seconds while power is on/off/on

Release the button and let the router warm up for a minute.

That clears the routers configuration completely and it's like brand new and you have to set it up all over again to your configuration.

The IP for it is 192.168.1.1

I think the default login for linksys router is:
admin = admin
password = admin

But I'm not positive without searching. I'm sure someone will chime in.

And no a router firmware upgrade does not require anything new to be done with the computer connecting to it other than setting it up for the new passkey for the network you set up.

---

### Post by 2hot6ft2 on 2010-02-21
From here: [http://compnetworking.about.com/od/routers/qt/linksys_passwds.htm](http://compnetworking.about.com/od/routers/qt/linksys_passwds.htm)

>  The default login information for Linksys routers depends on the model as shown below.

Default user names:

    * Linksys BEFW11S4, WRT54G: admin
    * Linksys EtherFast Cable/DSL Ethernet routers: Administrator
    * Linksys Comcast routers: comcast
    * All other Linksys routers: [none] 

Default passwords:

    * Linksys BEFW11S4: [none]
    * Linksys Comcast routers: 1234
    * All other Linksys routers: admin 

Where the word [none] is listed above, no name or password is required. Simply skip or press the Enter/Return key when prompted for those settings.

---

### Post by summersource on 2010-02-21
thank you so much 2hot6ft2

---

### Post by 2hot6ft2 on 2010-02-21
> **summersource said:**
> thank you so much 2hot6ft2
You're welcome. Glad to help.

---

