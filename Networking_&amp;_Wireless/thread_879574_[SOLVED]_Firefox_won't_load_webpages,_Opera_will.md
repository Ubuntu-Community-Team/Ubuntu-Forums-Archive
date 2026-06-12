---
title: "[SOLVED] Firefox won't load webpages, Opera will"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by cszikszoy on 2008-08-04
Hello,
 
I'm having a very strange problem with Firefox. I can't view any webpages in firefox, but I know that I have a connection to the internet. I'm currently posting on the same computer from within virtualbox, where the internet works fine.
 
In console, I can ping external websites without any problem. I've tried moving my configuration folder under ~/.mozilla/firefox, and have even tried uninstalling then reinstalling firefox. For whatever reason, it simply wont load a single webpage.
 
Oh, i've also disabled ufw, but as I said before, browsing the internet from within a virtual machine works fine.
 
Any help is appreciated!!  Thanks.

---

### Post by dentaku65 on 2008-08-04
Did you check if Firefox is set in offline mode?
You can check this under File->Work Offline

---

### Post by cszikszoy on 2008-08-04
> **dentaku65 said:**
> Did you check if Firefox is set in offline mode?
You can check this under File->Work Offline

Yes, usually if firefox is in offline mode it will display an error right away when you try to navigate to a webpage.

When I try to navigate to a webpage it just shows a blank page, and shows the status circle spinning like it's doing something, but nothing ever happens.

---

### Post by cszikszoy on 2008-08-04
anyone?

---

### Post by Vorian Grey on 2008-08-04
Does everything else work fine on the internet, like email, chat and whatnot? Or is it just firefox?

---

### Post by Baelus on 2008-08-04
Firefox may be using some kind of proxy info. You can check it by going to:

Edit -> Preferences -> Advanced -> Network -> Settings

Make sure it's using a direct connection.

---

### Post by cszikszoy on 2008-08-04
Thanks, I actually solved it just a little bit ago.  And it related to the proxy, but not on the FF side...

I was trying to use a different DNS server last night. Somehow (???) this changed my proxy settings in gnome. After I changed these back to normal everything is fine again.

Thanks though!

---

### Post by Xtian_1028 on 2010-06-22
Oh! I have a very similar problem right now!

Can I ask for the steps you took to finally solve why firefox won't load webpages?

Thanks!

---

