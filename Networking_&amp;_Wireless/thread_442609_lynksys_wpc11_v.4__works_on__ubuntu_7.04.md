---
title: "lynksys wpc11 v.4  works on  ubuntu 7.04"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by konik134 on 2007-05-13
hi people dont know this hapend to someone else but i got finally make my wirelles card "linksys wpc11 v.4" to work under under ubuntu 7.04 . after  removing  complletly network manager  using  latest ndiswrapper and driver net8180.inf and searching ubuntu forums i figerout how to do it  im using "mint linux "whit latest upgrade to 7.04 .  ok if someone need help just ask  :) :) :)

---

### Post by wavz on 2007-05-13
I would like to know how you did this. Im using Knetworkmanager and it drops out almost every minute. So if you could describe how you did your computer It would help alot of people out with this problem.

                                                                                                      Wavz

---

### Post by konik134 on 2007-05-13
as u can read in my post up first what i did is to uninstall network manager in your case is knetworkmanager then install latest ndiswrapper  then find to download driver which is for this card "net8180.inf" wish that i have the link to provide but all of these things i find here on forum just spend some time searching  then add ndiswrapper and driver r818x  to module list in terminal  gedit /etc/modules  ok then  also in terminal open sudo gedit /etc/network/interfaces put this ( # ) on the front all networks but no for  io  then go to system/administration open networking  click on wirelles to configurate now is the trick  found this here on forum thanks to to guy  when u tiping name of you network  in my case is linksys  just put (x)on the end of the name as u can se from screnshot  if is wep protected do your key  and lived on dhcp  then do this in the terminal /etc/init.d/networking restart  after that restart computer  tats all    let me know

---

### Post by konik134 on 2007-05-13
[http://ubuntuforums.org/attachment.php?attachmentid=3976&d=1133292079](http://ubuntuforums.org/attachment.php?attachmentid=3976&d=1133292079) 

[http://ubuntuforums.org/showthread.php?t=420161&highlight=linksys+wpc11+v.4](http://ubuntuforums.org/showthread.php?t=420161&highlight=linksys+wpc11+v.4)

first link is for driver dovnload  and extract to desktop

---

