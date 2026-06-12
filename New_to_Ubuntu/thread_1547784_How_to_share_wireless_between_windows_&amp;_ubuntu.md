---
title: "How to share wireless between windows &amp; ubuntu PC"
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-07
Hello:

My wifes windows laptop connects to the internet via a Novatel Turbo Stick.

Is it possible for me to use her internet connection by attaching my ubuntu laptop to hers by using a network cable?

Thanks,

Rob.

---

### Post by iansane on 2010-08-07
Not sure of the whole process but conceptually I think this is right.

On the windows pc you might need to find out how to bridge the wireless to the wired NIC. I'm not sure and a little confused about that part but it seems to make sense if you're plugging the linux pc into the windows pc.

Turn on internet connection sharing which sets your ip address to static
here's a link for how to in windows XP. Assuming the same works for wireless as it would for the NIC
[http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

You'll want to set your wireless router up to always give the static IP to the laptop which is different in different routers.

Then plug the linux pc into the laptops NIC and set the ip and default gateway of the linux pc according to the assigned static address of the windows pc.

Probably not a lot of help but this is just what comes to my mind as a starting point. Hope it helps

---

### Post by lkraemer on 2010-08-07
You can search for ad hoc network and do it that way.
one ref is:
[http://www.cs.washington.edu/research/edtech/presenter/doc/adhoc.html](http://www.cs.washington.edu/research/edtech/presenter/doc/adhoc.html)

lk

---

### Post by JustinR on 2010-08-07
Nevermind.

---

### Post by S.R on 2010-08-07
Edit to match previous edit.

---

