---
title: "Still trying to get Sprint air card to work"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-08-17
Hello,

Very new to Linux, not much computer experience anyway, been trying to get my Sprint card to connect.

I have Ubuntu 9.04 installed, I can use it to get on line if I put the card in my router and use a cable, but I have not been able to connect using the card in the laptop.

I followed the instructions in the Sprint Mobile Broadband Set Up Guide.

I get all the way to where it says "logging on" but it just sits there and never connects.

I have went back over it several times, everything seems set the way it says to in the guide, I do not know what to try next.

Any help will be appreciated.

Thanks

---

### Post by dlmarti on 2009-08-17
I have no knowledge of the card or the service, but a quick search on google for : "linux sprint air card" came up with a lot of positive posts and a few howto's

---

### Post by barnaclebill18 on 2009-08-17
> **dlmarti said:**
> I have no knowledge of the card or the service, but a quick search on google for : "linux sprint air card" came up with a lot of positive posts and a few howto's

Thanks for the reply.

I have been using Google but it seems most people asking questions like mine do not get their problem solved, also most of the solutions I have been reading about are way over my head, most of the time I really don't know what they are talking about and I could not follow those instructions.

Hey, I'm 67 years old and never touched a computer until a few years ago, the first one I ever used had XP, I got to learn that pretty good and now I am trying to learn Ubuntu, but it is tough, I need explicit instructions.

That is why I put this post in the absolute beginner section.

Anyway, I don't know what to try next, thanks for any help.

---

### Post by dlmarti on 2009-08-17
I'd love to help more, unfortunately I have no experience with the card.

Do any of these links help?
[http://ubuntuforums.org/showthread.php?p=2606060#post2606060](http://ubuntuforums.org/showthread.php?p=2606060#post2606060)
[http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/](http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/)
[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC80VzY4UUVGag==/sno/0](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC80VzY4UUVGag==/sno/0)

From what I gather the card is some sort of custom serial device, and you need to load a driver for it to work (apparently their is a linux driver for it).

After the driver is loaded you need to get ppp to use the serial device to connect.

One of the links is from this forum, maybe you could priv-message the guy that did get it to work and steal his setup.

kudos to you for trying, in anycase, I love when people get outside their comfort zone and actually try new things.  If there is anything more generic I can help with, just mail me.

---

### Post by barnaclebill18 on 2009-08-17
[QUOTE=dlmarti;7803621]I'd love to help more, unfortunately I have no experience with the card.

Do any of these links help?
[http://ubuntuforums.org/showthread.php?p=2606060#post2606060](http://ubuntuforums.org/showthread.php?p=2606060#post2606060)
[http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/](http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/)
[http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC80VzY4UUVGag==/sno/0](http://sierrawireless.custhelp.com/app/answers/detail/a_id/500/session/L3NpZC80VzY4UUVGag==/sno/0)

From what I gather the card is some sort of custom serial device, and you need to load a driver for it to work (apparently their is a linux driver for it).

After the driver is loaded you need to get ppp to use the serial device to connect.

Hello,

I'm pretty sure I have all the drivers and the ppp is recognizing the card, because the first couple of tries I had wrong,it would not work at all, but now it is trying to connect.

I will check out those links.

Thanks

---

