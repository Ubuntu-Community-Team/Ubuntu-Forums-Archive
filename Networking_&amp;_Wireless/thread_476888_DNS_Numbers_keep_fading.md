---
title: "DNS Numbers keep fading"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by BobSongs on 2007-06-17
[FONT=Verdana]Greetings;

I'm running Ubuntu Dapper Drake. I'm up to date as far as patches. But I've been running into a bit of a networking problem lately.

**[COLOR=Gray][font=Verdana]the details[/font][/COLOR]**
I've got a router (Belkin) that works fine. My Mac is currently surfing this site. 

But what's been happening is that when my user name is logged off (there are five users, two with administrative privileges) the Ubuntu box loses its connection to the Internet (i.e., the router). Each time I'm logged out by a family member I must:[LIST]
[*]login (my account allows for the usage of **sudo**)
[*]click **System** (from the menu)
[*]**Administration**
[*]**Networking**[/LIST]The **Network Settings** box appears. When the DNS tab is clicked the numbers are gone. After they're added clicking OK makes everything work.

However today entering the DNS numbers resulted in the busy cursor icon and the box hangs there. The system no longer accepts these numbers.

What is the file name (and its location) where the DNS numbers are usually stored? I don't mind entering the numbers manually. I just have no idea where to begin.

Bob

(**Edit:** I've just logged in the second administrator account and that account ***is*** fine as far as DNS numbers and surfing the web. So, it's just my own login name that's not working.)[/FONT]

---

### Post by nixfaced on 2007-06-17
Hi, 

The file you're looking for is /etc/resolv.conf.

---

### Post by BobSongs on 2007-06-17
[FONT=Verdana]Yep. That's the file. *Much* appreciated.[/FONT]

---

### Post by BobSongs on 2007-06-17
[FONT=Verdana]And the problem is resolved. :) I'm not entirely sure *how. *I guess it may have happened when I checked the DNS numbers under the 2nd administrative account.

Thanks again!
[/FONT]

---

