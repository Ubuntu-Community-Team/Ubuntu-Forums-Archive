---
title: "Networks visible but cannot connect"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by Racecar on 2010-06-16
Howdy, all. I recently found a Dell Inspiron E1405 and reformatted with Lucid. The wifi card is an Intel  PRO/Wireless 3945ABG, and I'm getting really strange behavior from it. Before I installed Lucid (when it still ran windows), I tried to connect to my network (which was visible) but couldn't get an IP address. Then I reformatted, and I'm getting the same thing. It sees available networks, but won't connect. I read in a similar thread that this could be a Network Manager issue, so I changed over to Wicd, but no  improvement. It always fails at 'Obtaining IP Address...'

Of course, ndiswrapper comes up a lot on wifi trouble threads, but I haven't tried it for two reasons. 1) The problem is clearly not  with my driver, because I can detect networks - right? 2)  whatever the problem is, it seems to have *persisted* from windows to ubuntu. (What the hell...?!) So what am I dealing with, folks? Is this some bizarre hardware issue? For what it's worth, the ethernet cable connection works fine. Any thoughts, anyone?

Thanks and apologies if this is addressed elsewhere!

---

### Post by Zip247 on 2010-06-16
Have you checked the router, it could be set to accept only a limited number of wireless connections which has been met.  

Just a thought.

---

### Post by anewguy on 2010-06-16
Encryption on the router?  MAC filtering?

Dave ;)

---

### Post by Racecar on 2010-06-16
Thanks for the quick replies, you two. I have no connection limit on this router, so I think that's ruled out. A lot of different people come through this location and connect to the (WPA protected) network without any difficulties, so I wouldn't think that's the problem. But maybe it has something to do with the age of this unit? I'll check MAC filtering if I can figure out what that is. Any other suggestions?

---

### Post by anewguy on 2010-06-16
MAC filtering is specified on the router in the way of a table of MAC (machine-specific) addresses of the computers allowed to access the wireless network.

What exactly are you doing when you try to connect?  Since this is a WPA protected network, are you specifying the key and type correctly?  Is the router broadcasting the network id (ESSID) or is it a "hidden" network (connecting to which is slightly different)?

Dave ;)

---

### Post by Racecar on 2010-06-16
The network id is visible, not hidden. I'm trying to connect by the usual procedure - select the correct network in the wicd array, enter the password in the prompted field. Wicd detects the type of encryption automatically, so I haven't messed with those settings.

---

### Post by Easy Limits on 2010-06-16
You might try changing the broadcast channel of the router.

---

### Post by linfidel on 2010-06-16
I doubt that it's the age of the unit, and the card should work without special drivers.  I have an old Inspiron 8500 which I think is older, and it works perfectly with a similar Intel card that replaced the crappy Broadcom card it came with.

One thing that hasn't been mentioned is whether the wireless is enabled on the laptop itself - there's usually a special function key that enables it.  That got me at one point, and there's no real way to know if it's enabled, I don't think, unless you can check the BIOS (which you should also do).

---

