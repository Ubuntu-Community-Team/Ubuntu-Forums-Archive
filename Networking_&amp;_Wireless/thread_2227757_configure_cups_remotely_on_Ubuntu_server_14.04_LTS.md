---
title: "configure cups remotely on Ubuntu server 14.04 LTS"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by Bradley_Lathan on 2014-06-03
Greetings all,

I have been trying to install cups and configure it remotely due to the system being headless.  It's currently running 14.04 LTS with the latest version of cups from the repo that it comes with.  Does anyone know of a good tutorial for me to follow before continuing to pull what little hair i have left out?  Somebody is bound to have blazed this trail already. I'd Also like to add Airprint support but it's not a big issue at this point.

The problem is that when I surf over to the cups and website try to configure.  It asks for my credentials, so I type my username and password and it keeps on popping up the dialog until it says unauthorized.   So i must be missing a step that is a stupid simple permissions issue somewhere. I have added myself to the lpadmin group.  Is there another group that I need to be added to in order to make cups happy with my changes? Thanks.

---

### Post by Bradley_Lathan on 2014-06-05
I was able to figure this out on my own, what it ended up being was in my /etc/network/interfaces file there was no reference to my local domain so I added it and made sure I was a member of the lpadmin group and it started working great.

---

