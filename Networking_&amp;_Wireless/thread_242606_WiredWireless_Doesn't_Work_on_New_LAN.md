---
title: "Wired/Wireless Doesn't Work on New LAN"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by codesplice on 2006-08-23
Hey all,
I'm having trouble getting on my new LAN under Dapper.  I can access fine through Windows, and I believe I have everything set up properly on the Linux side of things.  This is the first network I've had trouble connecting to - it's worked fine in the past, both wired and wirelessly.

Computer is a Dell Inspiron 9300
Ethernet card: Broadcom 440x 10/100 Integrated Controller
Wifi: Intel(R) PRO/Wireless 2915ABG
Router: D-Link WBR-1310

As far as router config, we're running MAC address filtering - I've added both my cards to the table.  Also running WPA... on that note, I can't find anything to set up a WPA key under Linux - help there?  But even if I ignore the wifi card and try to connect via an ethernet connection directly to the router, I can't see anything - can't even ping the router or anything else on the net.

That's all I can think to say about the problem thus far... just ask if you need more info.

I'd really like to be able to get back on Linux!

Thanks,
John

---

### Post by codesplice on 2006-08-24
PS - I figured out the WPA thing - I'll be installing all the necessary bullshit for it this weekend when I go home from school.  Still doesn't solve why I can't connect via ethernet...

And when trying to connect via wifi, it'll show sending/receiving packets but a 0% signal strength. 

I'm stumped.

---

### Post by codesplice on 2006-08-27
Update:

Installed NetworkManager and got it to work with WPA, so that's taken care of.  NM is a pretty cool little tool!  I followed the HOWTO on how to make it stop bugging me for the keyring password all the time... and now it won't store any keys.  And still asks me for the password.  Anything else I should try?

Additionally, I have no problem connecting to the network here via ethernet cable - yet last week I was unable to connect to our new network by either wifi or ethernet means.  I'm hoping incorporating support for WPA fixed the wifi issue - any thoughts on the ethernet side of things?

Thanks,
John

---

