---
title: "wicd  Has anyone tried it with Heron"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by David1000 on 2008-07-30
I am running Hardy Heron and have tried wicd several times but it does not install correctly.  Has anyone tried it successfully?  Lots of stuff on the net about it but as far as I can tell, not from people using Heron.

---

### Post by ModelM on 2008-07-30
I'm using wicd with 8.04 (32 bit) & had no problems installing or using it. I installed it by adding the wicd repositories to synaptic package manager & selecting wicd from the programs list after reloading.

---

### Post by jimv on 2008-07-30
When you say that it does not install correctly, could you be more exact?  Are you getting an error message during the install?  After the install?  What does the error say?

---

### Post by kamiokande on 2008-08-01
I've been using it since I've upgraded to 8.04 from 7.10, and it works well for the most part, but I have encountered some occasional problems.

For instance, sometimes the tray icon will freeze while indicating 'No Connection', whereas my wireless still works fine. This never happened in 7.10, and I'm not sure what the cause is. It still seems to connect to networks at the same signal quality, it's just that the icon/gui sometimes doesn't work.

---

### Post by imdano on 2008-08-01
Plenty of people are using in Hardy with no issues.  What error are you getting?

---

### Post by mrsudo on 2008-08-02
the only problem i have is the tray icon like kamiokande but other than that it works great.  the wireless adapter i have will just not let me use networkmanager...

---

### Post by imdano on 2008-08-02
It sounds like you might be seeing a 1.4.2 bug.  Give the next release, 1.5.0, a shot.  It's still only a release candidate now, but we expect to make the official release this weekend.

---

### Post by David1000 on 2008-08-02
Thats great news!  I'll look forward to it but as I am going away for a week, it will have to wait.

I had another go at installing wicd before I saw the last post, and it failed to install; but it did remove the existing network manager (hence I had to reinstall Heron to get it back).

Error message was:

"The Network Manager applet could not find some required resources.  It can not continue"

---

### Post by David1000 on 2008-08-17
Any update on when v1.5 is going to be released?   My Synaptic Package tells me that the latest version is still 1.4.2.1

---

### Post by imdano on 2008-08-17
It already has been released, it's just not in the apt repository yet.  You can download the .deb from [http://www.wicd.net/latest](http://www.wicd.net/latest).  Check out [http://www.wicd.net/latest/changes](http://www.wicd.net/latest/changes) for info on what's new/different.

---

