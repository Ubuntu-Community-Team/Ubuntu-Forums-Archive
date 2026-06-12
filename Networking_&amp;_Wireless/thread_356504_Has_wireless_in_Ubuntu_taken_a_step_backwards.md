---
title: "Has wireless in Ubuntu taken a step backwards?"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by boakes on 2007-02-08
When I was using Dapper Drake  I could install any wireless card without any problems.  Now all of a sudden I'm having to edit files and adding hexidecimal addresses and downloading unofficial drivers only to find that it doesn't compile.  I've been trying to install a Belkin f5d7050 in Edgy for about a week now, and no luck.  I've even tried it with ndiswrapper only to have it fail miserably.  Sometimes when I check the Network panel in gnome I have three different adapters no doubt that one is for the onboard wireless adapter and other the USB adapter, but then I have one called master, what is this?  Anyways, I just wanted to blow off steam and I wanted to voice my opinion to the Ubuntu gods, as it will most likely fall on deaf ears to begin with.

---

### Post by spd106 on 2007-02-08
I think it was kind of expected that Edgy was going to be very hit and miss for features. Though I hadn't expected the number of regressions that have been found. Most prominent is the broken ssid list in network-admin.

Most problems seem to have stemed from the rapid development time frame of Edgy. After Dapper was delayed two months, it was asking a lot for Edgy to have the same level of QC with only four months dev time. Especially as most packages were frozen almost as soon as they were imported.

I'd like to say feisty looks better for networking, but at the moment it's awful. Hopefully the network-admin/network manager issue will be sorted out before main [freeze]("https://wiki.ubuntu.com/FeistyReleaseSchedule"). Though since that's supposed to be today, it doesn't look likely. Maybe it'll get an exception.

I think a lot of people were expecting the new devicescape stack to have replaced softmac in the kernel by now. This should enhance wireless quite considerably, or so I'm lead to believe. Sadly it's still some way off yet, fingers crossed for feisty+1.


Sorry for sounding off so critically, the development team are doing a great job and deserve many thanks for all the effort they put in.

---

### Post by boakes on 2007-02-08
Guess I won't even bother messing with it then.  Sad to see this happen to a great OS.

---

