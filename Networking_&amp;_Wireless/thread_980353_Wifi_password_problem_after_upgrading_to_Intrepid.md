---
title: "Wifi password problem after upgrading to Intrepid"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by zorblek on 2008-11-12
I am having difficulties connecting to my home wireless network since upgrading to Intrepid. When I try to connect, it asks for my password. In the field for the default password is what looks like a hex string, maybe a hash of some sort, much longer than my actual password. When I enter the correct password, it fails to connect, and asks me for my password again. The password shown in the field is that same hex string again. This keeps happening until I reset my router, after which I can connect until the next time I reboot or come back from standby. I only have the problem with my home network. However, I'm pretty sure this is a problem with Ubuntu and not my router, for a couple of reasons:

1) The timing: this problem first manifested itself immediately after the upgrade.
2) I dual-boot Windows XP, and I don't have any trouble connecting in Windows.

Someone in Absolute Beginner Talk suggested I try changing the security type (it was set to the default, WPA2), but after doing that it just didn't connect (it didn't change the password, though). It was set to WPA2 before I upgraded, and there was no problem then.

Any clue what might be causing this? I am at a loss...

Thanks!

---

### Post by Shwefty on 2008-11-12
Ah, I had this problem too.  I have a 10 digit passcode (as standard for AT&T 2WIRE networks).  What I had to do to get it to work was to right-click on the wireless network icon in the top right and go to Edit Connections...

I found the wireless connection I was trying to fix under the wireless tab, then I deleted it out, and started again fresh.  (wash, rinse, repeat - until it works).  

I just figured that whenever I was putting in my password, and it was coming back in some nasty hex, that Ubuntu kept trying to use my saved connection, so, I deleted it out and tried again.  Hope this helps!

---

