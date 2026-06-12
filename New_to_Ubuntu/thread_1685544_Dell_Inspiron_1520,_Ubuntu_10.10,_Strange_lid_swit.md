---
title: "Dell Inspiron 1520, Ubuntu 10.10, Strange lid switch behavior"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-02-10
Hi all. I've been experiencing some strange behavior with Ubuntu 10.10 on my Dell Inspiron 1520. If I boot up without the power cable connected, the screen goes blank and stays blank the way it should. However, if I then connect the power cable, or boot with it connected, the screen goes blank for about two seconds, then comes back on, backlight and all. Only a restart without the power connected puts everything back in order.

I've ruled out extraneous mouse input. I even did a fresh install on an external disk. No update thus far has fixed anything, and I don't feel like breaking everything by enabling proposed or backported updates. . .

It seems like I see some lid switch bug of some sort about every other release or so with this laptop, just bad hardware luck I suppose. I've searched everywhere, and I can't seem to find this bug reported anywhere; I just figured I'd ask here before filing a new report.

Has anyone else experienced behavior like this?

Sorry if it takes me a bit to respond, I'm learning Dvorak :P

---

### Post by pi.boy.travis on 2011-02-10
I solved it. It was not connecting the power that caused it, it was an iPod touch connected to a USB hub that I habitually connected along with the power cable every time I set my laptop back at my desk. The iPod has the latest software, so it can't be mounted by the current stable Linux kernel in Ubuntu. This puts DBus in a tizzy, as I can tell from it's log, so much so that it began to misinterpret lid switch events.

---

