---
title: "firefox-bin fix"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by Legeril on 2011-04-19
Has anyone managed to fix this memory leak in firefox-bin? I'm 100% sure that flash is the problem, whenever I play a stupid little game or watch TV online my CPU is viciously and brutally raped. I have looked around the forums and there are one or two topics on this but no fix as far as I can see, so I am pretty sure I'm not the only one having this problem.

I'm using Firefox 3.6.16 if that is of any help

---

### Post by kerry_s on 2011-04-19
Have you tried a different browser?

---

### Post by Legeril on 2011-04-19
I have tried Chrome and Opera before but I never really liked them, I like the add-ons and such in firefox like Ad Blocker and Stylish.

---

### Post by kerry_s on 2011-04-19
Chrome/chromium has both of those, so you'll still have your extensions.
Firefox gets more bloated with each release, if your going to stick with it, then you'll just have to expect more resource use.
It's been that way & is not going to change.

---

### Post by jtarin on 2011-04-19
I've been using [Firefox 4 ]("http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html")without too many addons and it's performed nice enough for me that I have gone back to using it as my primary browser after using Chromium for over a year.

---

### Post by lovinglinux on 2011-04-19
@Legeril

That's not Firefox fault. Is flash fault. It works bad on any browser. Your CPU usage problem has nothing to do with memory leak. When a memory leak happens, the browser starts using more and more memory, even a few gigabytes, which can slow down the system considerably after a few hour of usage.

Your problem is basically due to the fact that flash cannot use xv output, like other video plugins, so it put a lot of stress on the CPU.

You might want to try my [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") extension to install the latest beta and improve flash performance, my [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer") extension to watch YouTube with a different plugin and my [tutorials on flash/firefox optimization]("http://www.webgapps.org/blogs/firefox-tutorials").

> **jtarin said:**
> I've been using [Firefox 4 ]("http://www.webupd8.org/2011/03/install-firefox-4-in-ubuntu-1004-1010.html")without too many addons and it's performed nice enough for me that I have gone back to using it as my primary browser after using Chromium for over a year.

I also have gone back using Firefox (4) after a couple of months using Opera as primary. I run Firefox with usually 60 extensions and don't have problems.

---

### Post by ELMIT on 2011-04-24
I am getting more and more frustrated with Firefox (3.6.16) on Ubuntu 10.10 (AMD/64)!

I have a quad-core cpu, 16 GB RAM (!!!) and top tells me:
102% CPU uand 31% Memory used for Firefox.

The window goes more grey than white. 

Any ideas what I should do to find out the problem in order to fix it?

bye

Ronald

---

### Post by lovinglinux on 2011-04-25
> **ELMIT said:**
> I am getting more and more frustrated with Firefox (3.6.16) on Ubuntu 10.10 (AMD/64)!

I have a quad-core cpu, 16 GB RAM (!!!) and top tells me:
102% CPU uand 31% Memory used for Firefox.

The window goes more grey than white. 

Any ideas what I should do to find out the problem in order to fix it?

bye

Ronald

First, get [Firefox 4]("http://ubuntuforums.org/showthread.php?t=1712247").

We don't have enough information to troubleshoot your particular case. So, I have a few questions:

[LIST]
[*]Does this problem happens when viewing specific web content like flash?

[*]Does this problem happens just a few minutes after starting Firefox or after a couple of hours?

[*]Do you use hibernation and never actually close Firefox?

[*]Do you keep more than 20 tabs open at all times?

[*]How many extensions do you have installed?

[*]Do you use experimental extensions?

[*]Do you use Flashblock extension?

[*]Do you use AdBlock Plus extension?

[*]Do you use NoScript extension?

[*]Have you ever optimized your profile databases?
[/LIST]

---

### Post by ELMIT on 2011-04-25
I started with your first statement, get firefox 4.

Installed, but how do I start it? Where is firefox 4 installed now?

---

### Post by lovinglinux on 2011-04-25
> **ELMIT said:**
> I started with your first statement, get firefox 4.

Installed, but how do I start it? Where is firefox 4 installed now?

If you installed using the mozillateam-firefox-stable ppa, then it will upgrade your current installation.

---

### Post by ikt on 2011-04-25
Has someone recommended flash-aid yet?

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

If not I recommend it first of all, then start doing other things.

---

### Post by ELMIT on 2011-04-25
My mistake, ... I still had 3.6.16 open and so it started another window 3.6.16. After I closed all 3.6.16 windows it upgraded, ...

Thanks!

1st minute impression: faster!

Top says 1.7% memory and 10% CPU

Thank you for your hint.

---

### Post by lovinglinux on 2011-04-25
> **ELMIT said:**
> My mistake, ... I still had 3.6.16 open and so it started another window 3.6.16. After I closed all 3.6.16 windows it upgraded, ...

Thanks!

1st minute impression: faster!

Top says 1.7% memory and 10% CPU

Thank you for your hint.

You are welcome.

---

