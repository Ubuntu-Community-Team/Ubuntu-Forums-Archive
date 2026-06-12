---
title: "ubuntu and nvidia geforce 4 mx 4000; a match made in hell?"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by John Galt on 2011-04-01
Hello everyone,

this comes from a person who has done everything in his power to try and understand what is it that is wrong. Previous posts have not yielded any results.

I have p4 2.4 ghz, nvidia geforce4 mx 4000 graphics card and 512 mb ram.

The problem is even after installing the necessary graphics driver from software repository and the additional drivers section (tried both methods), still i am not able to use the "visual effects" section in the "appearance preferences" of the "change desktop background" section. The compiz also doesn't seem to work. Basic functions like screen resolutions and colour corrections are working.

The errors screen is shown as a png attachment with this post. Also attached are the driver details screenshots.

Please advise.

---

### Post by John Galt on 2011-04-03
what....no posts yet!!!????

is there no solution to this problem??

@moderator....is this query posted in the wrong section?

if it is please move it to the right section. Thanks

---

### Post by clhsharky on 2011-04-03
John Galt


I never was able to use compiz(compositor) on legacy chip(nvidia geforce4 mx 4000)on Ubuntu 10.10(modern OS).
I also don't believe nvidia legacy drivers support 10.10 either, as far as I could tell.
Nouveau OSS drivers worked well with metacity(compositor)but not compiz.
Haven't tested the latest open scourse drivers(OSS)lately, to see if they now work with compiz on(geforce4 mx 4000).
Here
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)
I now only use this card now for testing old AGP boards.
Gforce 5200 cards do work well on AGP boards with Nvidia legacy driver and 10.10.


Sharky

---

### Post by 123456789123456789123456 on 2011-04-03
there is also a program that enables special effects, it is not the default program that comes with ubuntu.  and I have found that if you have the default program enabled, the extra effects from this program, can not think of the name right off, seems to mess with each other, canceling out all effects.  it is worth a try.  I have been experencing simular issues with other graphics cards.

---

### Post by John Galt on 2011-04-03
so basically.... the idea is to upgrade to better gear

---

### Post by John Galt on 2011-06-02
yaay...i finally got compiz to work for me....

and how i did it....really stupid on my part...

had not put in the compiz fusion addin yet...had downloaded ccsm, compiz and emeral but not compiz fusion.

downloaded that and now compiz just needs to be started with a click after login.

closing this thread..

happy ubuntu user...ubuntu rocks

---

