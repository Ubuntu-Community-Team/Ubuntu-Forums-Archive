---
title: "Ethernet cables"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by devid88 on 2014-03-06
[COLOR=#434343][FONT=helvetica]Hi friends how are you ?
plz tel me  which cables in best for networking systems?

[/FONT][/COLOR]

---

### Post by TheFu on 2014-03-07
Welcome to the forums.  That is a broad question.
[https://en.wikipedia.org/wiki/Category_5_cable#Category_5_vs._5e](https://en.wikipedia.org/wiki/Category_5_cable#Category_5_vs._5e)

The answer depends.
* what sort of network?
* how far apart are the components?
* what cards and switches?  How fast are all these components rated?
* is there any interference along the path the cables will run?

So ... without that data, let's assume a 10/100/1000 base-tx network will less than 50ft of separation between any 2 components.  CAT5e is the answer.  Buy cables to fit your size needs from monoprice.com or amazon. Cheap, good, cables.  Avoid paying retail which usually cost 3x more.  

CAT5e is more than 10/100 needs, but cheap enough that when you are ready for GigE (1000 base-tx), it is there already. It provides plenty of overhead for GigE networks and there really isn't any need for CAT6. CAT6 does not support 10G-base-tx networking, so it provides much, much more overhead for GigE, but not enough for 10G. Stick with CAT5e.

Of course, if you are running an infiniband network, CAT5e is useless. Same for a fiber network. Those are completely different networking standards.

---

