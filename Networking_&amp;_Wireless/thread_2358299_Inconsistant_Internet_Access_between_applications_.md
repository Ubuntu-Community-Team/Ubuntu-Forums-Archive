---
title: "Inconsistant Internet Access between applications when connected to router."
date: 2017-04-11
forum: Networking &amp; Wireless
---

### Post by Thepinkgamer on 2017-04-11
Hello

I purchased a router (NetGear N300) and been having some problems with applications getting Internet access when connected to it. 
It's very inconsistent. When I'm connected wired directly from the wall to my computer everything works fine, fast and generally ubuntu-great. 
However when connected via the router (wirelessly or wired) not all applications seem to like it. Skype works sometimes after a while of waiting, discord works similar but not voice chat. 
Browsers like palemoon works about 50% of the time while others like chrome works fine and some applications just don't get any internet at all. I have tried to search for solutions but haven't come up with any. I tried asking the Netgear forums but haven't really gotten a clear solution as they seem to be more interested in the internet provider then actually suggesting a solution. So I am checking here if it's maybe a softare-related issue on my end. The biggest problem is that the OS sometimes doesn't want to update, it just says it can't connect to launchpad. I have been having this issue on Xubuntu and ElementaryOS and on different computers with the same results. I have not tried any none-ubuntu based distros. 

I am running

---

### Post by TheFu on 2017-04-11
TL;DR - disable netgear's wifi and get a ubiquity WAP. Plug it into one of the netgear switch ports. Be happy.

The longer version ....
My LUG meets at a restaurant with a $300 netgear. Whenever more than 3 devices connect via wifi, it would crap out.  Because we have a good, long, relationship with the owners, they let us do almost anything with their networking. Initially, I'd bring a powerline ethernet setup, connect that into the netgear and we'd share a dumb switch at the table. Everything worked great. No issues, but the setup was cumbersome and we outgrew the 8-port switch.  I took a collection to get a better WAP. In my old day job, I did thousands of wifi deployments using all sorts of equipment from $20 cheapo devices to $20K grid wifi networks connected into $65K switches.  That lead to some clear decisions - for the money, a Ubiquity AP is the best solution to fix netgear wifi issue. At $70, it was an easy choice.  Now we have 40+ concurrently connected devices at the meetings, no wifi issues.  Life has been great almost 2 yrs later. The wifi "just works."

A few others I know have had issues with netgear stuff working with everything.  We screwed around with channel width, locked the connection speeds and protocols, but in the end, no solution that worked with everything was found.  I avoid netgear. Plus they don't have the best response to security issues with their equipment. OTOH, most consumer routers fail at that too.

---

### Post by Thepinkgamer on 2017-04-12
> **TheFu said:**
> TL;DR - disable netgear's wifi and get a ubiquity WAP. Plug it into one of the netgear switch ports. Be happy.

The longer version ....
My LUG meets at a restaurant with a $300 netgear. Whenever more than 3 devices connect via wifi, it would crap out.  Because we have a good, long, relationship with the owners, they let us do almost anything with their networking. Initially, I'd bring a powerline ethernet setup, connect that into the netgear and we'd share a dumb switch at the table. Everything worked great. No issues, but the setup was cumbersome and we outgrew the 8-port switch.  I took a collection to get a better WAP. In my old day job, I did thousands of wifi deployments using all sorts of equipment from $20 cheapo devices to $20K grid wifi networks connected into $65K switches.  That lead to some clear decisions - for the money, a Ubiquity AP is the best solution to fix netgear wifi issue. At $70, it was an easy choice.  Now we have 40+ concurrently connected devices at the meetings, no wifi issues.  Life has been great almost 2 yrs later. The wifi "just works."

A few others I know have had issues with netgear stuff working with everything.  We screwed around with channel width, locked the connection speeds and protocols, but in the end, no solution that worked with everything was found.  I avoid netgear. Plus they don't have the best response to security issues with their equipment. OTOH, most consumer routers fail at that too.
Thank you, any particular model you recommend?

---

### Post by TheFu on 2017-04-12
> **Thepinkgamer said:**
> Thank you, any particular model you recommend?

Depends. You knew that already. I doubt you want the 150km models or the 10 yr old M2/M5 stuff. ;). 
If you don't need more than the $65 model provides, as long at it isn't too old, I wouldn't worry.

I have zero financial connection with the company. Just a happy client.

Should also say that I do NOT have a ubiquity AP in my home. Haven't needed it and we don't use wifi much. With all my wifi experience, almost everything here is wired ethernet. The wifi network isn't part of the core network here. It is for guests.

---

