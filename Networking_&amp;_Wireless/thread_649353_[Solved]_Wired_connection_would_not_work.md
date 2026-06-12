---
title: "[Solved] Wired connection would not work"
date: 2007-12-24
forum: Networking &amp; Wireless
---

### Post by Shimfs on 2007-12-24
Hi Guys.
For the past 2 days, i have been sitting and tried to get my WIRED connection to work, something that should work out of the box.

I know that this wont solve the issues that everyone has (for those with wired connection that cant get it to work)

First of all, i tried all those blacklisting of the IPv6 things that some threads mentioned, and i were talking with some smart guys at the IRC channel, but neither would work, and for a complete linux user this posed some serious doubts about linux in me.

Well i finally found out that my router had a limited set of users that could use DHCP. (I could change the amount so that was no problem)
Well i could still noget get my wired connection to work, even tough i had allocated an extra slot in my router.

Then i used the Gentoo (i know im using ubuntu atm) minimal live CD, and inserted it. And i could configure my network, and after a few hours i found a way that would work. GREAT, now i just had to do the same in Ubuntu.

However, I encountered the problem that I could not access the router even though I used the right information.

For me, that was
IP address: 192.168.1.6 (note the 6, that was the free DHCP slot i made)
subnet: 255.255.255.0
Gateway: 192.168.1.1 (default for meny)

at this point however i had used the apt-get remove network-manager command and installed Wicd.

it would still not work. but i installed Wicd to get some more options (just read about it somewhere)

i used the same things, and found the DNS thing, and typed
DNS: 192.168.1.1 as i should in Gentoo.

it would still not work. I disabled it, went into systems>administration>network and found the DNS tab (overlooked it before) then i typed the DNS again, and it would still not work.

But then i connected trough wicd, with all the right information. And together it would work.

If people has the same problem a i, can you guys confirm if its just me that overlooked something, or if this really works. I encountered quite a few with the same problems as i

BTW im on Feisty

---

