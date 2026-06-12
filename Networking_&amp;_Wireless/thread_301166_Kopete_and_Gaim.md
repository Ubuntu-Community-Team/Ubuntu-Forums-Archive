---
title: "Kopete and Gaim"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by Zaff on 2006-11-16
Hi everyone,
Here's the thing, I'm new at Ubuntu and I used to have Gaim on windows and was really satisfied with it. So I was really happy to see it come directly installed with ubuntu. And on the live cd it worked great. But after installing ubuntu (i got dapper) i tried to log on msn AIM and Jabber and everytime msn logs on, gaim crashes. After several tries I finally installed gaim 2.0 (still unstable) and instead of crashing with msn here's what it says :
[COLOR="Red"]
<account> was disconnected due to an error: 
SSL support is needed for MSN. 
Please install a supported SSL library.
[/COLOR]
After fighting with synaptic for a while i eventually downloaded every single pack with SSL library in it and i still have the same problem.
So I gave up and installed Kopete. This time msn works fine but AIM won't start. Or more accurately it stays on "connceting" status for a while and if it manages to connects itself, it won't display my AIM contacts. The point being if i want to have all my contacts i have to launch kopete and Gaim which is kinda silly when you think about it.
So I kinda figured that maybe someone out there has a solution for me to at least one of these two problems. if possible I would prefer to use Gaim again but if kopete works it'll be fine.
And if anyone knows an equivalent that'll let me have AIM MSN and Jabber at the same time then i'll be happy as well.
Thanks.

---

### Post by ECPCLINUX on 2006-11-18
Hello, I'm also new at Ubuntu. As  a matter of fact I have been using Ubuntu for almost a week. I have not tried MSN on Gaim But I did try Gaim 2.o and it did not work well. Please do note That Gaim 2.0 is a Beta, nufsaid. Now I would recommend you use AMSN Instead of Gaim for MSN, it works really well for me. It seems you know already how to use Synaptic so just do a search for AMSN on Synaptic and install it. Since I'm no expert by any definition this is how I solved the problem. Hope this help, Good luck!  :wink:

---

### Post by qamelian on 2006-11-18
If you installed gaim 2 from source, you need to enable support for ssl when you run the configure script. I believe it's something like:
```
./configure --enable-gnutls
``` but I'm not 100% sure as I haven't compiled it from source for a while. Gaim 2 is included by default in Ubuntu 6.10 'Edgy Eft', by the way, and is already built with this option enabled.

---

### Post by Zaff on 2006-11-19
well AIM finally works with kopete (for some unknown reason maybe kopete felt i was gonna leave it for psy if aim wasn't gonna work :D ) so i'm letting go of gaim in linux (but not in windows).
Thanks for the help.

---

