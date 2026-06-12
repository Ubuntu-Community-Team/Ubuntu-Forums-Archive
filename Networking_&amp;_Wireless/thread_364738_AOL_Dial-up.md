---
title: "AOL Dial-up"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by d2843 on 2007-02-18
I'm using Ubuntu Edgy and loving it, except for the annoying fact that I can't connect to the internet. I am currently enslaved by AOL Dial-up, and I have been unable to connect through Ubuntu. I installed Penggy, but every time I try to use it, it says it cant initialize my modem. I believe my modem is on COM port 3 in Windows. I'm guessing I need some kinda driver, but I cant exactly download the right one, since I can't download anything on the Linux side. I was wondering if I should just try some sorta virtualization or emulation to actually run AOL software in Ubuntu. If so, how do I download the right software and set it up?

Please provide any advice you can, but also try to explain everything thoroughly. I'm very n00bish.

---

### Post by lhtown on 2007-02-19
OK, you have hit a bit of a road bump in Ubuntu. There are some things that work better than you expect, and there are others that are surprisingly bad. Modem support is on the bad side.

The problem is that most modems are super-cheap and don't really do much more than provide a place to plug in the cable. Much of the heavy lifting that is the responsibility of the modem is offloaded to the main processor and is basically emulated using software drivers. The only real benefit is that it allows manufacturers to make "winmodems" quite a bit cheaper than regular modems. There is a real downside to this method even on Windows in that the main processor has to work harder to keep up. With modern processors it isn't too significant though.

For linux developers this has been a real point of frustration since a "real" hardware modem is super-simple to support and a software or winmodem is very difficult although support does exist for a number of them.

Myself, instead of struggling with trying to get my winmodem to work, I just bought a hardware modem from tigerdirect.com. It can still be a bit of a headache figuring it out if it doesn't work at first, but relatively speaking, it is much, much easier.

For more information, you can see:
[http://linmodems.org/](http://linmodems.org/)

All of the above references getting your modem to work. I don't know anything about AOL specifically, but from the sound of things, it sounds like your first problem is with your modem.

---

