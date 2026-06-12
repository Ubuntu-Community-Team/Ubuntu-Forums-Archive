---
title: "Minor issue with panels moving"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by Moonfire on 2009-05-26
[FONT=Comic Sans MS]Hello all!

I'm rather new to the whole Linux thing, haven't had it installed for a full week yet.  Well, the total probably is - I had it installed a month or two back, but had to abort for the time being because I was spending too much time messing with it rather than working on school work *whistles innocently*.

Anyway, I set up the two panels that the install starts with on the bottom, with the one that has the Applications/Places/System/ect stuff on the very bottom and the one that has all my applications and such right above it.  However, when I restart, these panels switch places (the taskbar-like one now on the bottom).  It's easily fixed by right-clicking the Applications/ect bar, moving it to the Top and then the Bottom again, but it is a bit of an annoyance.  The usual fix of "If it moves and it's not supposed to, use Duct Tape" probably won't work in this case. :P

Thanks ahead of time for your help!

Edit: Gah, knew I'd forget to say it.  Currently using Ubuntu 9.04.
[/FONT]

---

### Post by Didius Falco on 2009-05-26
> **Moonfire said:**
> [FONT=Comic Sans MS]Hello all!

I'm rather new to the whole Linux thing, haven't had it installed for a full week yet.  Well, the total probably is - I had it installed a month or two back, but had to abort for the time being because I was spending too much time messing with it rather than working on school work *whistles innocently*.

Anyway, I set up the two panels that the install starts with on the bottom, with the one that has the Applications/Places/System/ect stuff on the very bottom and the one that has all my applications and such right above it.  However, when I restart, these panels switch places (the taskbar-like one now on the bottom).  It's easily fixed by right-clicking the Applications/ect bar, moving it to the Top and then the Bottom again, but it is a bit of an annoyance.  The usual fix of "If it moves and it's not supposed to, use Duct Tape" probably won't work in this case. :P

Thanks ahead of time for your help!

Edit: Gah, knew I'd forget to say it.  Currently using Ubuntu 9.04.
[/FONT]

Welcome to the Ubuntu forums!

Let's see if we can't get out a roll of virtual duct tape for you:

1. Arrange panels the way you want them to stay.

2. Press Alt+F2

3. Type **gconf-editor** in the little window that has opened.

4. Go to **Apps/Panel/Global** in **Configuration Editor** and tick the little box next to **locked_down**

5. Close Virtual Duct Tape roll  aka **Configuration Editor**.

6. Enjoy your locked down panels!!

Regards,

Didius

---

### Post by Moonfire on 2009-05-26
[FONT=Comic Sans MS]Aha, got it!  Thanks for the response, I appreciate it ^^.

Edit: Alright, after a reset, the panels still switched places.  And a shortcut to a game disappeared - not sure if that's related or not, though.  Any ideas?
[/FONT]

---

### Post by AmJaD on 2009-06-25
Hi

I recently got Ubuntu 9.04 a couple of days ago and had the same problem every time I restarted or logged back it.

Its been a while since you posted this so you probably have it setup already but if you don't, try this:

1. Press Alt+F2 to open the "Run Application" window
2. Type "gconf-editor" and click on Run
3. In the configuration Editor window navigate to apps/panel/default_setup/general
4. Double-click on "toplevel_id_list"
5. In the "Edit Key" window under Value swap the position of the "top_panel" or "bottom_panel" by selecting either one of them and clicking either up or down


Now the panels are how I want them and it was really easy to configure

---

### Post by louieb on 2009-06-29
> **AmJaD said:**
> ...so you probably have it setup already but if you don't, try this:


I had the same issue. The solution you gave solved it - Thank you.

---

