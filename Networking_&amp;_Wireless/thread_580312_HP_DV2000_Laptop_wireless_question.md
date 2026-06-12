---
title: "HP DV2000 Laptop wireless question"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by hauger on 2007-10-18
Okay, I had 7.04 installed and never did manage to get the wireless installed and running.  After all kinds of frustration, I reverted back to Vista since things there worked.  Anyways, here I am trying again with 7.10.  I was plenty surprised when I was prompted to install the restricted drivers and grab the firmware from the net.  

Well, it "worked".  By worked, I mean, when I physically turn on the wireless, it's "I'm working" light comes on, and it shows under the network interfaces as working.  Things are looking good.  The fly in the ointment though is that under Ubuntu, the wireless cannot see any wireless networks, although under vista there's about 7 visible, and at least one router located about 3 feet away.

Me thinks the wireless is not working as advertised.

Now, I'm really, really new to this and have no idea what my next step aught be.  Any help would be greatly appreciated.

Thanks,
Rob.

---

### Post by hauger on 2007-10-19
**bump**

---

### Post by hauger on 2007-10-21
No help available?  Is there more info I need to provide that could help with Diagnosing the problem?  I really could use the help, an Ubuntu laptop is kinda useless to me in a production environment if I can only get online via hardwire and have no wireless support.

Thanks.
Rob.

---

### Post by hauger on 2007-10-21
[SOLVED]:  Not that anyone's actually reading this, but I uninstalled and blacklisted the restricted drivers and then put in Ndiswrapper as per this HOWTO:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

I think too that the wireless controller originally installed was the cause of the horrible slowdowns my laptop would experience.

---

