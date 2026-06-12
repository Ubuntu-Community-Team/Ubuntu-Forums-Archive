---
title: "Headache: No sleep or hibernate AcerOne 10.04"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by JasonBa on 2010-05-05
Hi there, 

I'm a noob, I'll admit, to ubuntu.
But I'm pretty sure I installed everything correctly, and have a fairly sound setup (looking forward to no more viruses!).

My Acer One has a problem though,

When I close the lid, or manually put it to sleep the drives spin down, but everything else stays running (screen, fans, etc). Once it's like this it is not possible to bring the computer back out of the state, requiring a forced shutdown and restart.

When I choose to hibernate, the power is cut off before the drives manage to spin down (making that nasty noise they do when you know you're killing them before they're ready to turn off) and the whole system shuts down - it doesn't hibernate.

In both cases, it forces a disk check when started back up again.

I read this as being a problem in v7, but hoped I wouldn't face this with v10!


As I said, it's an AcerOne. I've been running Win7 on there fine, but wanted something lighter and faster. If it did work correctly for sleep and hibernate it'd be the perfect system.


Can anyone help me with this please?
Many thanks
Jason

+_)(*&^%$#@!+_)(*&^%$#@!!@#$%^&*()_+!@#$%^&*()_+

I would also like to know if it's possible to enable backspace for going back a page in FF / Chromium. But that's less important :)

---

### Post by shebaw on 2010-05-05
What version of ubuntu are you running
And for your second question read this,
[http://www.mydigitallife.info/2008/06/22/disable-or-enable-backspace-as-go-back-page-browsing-function-in-firefox/](http://www.mydigitallife.info/2008/06/22/disable-or-enable-backspace-as-go-back-page-browsing-function-in-firefox/)

It's possible to do it on firefox atleast, I'm not sure about Chromium.

---

### Post by JasonBa on 2010-05-05
Hi, 

Version 10.04 as I state in the title. It's just been released (april 29) Lucid Linux? 

Thanks for the link!

---

### Post by madjr on 2010-05-05
first disable the suspend and hibernate

go to power management or click on the battery

when you close it just use blank screen.


also make it that when you hold the power button it shuts down.

that way you just hit it once and shutsdown normally, no need to force shutdown


here is the bug report:

[https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/424877)

you should confirm it with a message for your aspire one (exact model)

---

### Post by JasonBa on 2010-05-05
Thanks for your message, so it's still a bug and at the moment I can't do anything for it? :( - I looked on the bug page, but my model has already been confirmed as defective unfortunately.

---

### Post by JasonBa on 2010-05-05
Oh, I also installed Ubuntu Studio desktop package, thinking it was a graphics program. Now it's changed my theme (got that back though) start-up splash screen and login sound.

Is there a "button" I can click to take this back to a default install?

---

### Post by madjr on 2010-05-05
> **JasonBa said:**
> Thanks for your message, so it's still a bug and at the moment I can't do anything for it? :( - I looked on the bug page, but my model has already been confirmed as defective unfortunately.

are you using sd card while suspending?

---

### Post by JasonBa on 2010-05-05
I *was*.. i took it out after reading the bug report and it's now doing it. One of the comments said it was only temporary though, so I'm hoping there will be a fix shortly!

---

