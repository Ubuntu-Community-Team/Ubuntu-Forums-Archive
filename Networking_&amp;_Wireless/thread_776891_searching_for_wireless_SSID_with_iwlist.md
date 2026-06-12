---
title: "searching for wireless SSID with iwlist"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by wildbillnj1975 on 2008-05-01
When I search for a wireless SSID with iwlist, sometimes it shows up and sometimes it doesn't.  Anybody know why that might be?

Here's the background:

I have a laptop running Dapper (6.06), which is used both at home and on the road.

At home, it is an NIS client, verifying logins and mounting home directories from a server (which I just upgraded to Hardy Heron).

On the road, I connect to whatever free wifi hotspot I can find.

Since the default startup uses NIS and ypbind, it's tricky to use it on the road, because you have to kill ypbind (or else everything is really slow because it's always trying to refer to the NIS master to check user IDs for things).

I figured out a way to make it automatically have it choose the home or roaming setup at boot time: search for wireless SSIDs, and if mine shows up, use the home config (NIS).  Otherwise, don't bother starting NIS.

The problem is, you can't just run iwlist once to scan for the SSID - the desired SSID shows up sometimes but not others (something like 60% of the time it works).  So, I call iwlist several times so that I don't get a false negative, but this delays the system startup quite a bit.

---

