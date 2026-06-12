---
title: "Wireless Intermittent in presence of mutiple wireless networks"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by amashal on 2007-09-26
Hello all,

I have a huge favor to ask.  I am new to the linux enviornment and I am having trouble with my wireless.

When I am at home my wireless works fine because it only sees one strong wireless signal.  But when I am  in a public place and there are multiple wireless sources my wireless keeps connecting and disconnecting, until it just doesn't connect anymore.  Initially when I restart my computer my wireless works fine, but after 10 minutes or so this pattern keeps repeating it self.  I am guessing that these multiple wireless sources are confusing my computer.

I am using a Dell Inspiron 700m.  I had to run the bcm43xx-fwcutter to get the wireless to enable initially.  I am not sure if this is relevant or not?

Thanks and please help!

Al

---

### Post by golbasche on 2007-10-31
I have had problems with my wireless seeing a bunch of networks.  It will join one and refuse to join any other, even if it is strong enough to connect.  I tried to find the process that was running and restart it.  I looked in /etc/init.d and restarted things until one of them restarted the process for wireless (I think)

I restarted /etc/init.d/dbus and everything works normally.

$ sudo /etc/init.d/dbus restart

I'm not sure how related this is but I hope it helps. It''s probably not the right way, but its better than restarting the computer like I was doing.

---

