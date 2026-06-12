---
title: "Internet Access Problem"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by uber on 2006-08-07
So after a fresh install of Dapper AMD64, I have noticed I can no longer access the internet from within Ubuntu. I can get online just fine in XP (that's where I am right now) so I know the modem/router/hub all works just fine. In Ubuntu, I can ping sites (Google, Yahoo, Digg, ect.) I can also use apt-get just fine, its just that in Firefox nothing seems to work. Any thoughts?

---

### Post by louis_nichols on 2006-08-08
What kind of errors do you get in firefox?

Do you, by ay chance, need to set up a proxy?

---

### Post by drtvasudevan on 2006-08-08
looks like ipv6 issue. not disabling it.
search these fora for solution.

---

### Post by eXisor on 2006-08-08
Ipv6 will not cause total failure, so it probably isn't that. Can you ping your router?

---

### Post by drtvasudevan on 2006-08-08
> **uber said:**
> S In Ubuntu, I can ping sites (Google, Yahoo, Digg, ect.) I can also use apt-get just fine, its just that in Firefox nothing seems to work. Any thoughts?

when apt get works and he can ping too this appears logical.
:rolleyes: 
in my case at least it*was* total failure till i opened about:config and toggled ipv6 value to true.

---

### Post by uber on 2006-08-08
I can also access some sites if I use the ip address instead of the web address. For instance, I can use google if I place the ip in the address bar, but not if I attempt to reach [www.google.com](www.google.com). I can also get around places like this if I only navigate by links (search on google, and then go from there) but the connection is horribly slow.

---

### Post by uber on 2006-08-09
I tried to search for ipv6 threads but could come up with nothing. Could anyone please explain to me what I should be doing?

---

### Post by drtvasudevan on 2006-08-09
well
open firefox
type about:config in the url box hit return key
when a list opens type ipv6 
now you will see only two lines.
double click on value  in the first line
it will change to true
close firefox; restart
sometimes this sets things right.
it did for me.
all the best.

---

### Post by RedBoot on 2006-08-09
Seems to me that it might be a problem accessing DNS.  Test this out:
dnsstuff.com shows that [www.google.com](www.google.com) is at 72.14.207.99. So try to input that in the address bar of firefox (i.e., type [http://72.14.207.99](http://72.14.207.99) and press enter. If you get the google.com site, then you may have your DNS entries messed up.

Are you using DHCP to get your IP and DNS stuff? If so, at the command line, reactivate DHCP:
```
sudo invoke-rc.d networking restart
```

If you assigned IP statically, go to System, Administration, Networking, go to DNS tab and input your ISP's DNS IP addresses.

---

### Post by uber on 2006-08-11
VICTORY! The ipv6 thing worked! I LOVE UBUNTU!!!!

Ok, I'm calm now.

---

### Post by drtvasudevan on 2006-08-11
great!
now copy the fix  in a text file and keep it on the desktop.
whenever you see a post like this : "new to linux. cant connect to net" post this as reply.
such a simple thing to try. if that does not resolve they can look further for guidence from experts!they are more likely to have a network /proxy problem.

---

### Post by speeddemon8803 on 2006-08-12
ok, im having a slightly different problem, still with xp, i am able to get through msn on my xp side, but when i try going to my ubuntu side with xp, its dead, ive tried to input the access numbers of MSN into my stuff, no success, what could i be doing wrong? any help would be greatly apreciated!

I am of course on dialup as you can see from "access numbers"

---

### Post by drtvasudevan on 2006-08-12
> **speeddemon8803 said:**
> ok, im having a slightly different problem, still with xp, i am able to get through msn on my xp side, but when i try going to my ubuntu side with xp, its dead, ive tried to input the access numbers of MSN into my stuff, no success, what could i be doing wrong? any help would be greatly apreciated!

I am of course on dialup as you can see from "access numbers"
perhaps this will help.
[http://www.ubuntuforums.org/showthread.php?t=87798&page=2](http://www.ubuntuforums.org/showthread.php?t=87798&page=2)
that will disable ipv6 across the board.
\\:D/ 
it is longish thread read through or if you havae no time just the posting number 66 which is the last one
let us know the result.

[-o<

---

### Post by RedBoot on 2006-08-12
> but when i try going to my ubuntu side with xp, its dead

Not sure what you mean by this. Can you explain?

---

### Post by drtvasudevan on 2006-08-12
i took it to mean that he can connect with msn messenger in xp and not in ubuntu.
in case you are trying to see the ubuntu partition from xp my friend, be advised that it is not possible.

---

### Post by speeddemon8803 on 2007-02-17
> **drtvasudevan said:**
> i took it to mean that he can connect with msn messenger in xp and not in ubuntu.
in case you are trying to see the ubuntu partition from xp my friend, be advised that it is not possible.

yes that is what I mean and sorry to burst your bubble but yes it is possible! (mount is your best friend!) If you have ntfs...your all good! I saw my winderz partition straight from ubuntu..and it was an ntfs partition.

---

### Post by speeddemon8803 on 2007-07-18
oh and since feisty, my wireless problem has been fixedid! :) (now all I gotta do is find my blasted WAP Key!

---

