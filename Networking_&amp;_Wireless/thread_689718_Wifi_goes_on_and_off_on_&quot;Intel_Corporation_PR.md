---
title: "Wifi goes on and off on &quot;Intel Corporation PRO/Wireless 3945ABG Network Connection&quot;"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by peleg on 2008-02-06
Hello buddies.

My wifi card ("Intel Corporation PRO/Wireless 3945ABG Network Connection") started to act weird in the last few days - it just turn on and off spontaneously, without "warning"... actually, while writing this post, it goes on and off at least 20 times (I'm not exaggerating).

I have DELL Inspiron 6400, brand new, with ubuntu 7.04. Everything went well until 2 days ago, when I didn't have access to WPA any more - so by the help of the #ubuntu channel, we have decided to switch to unsecured network, and now it works (and I'm ok with that).

Yesterday, it started to "make problems" - as I said, it just turns on and off (from 100% signal to "disconnected" and back again, all the time...) - and sometimes it doesn't, and it stays connected.
I have to say that this in NOT the AP, the rest of the computers works fine here.

I heard something about "heartbit" connection to routers... I couldn't find any real information about that. Do you know something about that?

Anyway, one more problem which MIGHT be related: during the fix that we've done 2 days ago, we couldn't make the ubuntu connect to the network automatically after reboot; after each reboot I do "iwconfig eth1" and find that my ESSID is "unassociated". I type:
```
sudo /etc/init.d/networking restart
```
...and everything is ok (except the "on and off" issue mentioned above...)

So: I can handle it, and I have even heard about a workaround that put this line in the restart processes somehow (which is not good, because it makes the restart much longer - it waits for a connection before starting the rest of the stuff, too early), but it is still annoying. It might be related - and might no - so I post it here anyway.

Thanks ahead,
Peleg.

---

### Post by harjp on 2008-06-30
Is anyone else having a problem with this network controller? I believe I am too.

Upon re-boot, my Intel Corporation PRO/Wireless 3945ABG Network Connection fails to re-establish itself.  On my machine, this device is mapped to wlan0.

If I do a iwconfig wlan0, I get a "device does not exist" message until I toggle the wireless radio switch on the front of the laptop.

Also, in Ubuntu, the little blue light that illuminates the wireless radio switch never comes on.

---

### Post by leandromartinez98 on 2008-07-01
I had a lot of problems with this card before switching to Wicd ([http://wicd.sourceforge.net](http://wicd.sourceforge.net)). With Wicd it worked fine for me, except that it does not connect automatically on boot. The light is never on, there are some workarounds for that, but I didn't follow them because this is really only ahestetic.

I cannot say that changing for wicd will work for all people, there are other threads concerning this card in the forum.

---

### Post by qlucy on 2008-07-02
Hi, buddies -

Same problems, Intel PRO/Wireless 2200BG. Maybe this will add some pieces to the puzzle...

1. Unsecured wireless networks work, but with WEP enabled everything works for awhile then the network manager will suddenly ask for the passphrase.  

It happens when the system's been idle for a few minutes, but not long enough to have automatically tried to standby or turn off the display.If I type the key in, it reconnects but is never assigned an IP address.

"lshw -C network" tells me
.....wireless=unassociated

Either toggling the switch then rebooting works, or using the sudo /etc/init.d/networking restart command, like you guys said. It's nice to know the command to fix it, but if anyone knows a workaround so we don't have to type it in all the time, that would rock!

There are a couple of other threads on this subject and the consensus seems to be that it's the result of a kernel update, either 22 or 24....so it makes sense that this would crop up right after an upgrade.

2. My signal also goes on and off randomly like peleg described. This computer dual boots with XP and the problem happens in XP, as well.  Tough to say if it's related, but I think I was experiencing this problem long before the other one.  peleg, does it tend to happen more if you are trying to download larger files or watch video content? This seems to be the case with mine.

The more searching I do, the more I find people experiencing the first problem.  Maybe if enough of us make noise they'll come up with a bug fix. =)

---

