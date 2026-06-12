---
title: "Another Wireless problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by Trekrider58 on 2008-07-10
Having decided to try out Linux I installed Ubuntu 8.04.1 under WUBI today. I followed the instructions on how to load my WG111T wireless device using ndisgtk - all went well until step 6 (plug back in USB drive and network-manager should do the rest) - nothing happened.

If I open 'Wireless Network Drivers' I can see the WG111T driver and underneath it says 'Hardware Present: No' although sometimes after I reboot it says 'Hardware Present: Yes'. If I open 'Network Settings' it only shows 'Wired connection' and 'point to point connection' no matter if it says Yes or No.

Looking at the help files it says to check for device recognition - 'Open Device manager (System > Preferences > Hardware Information)' - problem here is that there is no 'Hardware Information' under 'System > Preferences'. Where do I find this?

Any help on getting this to work would be great as it is such a pain having to keep rebooting just to find information and then try it. As you can probably guess the network is fine when I boot in XP.

---

### Post by Trekrider58 on 2008-07-10
As an addendum to this I have just run the command 'lshw -C network' and the result gives the Ethernet interface but no wireless interface.

I have tried uninstalling the driver and reinstalling it but get the same result.

---

### Post by Trekrider58 on 2008-07-11
Oh - well, I guess Linux isn't for me then:(

---

### Post by DanGent on 2009-11-11
you ever get anywhere with this?
i've got same problem. always used wireless cards on laptops, never tried ubuntu with a USB dongle before and so far its not so good!
same dongle, same problem....

---

### Post by dclark16 on 2009-11-11
I'm having a similar problem, except mines stranger. If I connect to my wireless downstairs it works fine, if i go upstairs it stays connect but the internet doesn't work, and eventually drops out altogether, the signal strength is at about 70%. If i try to connect upstairs (using wicd) it says "failed to connect, unable to obtain ip address". And its not limited to my wireless router, if i go to my mates house same issue. It seems that unless i have 100% wireless signal i cannot connect. I've googled it around but no one seems to be having the same problem, some people are just unable to connect full stop, but i can (when im downstairs, kinda defeats the object of wireless and a laptop if you have to be in one room), ive reinstalled 9.10 twice, Ive tried various wireless utilities and fixes and none of them seem to have any affect. I have spoken to my Linux tutor and he says he's never come across anything like it. i would really appreciate any help.
 
Im faily new to ubuntu, but if you can give me any help at all i will look into it and make sure i understand what im doing, i love ubuntu and i want to like it, its just not letting me XD

---

