---
title: "What's best way to handle multi wireless AP situation?"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by bliffle on 2008-02-03
My Thinkpad T60 has been working almost flawlessly since I installed ubuntu 7.04 and then 7.10 6 months ago. Especially the wireless thru the builtin wireless adapter, whether connecting to my in-home Netgear AP or the AP at the coffee shop, or a casual AP at an airport or a friends house.

So, naturally, I couldn't leave well-enough alone and I got a FON AP and signed up for the service. FON is a scheme whereby you trade shared bandwidth on your DSL or cable highspeed internet connection for the opportunity to share someone elses highspeed connection when you are away from home. Good deal if you travel some and occasionally need a high speed connection in a foreign city. Granted, you can usually find a cafe or ride an acquaintances highspeed in most world metropolises, but sometimes one needs another alternative, and it's tantalizing to realize there's somebody in the neighborhood who has an AP but you can't use it because you don't know them.

So FON involves registering for access to your AP to gain access to other peoples AP. But it would probably be abused, so they require that you use their FONERA AP which has 2 APs within it: one for your private use and one to share. they are quite cheap and can be bought for $40 from FON or $30 on eBay..

So I bought a FONERA and registered with FON and it all seems to work. But I didn't immediately replace my old Netgear AP with the FONERA because I wanted a backup, So I plugged the RJ45 ethernet LAN cable from the FONERA into the LAN RJ45 in back of the netgear, figuring that the Netgear had an ethernet hub between the wireless AP and the DSL LAN RJ45 so that one could connect a hardwired LAN in with the AP>

And it all works. I now have 3 wireless APs available at home: my old Netgear, the new "FON_AP" which is the shared FON wireless, and "MyPlace" which is the half of the FON AP which is reserved for my personal use.

But I have a problem trying to make sure I connect on any one rather than the other two. I'd rather connect to the old Netgear for my personal use, at least until I don't need it anymore and can use the "MyPlace" AP with assurance.

But I have little control over the initial connection that ubuntu makes and I have great difficulty changing from, say, "FON_AP" to netgear.

Is there some way to control which wireless AP I connect to?

---

### Post by psyburn on 2008-02-03
I presume you don't want to connect to FON_AP anymore unless you explicitly say so.

Ubuntu will choose the strongest signal from known AP (access point you have already said to connect to previously)

The information about known access points is kept in your home folder at the following path:
~/.gconf/system/networking/wireless/networks

Find a folder named FON_AP and delete it.
Then logout and log back in and you should connect to either the Netgear or "MyPlace" automatically 

However if you use anything labeled FON_AP again you'll need to go back in and delete the folder everytime you connect to a FON_AP

---

### Post by bliffle on 2008-02-03
That did it!

Thanks a million. Merci beau coup!

---

