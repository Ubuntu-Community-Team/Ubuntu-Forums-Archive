---
title: "wireless problem"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2010-03-26
Hi. Ive just moved to a house with a wireless internet connection. Same as in my old place I entered the wpa2 key and the internet said it was connected. I can enter the router setting page and i can ping google.com but when I open firefox it says "problem loading page". Can anyone help me? please? Tankyou

Is this a DNS issue?

p.s i'm running the lucid beta...

---

### Post by Mykk on 2010-03-26
you could try

sudo /etc/init.d/dns-clean start

Might work.

---

### Post by e1ektrob0y on 2010-03-26
Thanks but that didn't work. I did however type the ip for google in firefox addres bar 66.102.11.115 or something. It took me straight to google. But if i type in the address bar [www.google.com](www.google.com) i get "problem loading page". 

Any ideas?

---

### Post by Mykk on 2010-03-26
Well that confirms its a DNS problem.

I'll have a read and see what i can find.


Try another browser (not as a permanent solution, just for testing)?

---

### Post by e1ektrob0y on 2010-03-26
will do. thanks.

---

### Post by e1ektrob0y on 2010-03-26
so yes...is this a DNS issue with lucid all round or is this just me? does anyone have any helful links or info? thanks guys :)

---

### Post by admiralspark on 2010-03-26
I'd recommend OpenDNS. They're a superb service, and I've yet to run into any problems with them (plus, for me it's faster than using the host DNS servers). 

One other thing, in your Firefox Preferences, going into Networking from the Advanced tab...is any sort of proxy set? Sometimes there are misconfigurations left over from a previous ISP?

---

### Post by e1ektrob0y on 2010-03-27
i just tried using the 9.10 live cd. I had the same issue. I could load Google using the 66.102.11.115 but google.com gets "probem loading page". So i'm assuming now that its something to do with linux an the router here? now that the problem has been significantly narrowed down...please help me! thanks guys :)

---

### Post by e1ektrob0y on 2010-03-28
Solved. Disable ipv6 in grub. The new router is actually old and it cant handle ipv6 :( thanks for the help guys...

---

