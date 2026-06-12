---
title: "My university won't play nice with others"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by useresq on 2008-09-09
Two problems I've hit since I switched over to Ubuntu two weeks ago. Both involve my school's networking and both are problems that I've seen lots of people complaining about. But none of the solutions that anyone has suggested have worked for me.

The first is their use of a SecureW2 authorization system for the campus wireless network. I tried to get around using wpa_supplicant and it failed. So I asked my college's IT guys and...nothing. So I asked the campus IT guys and...nothing (kudos, though, to one techie for personally supporting Linux even though it is officially not supported, but his solution didn't work). So I asked the computer science department's IT guys and...nothing (again found an unofficial answer that didn't work).

Other people are claiming these solutions are working on systems with similar hard- and software to mine, so I can't figure out what I'm missing. wpa_supplicant's output ostensibly claims it connects to the network and receives authorization, but wpa_supplicant never terminates, and then there's no connection. I also haven't figured out how to switch between the campus network and the one I have at home, but I haven't tried since I can't get the former up and running.

The other involves the printing system they use in my school. The official answer is to use iPrint by Novell. I'm not a huge fan of Novell, but I gave it a try and it fails miserably. First I tried to add the printer the "normal" way by selecting it from the list on the iPrint server. That froze Firefox. Then I found that you can bypass this by adding the ipp to the printer list directly. But when I tried that it never prompted me for my username/password (for the secure printer) and won't print without them.

Neither of these problems is that bad (though the last three days the unsecure network on campus that functions as my backup has been down), but I would appreciate help getting them fixed.

Thanks!

-asg

---

### Post by Guilden_NL on 2008-09-09
Just a quick thought, what about asking them for Mac support and seeing what their answers are?  Much of Mac can be tweaked to work in Linux.  At minimum, you can determine where they are authenticating in the login process and perhaps tweak around it.

---

### Post by useresq on 2008-09-09
I'm fairly certain I wouldn't be able to figure anything out from that on my own.

In fact, if anyone does have a solution, it might be a good idea to talk to me like I was a five-year-old. (It *might* not be necessary, but I expect it will.)

-asg

---

