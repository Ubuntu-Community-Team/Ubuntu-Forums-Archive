---
title: "Web pages loading sowly on Linux, on Windows no such problem"
date: 2021-03-11
forum: Networking &amp; Wireless
---

### Post by lyudmil on 2021-03-11
I have this problem in Linux distros on my laptop HP Probook 450 G5. I'm using Firefox. Tried with Ubuntu, Ubuntu Deepin and KDE Neon - it takes between 10 and 20 seconds to load a website. Then I switched back to Windows 10 just to check and everything was fine. Now I'm on Ubuntu again.

Download speed is not affected.

The problem occurs with the initial loading of the site, then the other pages of the same website are loading faster.

[My hardware spec]("https://i.imgur.com/CN3v4ps.png")

---

### Post by TheFu on 2021-03-11
I'd check for DNS problems.
```
more /etc/resolv.conf
```
Also do you use systemd-resolved or resolvconf or are you allowing network-manager to attempt its stuff?

**inxi -Fz** would be helpful for a system overview.

---

### Post by SeijiSensei on 2021-03-11
Open a terminal and type "host www.google.com".  Does it reply more or less instantly?
```

$ host www.google.com
www.google.com has address 172.217.7.4
www.google.com has IPv6 address 2607:f8b0:4006:800::2004

```

---

### Post by lyudmil on 2021-03-12
> **SeijiSensei said:**
> Open a terminal and type "host www.google.com".  Does it reply more or less instantly?
```

$ host www.google.com
www.google.com has address 172.217.7.4
www.google.com has IPv6 address 2607:f8b0:4006:800::2004

```

It replies in a millisecond.

---

### Post by T6&amp;sfpER35% on 2021-03-12
what browser you use for windows? i'm thinking maybe it's browser related?some setting in FF? 
I don't use FF so not too familiar with it's inner workings.(but i'd guess it should work fine to load websites "out of the box")

---

### Post by T6&amp;sfpER35% on 2021-03-12
> [COLOR=#000000]I'd check for DNS problems[/COLOR] but it does sound like this
maybe try [this](https://geek-university.com/linux/configure-dns-settings/) and see if it helps ?

---

### Post by TheFu on 2021-03-12
> **3nd said:**
> but it does sound like this
maybe try [this](https://geek-university.com/linux/configure-dns-settings/) and see if it helps ?

That configuration method has been deprecated for 2 LTS releases. 

Firefox has changed some things in their networking the last few months. They made DoH default. I know that if ipv6 is disabled in the OS, then some FF internal settings to disable it are required too. Off the top of my head.

Really need to see the dns file already requested, but fast pings of popular sites may or may not be helpful. Could be cached DNS results.

---

### Post by lyudmil on 2021-03-12
Thank you, everyone!

I don't reply to most of the posts here because I'm a n00b and I don't know what all this means.

In Windows and Linux I use Firefox. I just installed the Brave browser and things are perfect so far.

---

### Post by TheFu on 2021-03-12
We we all noobs. if you don't understand and google doesn't explain, ask. Helping you get a solution is why we are here.  
Brave could be a fine solution.

---

### Post by T6&amp;sfpER35% on 2021-03-13
yup i never use FF , only Brave here :guitar:

---

