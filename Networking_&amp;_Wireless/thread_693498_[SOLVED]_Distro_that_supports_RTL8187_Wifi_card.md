---
title: "[SOLVED] Distro that supports RTL8187 Wifi card?"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by bunnyfly on 2008-02-11
Hello! If you can help me, I will be the happiest girl alive!

So I've searched high and low, but cannot figure this out.
I have a Realtek RTL8187 wifi card (it's an internal USB wifi to the ASUS P5k MB) and it does not work with Ubuntu.

I have tried about 20 different things suggested in posts: messing with kernel modules, dmesg, blacklisting drivers, disabling IPv6.
I installed WICD (tried ndis, wext, everything), madwifi, ndiswrapper (with a few different inf files from Realtek themselves and other sites). I even downloaded the Linux driver source code from Realtek and installed that. Didn't work.

From the beginning, I could see my wifi card and it would detect my connection. But would either take a minute thinking before not connecting, or some configurations it would claim it was connected, but there would be no actual data going through.

The closest I've gotten is, with WICD (using only wext), I can get a connection. It works, and sometimes it works fast - however, after a random amount of time (30 seconds to 30 minutes) it will just cut out. Sometimes it will be disconnected, sometimes it will still show it's connected, network traffic goes outbound, but nothing is detected coming in. At that point, I can't reset the connection without rebooting. Reseting WICD, refreshing, etc doesn't seem to work, it just ignores me or WICD freezes and won't reload after killing it for some reason.

I just tried installing Linux Mint and Opensuse...Mint does out of the box what I've achieved after a week of work on Ubuntu above - connection, but it drops after a bit, and I have to reboot for internet. I couldn't get Opensuse to even detect my card.

And yes - on Windows XP, the wifi works splendidly. I can download at 500kb while uploading at 30kb and surf the net all at once without a lag.

SO - my question is: is there a distro well known for its wifi capabilities? Or does somebody know the SUPER SECRET that isn't posted elsewhere? I want SO badly to get (back) off of Windows, but ever since building my new computer, I'm stuck with it because I can't get Linux to get a usable connection.

THANKS SO MUCH!
[bunnyfly]

---

### Post by KCPokes on 2008-02-11
Strange that it does not work, out of the box, for you.  I have a Gateway laptop with the RTL8187 and it works by default on both Ubuntu and Mint.  Key thing is working; I didn't say working well.  The biggest issue with the default driver is that it crashes all the time.  I've found that blacklisting the rtl8187 driver and installing ndiswrapper with Windows 98 drivers, for that card, works the best.  Your mileage may vary, of course.

---

### Post by hahahan on 2008-02-11
Bunnyfly,

I use a usb rtl8187 adapter with Gutsy Gibbon succesfull.
The latest driver from realtec is known to be buggy (linux_26.1025.0328.20007) but the
rtl8187_linux_26.1010.0622.2006 works fine.
You can get it here:[http://aircrack-ng.org/doku.php?id=r8187](http://aircrack-ng.org/doku.php?id=r8187) with instructions.

Good luck.

---

### Post by sfleite on 2008-02-12
Hi hahahan,
I update my drivers, and all my problems gone. I haven't no more freezes on my wireless connection.
Thank you very much.

Saulo Leite.
:guitar:

But I have one problem. I have a connection only if a encryption is a WEP, not function with WPA/WPA2. :(

---

### Post by bunnyfly on 2008-02-20
Hmmm - for another unrelated reason (that was my fault) I had to reinstall Ubuntu this week. Again, the wifi didn't work at all...however after installing WICD it worked sporadically, constantly cutting out and requiring a total reboot to reconnect...so I was about to downgrade the drivers like you suggested Hahahan, but then I had a weird idea and changed my router from WPA to WPA2 without changing any of my WICD settings. And now it's a constant, fast connection! Weird. Maybe Ubuntu/WICD/a driver doesn't check which WPA version is being used? Hmm...

Thanks for your help though - if this somewhy gives out in the future, I'll try the driver you suggested Hahahan - I'm bookmarking the link you gave! Thanks,
[bunnyfly]

---

