---
title: "Remote desktop??"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-12-12
I'm going away for the weekend but I'm currently downloading some large files from work and I want to be able to keep an eye on them from my windows XP netbook. I've seen a couple of guides online but there still a little confusing and there are also some things they don't cover such as that I connect to the Internet through a router and that I have a dynamic IP...so how would I go about this?

thanks In advance!

---

### Post by AndyCooll on 2008-12-12
Though you have a dynamic IP address, in reality this is likely to be more static than you think. It's likely that this will only change if you reboot your router.

What you need to do on your router is use port-forwarding and set it so that all incoming traffic for the particular port required by the application is re-routed to the pc in question.

:cool:

---

### Post by Mucho on 2008-12-12
or you can install hamachi.. and connecting over this..

---

### Post by Jouke74 on 2008-12-12
And I suggest you first go and see your company IT department before trying to break security of the complete company network...

---

### Post by kamitsukai on 2008-12-12
> **Jouke74 said:**
> And I suggest you first go and see your company IT department before trying to break security of the complete company network...

Why would this break security? I'm connecting to my home PC not a company computer

---

### Post by superprash2003 on 2008-12-12
this tutorial should help you get started [http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

---

### Post by kamitsukai on 2008-12-12
> **superprash2003 said:**
> this tutorial should help you get started [http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

Thanks followed that tutorial, but is there anyway to tell if it worked? as I presume I cant connect to it from another PC In the same house?

---

### Post by 2hot6ft2 on 2008-12-12
> **superprash2003 said:**
> this tutorial should help you get started [http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html](http://prash-babu.blogspot.com/2008/06/how-to-remote-control-your-ubuntu.html)

Nice job superprash2003:KS

---

### Post by weezerisrock on 2008-12-12
> **kamitsukai said:**
> Thanks followed that tutorial, but is there anyway to tell if it worked? as I presume I cant connect to it from another PC In the same house?

It should still work from another computer in the same house.  All your computer would be doing is going out to the internet hitting the free domain which would send you back thru your router and to the computer on the other side.

---

### Post by kamitsukai on 2008-12-12
> **weezerisrock said:**
> It should still work from another computer in the same house.  All your computer would be doing is going out to the internet hitting the free domain which would send you back thru your router and to the computer on the other side.

didn't work then...:confused:

---

### Post by bodhi.zazen on 2008-12-12
Take care, VNC connections are insecure. 

I suggest, at a minimum, you tunnel over ssh.

I also suggest you use ssh + screen. You can detach and reattach your screen session and monitor your donlwads this way (use wget or rtorrent).

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)



	[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

---

