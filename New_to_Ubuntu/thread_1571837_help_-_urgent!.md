---
title: "help - urgent!"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by gdtw on 2010-09-10
Hi all,
I am not experienced with ubuntu, postfix, apache. I am hosting my own site on this ubuntu machine. Now I got a problem. Will someone please help?

So I had a system clock problem - clock was 17 minutes ahead of world time. So I fixed it by moving it backward. (The reason I adjusted the clock was because my website credit card  transaction could not go through because of the time hash problem -  clock was off by more than 15 minutes.)

Soon after, I realized that my thunderbird keep saying "cannot connect to mail server  ..@... connection was refused."

I look at mail.log and see that at the time when I adjusted the clock: "... web-server dovecot: fatal: time just moved backward by 970 sec.. this might cause a lot of problem, so i'll just kill myself..."

I have tried postfix restart, but it did not do anything.

How do I fix the problem? Is the mail problem caused by the clock adjustment? What other problems can this server suicide cause?

Thanks for your help.

---

### Post by scottuss on 2010-09-10
Whoa now, by credit card transaction you presumably mean a transaction that you are making, and hopefully not transactions that people are going to be making through this server, right?

I'd recommend syncing your clock with an NTP server. To fix the issue, some services might want a restart. To ensure you get them all, I'd just do a reboot. Not the "nix" way but probably gets the job sorted, and this isn't a mission critical server.

---

### Post by gdtw on 2010-09-10
Looks like reboot fixed the mail problem. I hope there is no other potential problems?
I wonder if the clock being off can cause other problems? will it slow down the server?

In the beginning, I follow all the advices I found such as caching images to speed up. At one point, google webmaster shows my site's speed was faster than 98% of the sites. 5 months later now, the load speed is at the bottom half, slower than 60% of the sites. The site is a retail site and I have not added more items (now at 60K+).

Any tips on how I can fix the speed problem?

Thanks

btw, it looks like the clock being off also caused a long list of PCI compliance scan vulnerabilities.

---

### Post by scottuss on 2010-09-10
With the greatest of respect I'm concerned that a retail site is being administered by someone who themselves said "I am not experienced with ubuntu, postfix, apache"

However, you shouldn't have any more issues with time as long as all of the daemons have come back up correctly.

As for the speed issue, that's something else entirely to look into.

---

### Post by gdtw on 2010-09-10
I know. as a matter of fact, "not experienced with" is an over statement.. its more like "not familiar with.."

---

### Post by scottuss on 2010-09-10
Yikes! I don't mean to be rude but I'd hope any site I'm putting my credit card / other details into would be managed by someone who knows exactly what they're doing.

However, if you do need help, this forum is a good place to come to.

---

