---
title: "I've done everything right! Why isn't PlayDeb working?"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by abben on 2010-01-20
I'm using a fully updated Ubuntu 9.04, I have apturl installed, I have installed the playdeb package at playdeb.net. 

So, I think, everything being done right, I might go to the [games section of PlayDeb.net]("http://www.playdeb.net/updates/ubuntu/9.04/") and click the install this now link, to install something. But I don't get the "install now" popup I was hoping for. I don't even get an error message. All I get is new tab that pops up with a url such as:

```
http://www.playdeb.net/install/xboard/4.4.1-1~getdeb1
```

And a blank page.

Before the click...

[IMG]http://imgur.com/rbxL1.png[/IMG]

After the click...

[IMG]http://imgur.com/wR0GA.png[/IMG]

Am I missing something? Do I have to change some sort of firefox setting so I can handle the url properly?

---

### Post by synapsys on 2010-01-20
Maybe it's that game.
Maybe the server's having issues.

Have you been able to successfully install any other games?

---

### Post by thatguruguy on 2010-01-20
When I download something from playdeb's site, I also get a blank page. But apturl pops up separately.

The other thing you can do, if you've installed paydeb's repo into your sources list, is just go into synaptic and install the game straight from there.

---

### Post by abben on 2010-01-20
> **thatguruguy said:**
> When I download something from playdeb's site, I also get a blank page. But apturl pops up separately.

The other thing you can do, if you've installed paydeb's repo into your sources list, is just go into synaptic and install the game straight from there.

Thanks. That worked for xboard. I don't actually want xboard, I just wanted a test case. I really wish I could just click the link on the site.

> Maybe it's that game.
Maybe the server's having issues.

Have you been able to successfully install any other games? 

I wish. From the web site, no game I have tried works, and by now I've tried every game on the first two pages.

---

### Post by abben on 2010-01-20
Is it just a matter of telling firefox (or google-chrome) to call apturl?

When I visit the site in google-chrome, I at least get a popup saying that a url will be opened with the program xdg-open... which does nothing.

---

### Post by thatguruguy on 2010-01-21
Are you using kubuntu?  If so, check out this bug: [https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/476853](https://bugs.launchpad.net/ubuntu/+source/ubufox/+bug/476853)

---

