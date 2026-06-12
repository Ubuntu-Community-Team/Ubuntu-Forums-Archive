---
title: "apt-get update kills network"
date: 2005-10-06
forum: Networking &amp; Wireless
---

### Post by amohanty on 2005-10-06
So I was away from my broadband for about a couple of weeks. When today I finally got back to it and saw the little red upgrade icon, I clicked on it and clicked ok after a review. However it was unable to install the latest version of firefox and firefox-gnome-support and broke it in trying to do so. So I had to uninstall ubuntu-desktop and other related stuff, log into recovery console and reinstall all of it, which went fine.

But ever since then everytime I hit apt-get update I get:
40% [Connecting to archive.ubuntu.com] [Connecting to security.ubuntu.com] [Con
and then thar goes my local network off of my router. And it will refuse to come back up till I power cycle my router and do a:
/etc/init.d/networking force-reload

Any ideas, getting desperate and dont really feel like reinstalling although I think will have to do so.

Thanks
A<+M

---

### Post by Jomx on 2005-10-08
I had a similar problem.

I auto updated Ubuntu and got stucked with the firefox problem.
In my case I could reinstall Firefox following the advice on thread "firefox 1.0.7-0ubuntu0.1_i386 update error".
I also had to reinstall my wireless drivers because the wireless network went out of order due to the update.
but now my network connection goes very slow and when I open applications as amule, which was also updated, latency to my wireless router can grow up till 70 seconds.
I uninstalled clamav which was also upgraded but no difference.

I regularly update my system every week. It looks like something strange happened with latest updates.

Just some clues but no answer.

---

### Post by Jomx on 2005-10-08
Something more.
Firestarter was upgraded at the sametime I did with the rest of the stuff. I downgraded Firestarter and now the downloading processes work much better. Latency went back to normal times. 

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused: Was Firestarter the problem or maybe a lower dependet module? Amule still has a nasty behaviour.

---

