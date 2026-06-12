---
title: "Ice weasel for Natty?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by comsparks on 2011-05-10
The firefox 4 is very slow and have uninstalled it. I'm using Chromium which is very fast. I want to use the add on Reminder Fox which works with Firefox and ice weasel but doesn't seem to be supported for Chromium. I've tried to download and install ice weasel using the apt-get command but it keeps coming back saying that it will use firefox vice ice weasel. I wanted to check to see if ice weasel works any faster than FF4. Is there a way to install ice weasel for Natty. Thanks.

P.S. my system does not support Plymouth so Ubuntu has reverted back to Classic mode.

---

### Post by earthpigg on 2011-05-10
Hi,

iceweasel is just firefox without the firefox branding. it should do everything just as well as firefox, and fail in the exact same ways that firefox does.

---

### Post by An Sanct on 2011-05-10
Install it with terminal
```

sudo apt-get update
sudo apt-get install iceweasel

```Anyway, Iceweasel is a flavor of Firefox, I see no reason, why it should run faster the Firefox.

---

### Post by comsparks on 2011-05-10
Yes I know about the FF4 and IW relationship but was curios to see if it could be done. The Apt-Get only will download and install Firefox and not Iceweasel. Thanks all.

---

### Post by lovinglinux on 2011-05-10
Please be more specific about what do you think is slow in Firefox. Startup? Page loading? Switching tabs? Searching bookmarks?

Firefox is very fast, but it can be optimized. Just let me know so I can assist you.

I don't think installing Iceweasel will make any difference.

---

### Post by bodhi.zazen on 2011-05-10
iceweasel is a Debian package. You could try using the .deb from debian.

On Ubuntu you can use icecat.

[https://launchpad.net/~gnuzilla-team/+archive/ppa](https://launchpad.net/~gnuzilla-team/+archive/ppa)

---

### Post by bodhi.zazen on 2011-05-10
> **lovinglinux said:**
> I don't think installing Iceweasel will make any difference.

+1 to that general advice.

---

### Post by comsparks on 2011-05-10
I tried that IceCat and yes same results. The slowness is really evident on the Yahoo web page. I have to wait up to 15 seconds for whatever I click on to respond. That includes scrolling, anything. I switch over to Chromium and it screams through it. Any ideas? Thanks.

---

### Post by lovinglinux on 2011-05-10
> **comsparks said:**
> I tried that IceCat and yes same results. The slowness is really evident on the Yahoo web page. I have to wait up to 15 seconds for whatever I click on to respond. That includes scrolling, anything. I switch over to Chromium and it screams through it. Any ideas? Thanks.

The page does not take long to load the content, but the browser kind of freeze? Or the content itself appears slowly like dial-up?

Looks to me that is a video driver issue. Make sure you have the latest driver installed and make sure smooth scrolling is not selected in Firefox advanced settings.

Just to make sure, start Firefox in safe mode and report if the problem persists.

```
firefox -safe-mode
```

If the pages are loading slowly, disable ipv6 and enable pipelining. For instructions see [http://www.webgapps.org/firefox/preferences-tweaks](http://www.webgapps.org/firefox/preferences-tweaks)

---

### Post by comsparks on 2011-05-11
I has to do with Ubuntu on my machine I guess. I installed Debian Squeeze and Iceweasel, Firefox etc. runs fast no problems. Actually the entire OS runs much faster. Anyway thanks for all the help. I guess they can remove this thread as I will not be using Ubuntu any longer. Thanks again.

---

