---
title: "Problem with the Scubuntu-theme"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by bhargava470 on 2009-05-26
Hi
I recently installed packages that come with scubuntu, but after installing a few I started noticing the following message being displayed every time:

 /usr/share/themes/Scubuntu/gtk-2.0/gtkrc:87: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Scubuntu/gtk-2.0/gtkrc:88: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/Scubuntu/gtk-2.0/gtkrc:199: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.


I searched for this in the web and found a few, but i couldn't solve this on my own.

[CENTER]Thought this might be useful:

apt-cache policy scubuntu-theme
scubuntu-theme:
  Installed: 0.4
  Candidate: 0.4
  Version table:
 *** 0.4 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
        100 /var/lib/dpkg/status
[/CENTER]

Can anyone tell me how to fix this.

Thanks.

---

### Post by bhargava470 on 2009-05-26
Sorry forgot to mention, when i change the theme I 'm not noticing any problem...noticing the message only when scubuntu-theme is applied.


Thanks

---

### Post by SunnyRabbiera on 2009-05-26
I have seen this issue pop up before, from one of my own themes.
I would not worry about it, as it doesnt mean the system is comprimised or anything.
It is annoying though

---

### Post by oOarthurOo on 2009-05-26
It's not a problem at the moment. It's just a warning message to the developers. That kind of stuff is better placed in a readme in /usr/share/doc, so that it doesn't confuse the users. 

Ignore it.

---

### Post by bhargava470 on 2009-05-26
Thanks for the reply.

---

### Post by SunnyRabbiera on 2009-05-26
If you want to play around with it though you can edit the theme on your own, you could install gksu-nautilus to allow you administrative access and with gedit (the text editor for ubuntu) you can edit the file.
But for the new user I would not do it right away, learn a bit more first before doing anything drastic.

---

