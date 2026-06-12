---
title: "Jaunty problem with ATI Display Adapter"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by bleyz on 2009-07-26
I've just installed Jaunty few days ago and it doesn't seem to be getting along well with my ATI HD2600 Pro Display Adapter. I've recently asked the question [here]("http://ubuntuforums.org/showthread.php?t=1221536"), though I couldn't get a proper answer to fix my question. So I've decided to try my chance here. 

When I've been installed Jaunty on my computer, installation process worked like a charm. Though things have changed when the Jaunty starts for the first time. Computer was slow to crawl at the beginning, which was the same with my notebook computer with integrated Nvidia gpu. That notebook worked great when I installed video drivers from Nvidia, so I tried to do same thing and installed the latest driver for my HD2600 Pro from the section called "Hardware Drivers". The result was disappearing top panel and a nonfunctional problem. Then I've made some research on net and read some people succeed with installing the driver from ATI website. I've just tried the same thing, though with no luck. I've made some serious search in forums, though I couldn't find an exact solution for my problem

---

### Post by alphacrucis2 on 2009-07-26
> **bleyz said:**
> I've just installed Jaunty few days ago and it doesn't seem to be getting along well with my ATI HD2600 Pro Display Adapter. I've recently asked the question [here]("http://ubuntuforums.org/showthread.php?t=1221536"), though I couldn't get a proper answer to fix my question. So I've decided to try my chance here. 

When I've been installed Jaunty on my computer, installation process worked like a charm. Though things have changed when the Jaunty starts for the first time. Computer was slow to crawl at the beginning, which was the same with my notebook computer with integrated Nvidia gpu. That notebook worked great when I installed video drivers from Nvidia, so I tried to do same thing and installed the latest driver for my HD2600 Pro from the section called "Hardware Drivers". The result was disappearing top panel and a nonfunctional problem. Then I've made some research on net and read some people succeed with installing the driver from ATI website. I've just tried the same thing, though with no luck. I've made some serious search in forums, though I couldn't find an exact solution for my problem

I always install the latest Catalyst driver from ATI. After you downloaded and installed it, did you remember to issue this command before rebooting:

```
sudo aticonfig --initial
```

---

### Post by bleyz on 2009-07-26
I've made a fresh install of the whole Ubuntu again and tried the steps that you mentioned. Resolution and other things seemed to be working fine, though an odd thing happened when I tried to open Firefox. Firefox disappeared with the top panel. When I press Alt + Tab I can see it for a moment and then it disappears again. It is open, put I can't access it. Same thing happened for terminal. What can I do about this?

---

### Post by QIII on 2009-07-26
Try starting Firefox from the terminal and see how it behaves.  You may get the same behvavior, but that might jog someone's memory after you post what happens.

DO NOT USE sudo FOR THIS.  DO NOT USE sudo FOR THIS.  DO NOT USE sudo FOR THIS.
Using sudo will cause some of the supporting files in your profile folder, like bookmarks, to be available only using sudo from then on, unless you chmod them.

For FF3.0.x

```
firefox
```

For FF3.5

```
firefox-3.5
```

---

### Post by bleyz on 2009-07-26
Thanks for your advice dude, but it doesn't seem to be possible to access terminal too. It behaves just like Firefox, like every other program on the system.

---

### Post by QIII on 2009-07-26
Aw, crud!

I read that and forgot.  Getting old and forgetful.  Can I blame this on my bifocals?  No?  My wife rarely goes for that excuse, either.

Kinda hard to use the terminal if you can't use the terminal!

OK.  Stand by.  I'll do a little research.  I think I've seen similar things in the past...

---

### Post by QIII on 2009-07-26
Do you have a Window List on your Gnome Panel?

If not, add one and see if the windows that minimize show up there.

---

### Post by bleyz on 2009-07-27
Sorry for the late answer, I was extremely busy today :( . I've just made a fresh install and tried to install the newest driver from ATI website and guess what: it worked. Though I don't understand why it didn't work the last time, but I won't complain much about that :). Thanks for all your help dude, I'm really thankful about that :popcorn:

---

