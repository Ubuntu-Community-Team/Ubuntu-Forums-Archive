---
title: "Firefox 3.5 for 8.04"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by rvgsd on 2009-07-20
Does anyone know or have an idea about when Firefox 3.5 is gonna be officially available for Ubuntu 8.04 users?

---

### Post by vegetarianshrimp on 2009-07-20
You can download it now: [http://www.mozilla.com/en-US/](http://www.mozilla.com/en-US/)

---

### Post by rvgsd on 2009-07-20
Yeah, I can download and install it manually, but its not available through repositories.

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

```

Hardy and Intrepid*Please check back here in a few days.*
The Ubuntu Mozilla Team is working to make Firefox 3.5 available for older releases

```
Are there any disadvantages of installing FF manually as compared to from a repository?

---

### Post by vegetarianshrimp on 2009-07-20
> **rvgsd said:**
> Yeah, I can download and install it manually, but its not available through repositories.

[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

```

Hardy and Intrepid*Please check back here in a few days.*
The Ubuntu Mozilla Team is working to make Firefox 3.5 available for older releases

```
Are there any disadvantages of installing FF manually as compared to from a repository?
Well, I don't think all apps update themselves, and need a repository to do that. I actually have no idea, so disregard what I just said ;)

here's a way you can install it through launchpad's repositories: [http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html](http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html)

---

### Post by rvgsd on 2009-07-20
Yeah.. I know about that repository. It installs Shireteko which is firefox testing version or something, not the smooth final release. It doesnt support a lot of plugins. 

On the page:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

they say for the daily updates:

[B]Installing from the Mozilla Website (Dangerous)
[/B]
[LIST]
[*]**[B]High difficulty, low safety**: Sharing a Firefox profile between Ubuntu's Firefox 3.0 and Mozilla's Firefox 3.5 might cause problems that will go unnoticed for weeks or months. [/B]
[/LIST]
**Please wait until the Ubuntu Mozilla Team make a stable version of Firefox available for your release. If you can't wait, please use one of the methods described above. If you have to use a Mozilla build of Firefox, see the [guide for installing Mozilla builds]("https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds"). Installing from Mozilla is only recommended for comparing the behaviour of Ubuntu and Mozilla builds (e.g. while tracking down a bug). **


 
Does that mean I should not have 3.0 and 3.5 on the same machine?
Can anyone explain this please?

---

### Post by vegetarianshrimp on 2009-07-20
> **rvgsd said:**
> Yeah.. I know about that repository. It installs Shireteko which is firefox testing version or something, not the smooth final release. It doesnt support a lot of plugins. 

On the page:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

they say for the daily updates:

[B]Installing from the Mozilla Website (Dangerous)
[/B]
[LIST]
[*]**[B]High difficulty, low safety**: Sharing a Firefox profile between Ubuntu's Firefox 3.0 and Mozilla's Firefox 3.5 might cause problems that will go unnoticed for weeks or months. [/B]
[/LIST]
**Please wait until the Ubuntu Mozilla Team make a stable version of Firefox available for your release. If you can't wait, please use one of the methods described above. If you have to use a Mozilla build of Firefox, see the [guide for installing Mozilla builds]("https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds"). Installing from Mozilla is only recommended for comparing the behaviour of Ubuntu and Mozilla builds (e.g. while tracking down a bug). **


 
Does that mean I should not have 3.0 and 3.5 on the same machine?
Can anyone explain this please?
Yes, I think it means that. But don't go uninstalling 3.0. It might still mess it up. I would just wait.

---

### Post by m_ad on 2009-07-20
I was wondering the same thing for other applications. I've been told that installing deb files manually is a bad idea, especially if older version of the package are available in the repos.

I'm using 8.04 still because it works flawless with my system, but some of the newer apps (hello Audacious2) won't install properly. If we use 8.04, I think we're stuck with some older version of software.

---

### Post by vegetarianshrimp on 2009-07-20
> **m_ad said:**
> I was wondering the same thing for other applications. I've been told that installing deb files manually is a bad idea, especially if older version of the package are available in the repos.

I'm using 8.04 still because it works flawless with my system, but some of the newer apps (hello Audacious2) won't install properly. If we use 8.04, I think we're stuck with some older version of software.
It's not just 8.04, its Ubuntu in general. The Ubuntu team does a lot of testing and recoding before putting something in the repos. Fedora, on the other hand, has the newest software, but is more likely to crash because of that.

---

### Post by m_ad on 2009-07-20
I'm not complaining. I like a stable system :)


Sometimes newer software fixes some REALLY annoying bugs though.....

---

### Post by vegetarianshrimp on 2009-07-20
> **m_ad said:**
> I'm not complaining. I like a stable system :)


Sometimes newer software fixes some REALLY annoying bugs though.....
True...

---

### Post by rvgsd on 2009-07-20
Soo..how long would it take for us to get FF 3.5?? Also waiting for VLC 1.0 for Hardy..!

---

### Post by steveneddy on 2009-07-20
This has been covered many, many times already in the forums.

Like all past releases of Firefox (and other software for that matter)

you can install it directly from the website

You can install it with a ppa, which simply means that you tell apt where to get the software and it fetches the software and installs it for you automatically AND keeps you up to date.

My method of choice is to install the ppa:

[Here are the instructions for ppa install.]("http://ubuntumanual.org/posts/183/install-or-upgrade-to-firefox-3-5-rc2-in-ubuntu-karmic-jaunty-intrepid-hardy")

Remember to COPY and PASTE these commands in terminal.


Enjoy!  :popcorn:

---

### Post by rvgsd on 2009-07-20
Yeah, I have read a few of the earlier posts and also I am aware that it can be installed through the nightly builds ppa (unofficial install). 
What I am wondering about is when will FF 3.5 be _officially_ available for 8.04 through the repositories.

---

### Post by steveneddy on 2009-07-20
> **rvgsd said:**
> Yeah, I have read a few of the earlier posts and also I am aware that it can be installed through the nightly builds ppa (unofficial install). 
What I am wondering about is when will FF 3.5 be _officially_ available for 8.04 through the repositories.

no

which is why we need to use the ppa

besides, you get a better build and it compiles on YOUR machine - much better

EDIT:
anything you install outside of the repos will be considered "unofficial" FYI

---

### Post by rvgsd on 2009-07-20
Thanks all for replying to this thread!! I think I am gonna manually install..no waiting :)

---

### Post by steveneddy on 2009-07-20
> **rvgsd said:**
> Thanks all for replying to this thread!! I think I am gonna manually install..no waiting :)

using the ppa immediately installs the software AND keeps it up to date automatically through update manager

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

