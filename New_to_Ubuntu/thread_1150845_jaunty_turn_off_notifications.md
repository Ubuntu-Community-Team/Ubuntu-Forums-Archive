---
title: "jaunty turn off notifications"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by omkarwagh on 2009-05-06
i recently upgraded to jaunty and have the following two issues:-

1.if there are updates available, the damn update manager opens up by itself every few minutes. this is a highly irritating feature especially when one is working. how does one turn it off? none of the previous versions of ubuntu have this problem.

2.notifications:- i use pidgin for all of my IM needs. but unfortunately jaunty seems to assume that every contact signing in/out , message being recieved etc. is an extremely important event that deserves my undivided attention immediately. 
however, i beg to differ and wish to know how to turn this off. again, this problem was not encountered anywhere in the previous versions of ubuntu.

thanks in advance.

p.s.:- i do hope the ubuntu developers actually take some time out to think before wasting time implementing such obviously detrimental and rather useless features.

---

### Post by mcduck on 2009-05-06
To change the update manager back to old behavior (displaying notification icon when updates are available instead of opening the Update manager) open gconf-editor and turn off update-manager/auto_launch.

For Pidgin notifications you can configure what notifications to display in Pidgin's "Libnotify Popups"-plugin's settings. Go to Tools/Plugins, find the Libnotify plugin and click the "Configure Plugin"-button.

---

### Post by omkarwagh on 2009-05-06
thanks

---

### Post by durand on 2009-05-06
> **omkarwagh said:**
>  
p.s.:- i do hope the ubuntu developers actually take some time out to think before wasting time implementing such obviously detrimental and rather useless features.

What's useless to you may be useful to someone else. I definitely prefer having buddy list notifications and the new update manager encourages people to update more often. It should only pop up every 10 days or so unless you haven't updated.

---

### Post by LowSky on 2009-05-06
> **omkarwagh said:**
> 
p.s.:- i do hope the ubuntu developers actually take some time out to think before wasting time implementing such obviously detrimental and rather useless features.


I hope you take the time to think and realize you are using an operating system which cost you nothing. And thos said developers implement changes that the community may have asked for. So unless you can build and maintain your own linux distro, don't complain, these guys are trying to make a piece of art out of zeros and ones. compared to Ubuntu version 5.10, Version 9.04 is much more advanced and user friendly.

---

### Post by mick8985 on 2009-05-06
> **LowSky said:**
> I hope you take the time to think and realize you are using an operating system which cost you nothing. And thos said developers implement changes that the community may have asked for. So unless you can build and maintain your own linux distro, don't complain, these guys are trying to make a piece of art out of zeros and ones. compared to Ubuntu version 5.10, Version 9.04 is much more advanced and user friendly.

This implies that because Ubuntu is free you shouldn't have any complaints about its quality, that's rubbish and demeaning to open source software. With that attitude your promoting the idea that linux is of inferior quality and it is expected to always be that way.
The OP is guilty of shooting his mouth off before he investigated the situation (that the notification system doesn't actually show more notifications than the previous one, and that individual apps decide how often notifications are given), but if he has a genuine grievance he should be able to complain but in a constructive manner, and not just put up and shut up.

---

### Post by mister_pink on 2009-05-06
I must admit I find the new update manager thing incredibly annoying as well. Whilst I like the look of the new notifications system, I think the whole philosophy behind it is flawed. They started with the premise that notifications should be just information that requires no action. I'd argue the exact opposite, if it requires no action then why on earth am I being told?

---

### Post by durand on 2009-05-06
> **mister_pink said:**
> I must admit I find the new update manager thing incredibly annoying as well. Whilst I like the look of the new notifications system, I think the whole philosophy behind it is flawed. They started with the premise that notifications should be just information that requires no action. I'd argue the exact opposite, if it requires no action then why on earth am I being told?

You may want to know who just signed on or if your laptop battery is low?
I think what they mean by it requiring no action is that you can completely ignore it and just get on with your work. If you move over it, you can still access everything under it. They do need to implement some sort of dismiss function though...

---

### Post by phantom3113 on 2009-05-06
> **LowSky said:**
> I hope you take the time to think and realize you are using an operating system which cost you nothing. And thos said developers implement changes that the community may have asked for. So unless you can build and maintain your own linux distro, don't complain, these guys are trying to make a piece of art out of zeros and ones. compared to Ubuntu version 5.10, Version 9.04 is much more advanced and user friendly.

I would have to agree with LowSky here. I agree some features may be useless to the general public, but there are those that find such features beneficial. So go easy on the developers, especially if your issue is an easily solved one, and aesthetic at that.

---

