---
title: "xubuntu 10.04 firefox weirdness: my3.com.au"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by kookoo78 on 2010-05-30
I'm running on a Toshiba NB300 notebook and have encounter an odd problem. Can someone enlighten me?

I just downloaded and updated (70mb+) of xubuntu 10.04. Also installed the restricted driver set (flash etc).  Plugged in / installed Huwaei 3G usb modem that runs of the Three network. All of it works wonderfully, except...

Whenever I go to [http://www.my.three.com.au/](http://www.my.three.com.au/) Firefox refuses to connect to the site

```

    * The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.


```I'm pretty sure this is a firefox issue, because I just checked out the site in Ubuntu 9.10 on my other PC and the site works fine. I tried installing Midori on xubuntu, but that also failed to bring up the three site, so am thinking it's a xubuntu oddity. Other sites seem to work just fine

Could someone with Xubuntu 10.04 try accessing [http://www.my.three.com.au/](http://www.my.three.com.au/) and letting me know if they also have issue reaching the site? Any ideas why this might be / how to fix it? (I tried setting Firefox on 'no proxy', but same result)

---

### Post by nhasian on 2010-05-30
just to clarify, your internet is working fine and you can reach all sites except for my.three.com.au?

---

### Post by lovinglinux on 2010-05-30
I can reach that site. for future reference, use [http://downforeveryoneorjustme.com](http://downforeveryoneorjustme.com)

To fix your problem I would start by disabling ipv6. See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

---

### Post by kookoo78 on 2010-06-01
> **lovinglinux said:**
> I can reach that site. for future reference, use [http://downforeveryoneorjustme.com](http://downforeveryoneorjustme.com)

To fix your problem I would start by disabling ipv6. See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").


Hey, that solves it. Thanks!

---

