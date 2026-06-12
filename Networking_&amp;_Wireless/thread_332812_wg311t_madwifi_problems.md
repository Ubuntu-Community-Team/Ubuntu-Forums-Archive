---
title: "wg311t madwifi problems"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by chrismcr on 2007-01-06
Hi

I'm new to ubuntu, having previously used gentoo for quite a while. I'm trying to get a netgear wg311t card working with madwifi, having seen it recommended for linux in general.

The madwifi modules load fine, there is nothing untoward in dmesg at all, and I can scan for aps. Trouble is when I try to connect, iwconfig tells me I'm getting "nwid" errors. I don't get any other kind of errors from iwconfig, just this nwid value which goes up and up... the signal strength is also permanently stuck at around 25.

Its a dual-boot system; the wifi card works fine through windows.

I've tried manually installing the latest madwifi source (non-cvs) to no avail.

There seem to be quite a few people having various different problems with this card since upgrading to edgy.. anyone got any ideas?

Thanks,
Chris

---

### Post by chrismcr on 2007-01-06
I can't believe it.
I must need a holiday.

I've been hitting my head off this all day - I assumed no ping response from the router meant no connection.. of course it doesn't respond to pings. Its a good job ubuntu's automatic update popped up or I would have carried on like this for weeks ](*,) 

I'm still getting far too many nwid errors though, and my connection strength is still terrible. But at least it works!

---

