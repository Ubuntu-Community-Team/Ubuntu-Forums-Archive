---
title: "Ubuntu (Feisty) Dropping Wireless Connection"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by AhrenBa on 2007-07-09
Hello,

I am running Ubuntu 7.04 (Feisty Fawn) with all the updates. I am using a Linksys WUSB54g wireless adapter.

I have inputted all my credentials into the administration - network boxes and the connection will begin to work fine. However, the connection will randomly just drop, and I won't be able to access the internet or my network.

The problem is fixed everytime by going back to administration - network and unchecking and then rechecking the connection box. 

Why is it doing this, and is there a solution for this? Thanks.

---

### Post by 1212jtraceur on 2007-07-10
I'm having this problem too, but with an Intel Pro Wireless 3945 card.

---

### Post by oooooops on 2007-07-10
I've seen several people with this same isuse (including myself).  I dumped network manager and use the command line to manage my connection at this point.  I still get random drops but then I'm starting to think I have a wireless router issue as my work XP  box is doing the same thing.  

The network card for the linux box is Atheros Ar5212 using ndiswrapper

---

### Post by AhrenBa on 2007-07-10
> **oooooops said:**
> I've seen several people with this same isuse (including myself).  I dumped network manager and use the command line to manage my connection at this point.  I still get random drops but then I'm starting to think I have a wireless router issue as my work XP  box is doing the same thing.  

The network card for the linux box is Atheros Ar5212 using ndiswrapper

Did you actually uninstall the Network Manager? If so, how do you go about doing this?

Do you think NDISwrapper would work any better for managing a connection? When you said you use the command line, how do you manage a connection with that?

Sorry for all the questions. ;)

---

### Post by fredj on 2007-07-10
You only use ndiswrapper and modprobe to switch to windows XP drivers. The driver that you already have
seems to be working. The problem with the dropped connection seems to be caused by a combination of
the wireless card, the router and possibly network manager.
I have noticed in windows XP that my wireless card disconnects sometimes but XP usually reconnects it
within a few seconds.

If you are going to configure you wireless card though the command line or even through a script that runs
at boot up the first thing you need to consider is what sort of security is your wireless network using. Is it
using WEP or WPA. Do you use DHCP to get a network address.

You don't need to uninstall network manager.

---

### Post by gerkin on 2007-07-16
Hi, check out my post here it might help:

 [http://ubuntuforums.org/showthread.php?p=3030748#post3030748](http://ubuntuforums.org/showthread.php?p=3030748#post3030748)

---

