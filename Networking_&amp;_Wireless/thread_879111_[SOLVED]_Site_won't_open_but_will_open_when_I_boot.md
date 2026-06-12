---
title: "[SOLVED] Site won't open but will open when I boot live CD"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by randyclark on 2008-08-03
I cannot open a site ([www.cokesbury.com](www.cokesbury.com)) that I use regularly for work and have been able to open in the past. In Firefox 3.0.1, the progress bar in the lower left gets to about halfway and then nothing happens. I have tried Lynx, Opera, and IE under Wine and none of them can open the site either.

I can open the site from a Windows XP machine and a laptop running Vista both of which are connected to the internet by the same router as the Ubuntu machine that won't.

The odd thing is is that if I boot 8.04 using the live cd and attempt to open the site, it opens fine/ 

I have tried pinging both the site but no packets get through. When I attempt to open the site using the IP address I find when I do a lookup, I get "Bad Request (Invalid Hostname)." 

FYI I am using the OpenDNS nameservers on my router.

Any suggestions? I have searched the forums and Google to no avail.

I assume something has been set inadvertently that is causing such trouble with the site. All other sites, to the best of my knowledge, open fine.

---

### Post by cpetercarter on 2008-08-03
There is a heap of Javascript on that site, with no "noscript" alternatives. You do have Javascript enabled, don't you?

---

### Post by randyclark on 2008-08-03
Yep... one of the many things I tried before getting to this point. Thank you, though, for the question.

---

### Post by randyclark on 2008-08-04
Although I never got any help on this question, I ultimately solved the problem by following the advice here:

[http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon]("http://www.ventanazul.com/webzine/articles/cannot-access-websites-ubuntu-gutsy-gibbon")

I suspect someone can explain why his advice works, but I:

(1) Installed firestarter (sudo apt-get install firestarter)

(2) Ran the configuration wizard.

(3) Now the site loads!

If you stumble across this problem, which others seem to have, give this a try. Nothing else worked for me.

---

