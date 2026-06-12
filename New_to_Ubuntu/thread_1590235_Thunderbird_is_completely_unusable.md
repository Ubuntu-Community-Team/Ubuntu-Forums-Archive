---
title: "Thunderbird is completely unusable"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by veterankamikaze on 2010-10-07
I've been playing with Ubuntu for a few weeks and have been struggling with using Thunderbird. Can anyone explain why Thunderbird would exhibit the behavior shown in the screenshot?

I've tried purging and reinstalling with the same result. This happens on launch and never resolves to make Thunderbird usable.

---

### Post by TeoBigusGeekus on 2010-10-07
Try deleting the .thunderbird folder in your /home partition, then purge and reinstall.

---

### Post by veterankamikaze on 2010-10-07
I've tried that as well with the same result. As far as I've been able to tell, Thunderbird is the only app with this problem.

---

### Post by slooksterpsv on 2010-10-07
> **veterankamikaze said:**
> I've tried that as well with the same result. As far as I've been able to tell, Thunderbird is the only app with this problem.

Consider using Evolution? It's a lot better than Thunderbird in my opinion as you can use calendar, tasks, etc. (It's like Outlook but Free and Open Source) Other than that, I would run thunderbird from a terminal and see if/what errors it outputs when running it.

---

### Post by andrewthomas on 2010-10-07
Do you have desktop effects enabled?  

Is the problem with the opacity of the windows?

---

### Post by veterankamikaze on 2010-10-07
> **slooksterpsv said:**
> Consider using Evolution? It's a lot better than Thunderbird in my opinion as you can use calendar, tasks, etc. (It's like Outlook but Free and Open Source) Other than that, I would run thunderbird from a terminal and see if/what errors it outputs when running it.

That's not very helpful. I tried using Evolution as that's what is installed with Ubuntu by default and found that I didn't like it. I made a decision to use Thunderbird (as I do for personal email on all of my other machines) and am having this issue.

> **andrewthomas said:**
> Do you have desktop effects enabled?  

Is the problem with the opacity of the windows?

I've turned desktop effects off and still have odd rendering issues. Interestingly, if I attempt to resize the "Mail Account Setup" window, I will eventually see some input fields and Cancel/Continue buttons. However, even after muddling my way through with that, Thunderbird isn't usable due to those weird rendering issues.

---

### Post by andrewthomas on 2010-10-07
Have you tried the version from this ppa?

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

I use it (I don't update it daily, just once every couple of weeks.)

---

### Post by jtarin on 2010-10-07
Boot to failsafe Gnome and try.

---

### Post by redbook4574 on 2010-10-07
You probably don't want to hear this but I would cut my losses and try a fresh install from scratch. Ubuntu like anything else can be a proper git to find a simple error and re-install is often quicker.

---

### Post by MartyBuntu on 2010-10-07
I had the same problem. I installed Compiz and it went away...I was able to finally use Thunderbird.

It sounds strange, but it worked for me.
This only happened on my Dell Inspiron 5100 laptop with ATI Radeon graphics card.

---

### Post by veterankamikaze on 2010-10-08
> **andrewthomas said:**
> Have you tried the version from this ppa?

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

I use it (I don't update it daily, just once every couple of weeks.)

This appears to have resolved the issue! I could have sworn I tries this a few weeks ago with no luck. Thunderbird is now generally usable now, though not as smooth as I would expect. I'll chalk that up to the specs of the machine (poor little netbook).

Thanks so much for the help. I'm now one step closer to Ubuntu being my primary platform on this machine.

---

