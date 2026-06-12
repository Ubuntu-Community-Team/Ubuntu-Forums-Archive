---
title: "Wireless Adapter"
date: 2005-04-10
forum: Networking &amp; Wireless
---

### Post by doans on 2005-04-10
I am having troubles with my Netgear wireless WG111 USB adapter on Hoary.  

First, it has never activated itself on bootup.  I have to manually activate the connection on every restart.  Second, the connection is really flakey.  As in the connection is great for 30minutes an hour and then nothing.  I have to unplug the adapter and plug back in.  The opposite of productive.

btw I have got the adapter working with the use of ndiswrapper.

My question is should I try a different .inf file from the windows cd?  As in, I have used the inf file from the WinXP directory on the CD.  Would the Win 98 or 2000 inf files be more compatible with ndiswrapper? Or would they be more stable?  If so how do I uninstall the current inf file from ndiswrapper?

Or is there anything else that I can try to resolve these issues?  Thanks.

---

### Post by electroglas on 2005-04-10
My Ma111 had no success just plugging it in. I had really hoped Ubuntu was further along in the wireless dept. Such a pity we can't get manufacturers to release code for good drivers.

I guess, I'll wait until I am ready to move computers and use the Sis900 ethernet.

---

### Post by philcolbourn on 2005-04-10
I have been using wg111 for a few months now on hoary. Just today I switched to an old zytel zyair b-220 as the driver works without a special kernel nod (2.6.10+).

I have moved the wg111 to an xp box.

Like everyone else (I guess) i also used ndiswrapper. I don't recall any problems once I got over the learning curve and understood what was going on.

To get ndiswrapper to boot, just add something like this to your /etc/network/interfaces file:

iface wlan0 inet dhcp
#this loads ndiswrapper which (i think) loads the firmware into the wg111
        pre-up modprobe ndiswrapper
#pull it out at the end of the day
        post-down rmmod ndiswrapper
        name wg111/zyair
#you should be using WEP at least. WPA is better and I should be using that!
        wireless_mode managed
        wireless_essid XXXXXXXX
        wireless_key XXXXXXXXXXXXXXXXXXXXXXXX
#my little experiment in optimising file transfers over PPPoA and ADSL
        mtu 1478

auto wlan0

(NB: I didn't have fxload installed so I don't think it was needed, but it can't hurt I suppose)

Now, my problem was that if i shutdown the pc, it would hang when trying to unload ndiswrapper. I just put up with it. If I remembered, i would unplug the wg111 when I got the text screen back and this would usually work ok. I then switched the pc off and reinserted the wg111 ready for the next day.

I think i used the xp drivers (v2.1) from memory off the netgear web site.

There are a number of versions of the wg111. mine is a wg111v2 with a serial number beguinig with wg72. According the netgear web site, it is actually a wg111v1!
the v2's start with WG41. I don't know, but it worked ok.

I did notice that massive high speed file uploads (eg. via scp) hung the pc, but that may not be the wg111 causing it.

---

