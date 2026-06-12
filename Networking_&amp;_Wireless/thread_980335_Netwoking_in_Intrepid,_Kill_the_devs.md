---
title: "Netwoking in Intrepid, Kill the devs"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by NitroBooster on 2008-11-12
Man,

The devs are clearly holding out on why networking is all messed up in 8.10   I've tried to make networking work on 8.10 Desktop with static ip for 4 days now. I've read every freaking forum thread, tried every stupid little trick I could find, hell, I even hired the admins at my ISP, and between all that  - networking does not work properly. And if it does start to semi work for a second, it just stops working out of nowhere.

So I guess the questions is when is there going to be an update, a comprehensive workaround, or additional information released on how to set it up? Because in it's current state of disclosure the mechanisms for tuning it fail miserably. 

I'm talking about /etc/network/interfaces, freaking /etc/resolv.conf, and last but not least /etc/dhcp3/dhclient.conf

These files DO NOT DO THE TRICK!

How dare you call it a stable release. Did Microsoft buy this project?

---

### Post by enigmageek on 2008-11-13
Hello. It clearly states in the Changelog for Intrepid that they use the newest NetworkManager and it doesn't yet support static IP configuration. They should have it fixed soon. I always wait a few months to do a major upgrade to give it time to resolve issues. I will probably stay with Hardy until it is EOL'd because of the network manager issue, KDE 3.5.10 not being included, and a host of other things.Good luck and for the future, please read the Changelog carefully and watch the forums to see if showstopper bugs are being resolved.
Regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5

---

### Post by sirius56 on 2008-11-14
NitroBooster,

You said it succinctly.  I wasted a few days trying to fix the same bug.

I still can't seem to set up a Fixed connection to my router.  8.10 keeps on changing the manual connection back to DHCP.  None of the suggestions I've found in this forum worked.  

I too am surprised that such a major bug could have slipped through and is apparently not getting any attention.

Please let me know if you hear of any fixes that work.

---

