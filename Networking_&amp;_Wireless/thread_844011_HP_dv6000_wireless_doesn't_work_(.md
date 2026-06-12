---
title: "HP dv6000 wireless doesn't work :("
date: 2008-06-29
forum: Networking &amp; Wireless
---

### Post by gamer4lyf3 on 2008-06-29
Greetings everyone, I recently got a new laptop and I'm trying to get Ubuntu's wireless to work correctly. I can get a connection just fine I can connect and everything. But I can never actually browse the internet even though it says it's connected. I don't think it's the driver though because I can look at all the networks in my range. if you need information just let me know and let me know how I can get the information please :)!

---

### Post by bobyy on 2008-06-29
Hy there
If you want to somebody try to help you 
add some infos ..like output to ifconfig ,route -a ....if you have a router or not..witch type of connection you have ...stuff like this...

regards.

---

### Post by b3n5p34km4n on 2008-06-29
i'm replying to this because i have the same laptop and i'm also having problems connecting to the internet.

i just installed 32 bit hardy after getting rid of 64 bit hardy.  internet worked perfectly for 64 bit.  i could detect wireless networks and everything.  but i just installed 32 bit and with th network thing it only gives options for wired and for dialup.  it doesn't detect wireless networks.  i am on the laptop right now because i dual boot vista and the internet is working perfectly.  it was also working perfectly about two hours ago when i had 64 bit.

---

### Post by b3n5p34km4n on 2008-06-29
i switched from 64 bit to 32 bit because i couldn't get flash to work.  now with 32 bit i can't even get basic wireless internet to work whereas with 64 bit it worked like a dream with absolutely no trouble or setting up involved.  i am considerably frustrated so i would very much appreciate anyone's help that could get my wireless working.  i've already tried 2 of the walkthroughs with absolutely no result.  this boggles my mind as to why a fresh install of 32 bit doesn't have wireless and a 64 bit does.

---

### Post by gamer4lyf3 on 2008-06-29
Hey with a little looking around I got it to work! :). follow this persons instructions exactly and it should all work out fine for you.
[http://ubuntuforums.org/showpost.php?p=4808350](http://ubuntuforums.org/showpost.php?p=4808350)

---

### Post by b3n5p34km4n on 2008-06-29
wow, still didn't work for me.  this is unbelievable.  if i can't fix this problem i'll have to go back to windows...  and i don't want that... can't anyone help me?

---

### Post by Ayuthia on 2008-06-30
> **b3n5p34km4n said:**
> wow, still didn't work for me.  this is unbelievable.  if i can't fix this problem i'll have to go back to windows...  and i don't want that... can't anyone help me?

I saw in one of your posts that you have a 14e4:4315 card.  It might be possible that your card worked when you installed linux-restricted-modules in the past.  There was a wl driver that was recently introduced in Ubuntu, but it looks like they might have taken it out.

You might try this link:
[http://ubuntuforums.org/showthread.php?t=786397](http://ubuntuforums.org/showthread.php?t=786397)
It has helped some people get that card working using ndiswrapper.

---

### Post by b3n5p34km4n on 2008-06-30
thanks! i'll try it and let you know how it works

---

