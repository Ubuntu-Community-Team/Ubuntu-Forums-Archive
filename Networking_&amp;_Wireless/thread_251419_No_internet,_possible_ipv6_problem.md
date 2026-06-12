---
title: "No internet, possible ipv6 problem"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by Jackster on 2006-09-05
Hi, I was wondering if anyone here could help,
I'm having a problem with Ubuntu, and I think it's related to ipv6. I couldn't access the internet at all, but then I disabled ipv6 in Firefox and I could browse the internet in Firefox, but still things like Gaim or Software Update wouldn't work. I tried following this: [http://www.ossgeeks.co.uk/?p=20](http://www.ossgeeks.co.uk/?p=20) , and it does seem to have disabled ipv6, but there is still no internet available in anything except Firefox.

Anyone have any ideas?
Thanks,
Jackster

---

### Post by coffeecat on 2006-09-05
From your firefox experience it definitely is an IPv6 problem. Three suggestions.

You might find [this thread]("http://www.ubuntuforums.org/showthread.php?t=87798") useful. The instructions at the beginning are more to do with Breezy and there are some posts later on that say they don't work in Dapper. Towards the end are some posts from people who say they have disabled IPv6 in Dapper. I don't know whether these modifications are different from what's in your link. Might be worth checking.

or

Disable DHCP and set up a static IP address for your computer in the range recognised by your router. You'll also have to assign gateway, subnet mask and DNS addresses (your ISP DNS addresses) manually as well. This should get round the problem.

or

See if your router manufacturer has released a newer version of the router firmware. Last year I had a D-Link router that clobbered me with the IPv6 issue. After using static addresses for a time I fixed it once and for all by updating the firmware and I could use DHCP. But others have not been so lucky - not all manufacturers are on the ball with this one. This, I believe, is the fundamental problem - inadequate router firmware unable to cope with IPv6 modified addressing.

---

### Post by Jackster on 2006-09-06
Hi coffeecat, thanks for your reply, I'll try the firmware on the D-Link website, it says it's the GPL Code for it though so I'm not sure if it'll work or not... probably not.

If it doesn't work then I'll just disable DHCP, hey it's a chance to learn about networks :)

---

