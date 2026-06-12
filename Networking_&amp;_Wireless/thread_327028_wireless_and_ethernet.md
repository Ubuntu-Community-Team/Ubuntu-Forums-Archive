---
title: "wireless and ethernet"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by liamjames91 on 2006-12-28
been using ubuntu for about half a year, i have a toshiba laptop with wireless internet running edgy eft, thats connected  wirelessly to a wireless router](*,) lol duh? , i also have another desktop pc running edgy, is it possible to use the laptops wireless internet on the desktop connected via an ethernet cable ? or am i asking too much?? :confused: if its too much trouble ill probably try find a wireless adapter thats linux friendly? any suggestions?

---

### Post by beow on 2006-12-28
Of course it is possible, everything is possible with Ubuntu... , it's just a question about the amount of work you're willing to put in ;). Here is a start-point:

[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

There may be a problem if one interface is a wifi interface, but you don't kno until you tried...
In the long run it's probably easier to get a wifi dongle to the desktop, I just installed a netgear wg111v2 (with a lot of effort, even though its suppose to work out of the box).

Good luck!

---

### Post by liamjames91 on 2006-12-28
ok ill try, i actually have a netgear wg111t wifi dongle for the desktop, it worked in dapper but after the upgrade, which was done from a clean install not and online upgrade and it will not work, installed ndiswrapper and ndisgtk, installed both of the .inf files but ndiswrapper crashes when the adapter is plugged in and ubuntu boot up crashes when its plugged in ?? the annoying thing is wireless worked right away on the built in wifi on my laptop which is an intel wireless chipset, ho humm, if only they would release linux drivers! ](*,)

---

### Post by beow on 2006-12-28
Well try to reinstall ndiswrapper/ndisgtk. According to [http://ubuntuforums.org/showthread.php?t=258732](http://ubuntuforums.org/showthread.php?t=258732) it should not be impossible to get it to work and it certainly much more useful than the ethernet bridge approach.

---

### Post by liamjames91 on 2007-01-04
:-D well after long frustration, and alot of forum reading apparently there is something wrong with ndiswrapper in edgy, something to do different versions of something anyway, i have unfortunately, gone back to dapper, and guess what?? that little blue light on my wireless adapter is flashing away once more!! woo hoo!! just thought id let you know!

---

