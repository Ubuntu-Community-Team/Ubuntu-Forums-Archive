---
title: "TEW-632BRP Internet Problems"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Zarckon on 2008-11-20
I'm having a problem with the Trendnet TEW-632BRP wireless router. I've searched the forum here and elsewhere on the net and I put in a help ticket with Trendnet support. And still haven't been able to solve this problem.

I'm connecting to the internet through the wired ports, so wireless is not the problem here (at the moment anyway). When I go to web mail on Yahoo or Hotmail, I can open the site and get a list of the mail waiting to be read, but clicking on a message, just goes to the activity signal then eventually some error (something like "page failed to load"). It's not a fluke and it goes away immediately when I change back to the old router.

I've found a number of places that I can't submit as well. When I tried to submit a helpdesk ticket at Trendnet it stalled. When I tried to use the jump forums here it stalled. When I tried to put something in my shopping cart on Amazon it stalled. Again all of this goes away completely when I return to the old router.

So, some interaction between the operating system (Hardy) and the router. I don't have a clue as to what all of these things have in common. Any help would be appreciated.

Oh, yeah, it's not just Ubuntu with the problem. Same problem with XP home on a Viao laptop. XP home on a desktop works fine with the new router, but no longer works with the old router. XP pro on a laptop seems to work fine with both.

Weirdness plus, thanks for any thoughts or other help.

---

### Post by superprash2003 on 2008-11-20
well this may sound weird, but you could try changing your DNS servers to opends , their ips are 208.67.222.222 and 208.67.220.220 .. change them in ubuntu itself

---

### Post by Zarckon on 2008-11-20
> **superprash2003 said:**
> well this may sound weird, but you could try changing your DNS servers to opends , their ips are 208.67.222.222 and 208.67.220.220 .. change them in ubuntu itself

Interesting idea... However, under networking the DNS server that is listed is the router IP and the router gets DNS services from my ISP. I did add the two DNS services to my networking to see what would happen and it did not change things.

It seems to me that whatever the solution is, it has to account for two (2) computers having no problems and two (2) computers having problems. Since the router is choosing the DNS servers from the ISP all computers are using the same DNS, but don't all have the same problem.

Still good thought, I think your suggestion focuses on what the operating system might be doing in relation to the router. And please correct me if I went to the wrong place to set DNS in Ubuntu, or if you think I should try deleting the router as the DNS and adding the two (2) that you suggest.

It is a puzzle.

---

### Post by superprash2003 on 2008-11-21
here.. this should help [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Zarckon on 2008-11-22
> **superprash2003 said:**
> here.. this should help [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

Thanks for the more detailed instructions on adding the DNS. I added them following the instructions. No change. I turned the machine off and did a cold restart. No change. I think we can safely conclude that it's not the DNS settings.

Any other ideas?

---

### Post by superprash2003 on 2008-11-24
hmm.. could you post output of cat /etc/resolv.conf

---

### Post by Zarckon on 2008-11-28
> **superprash2003 said:**
> hmm.. could you post output of cat /etc/resolv.conf

I'll attempt to do that sometime in the next few days. I've blown up my boot into Linux somehow and haven't yet gotten a fix for it. Thanks for your thoughts.

---

