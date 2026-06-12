---
title: "Can't Watch Streaming video from this site."
date: 2011-06-09
forum: New to Ubuntu
---

### Post by suomalainen on 2011-06-09
Ubunteros,

When I visit:

[http://www.quicksilverscreen.im/](http://www.quicksilverscreen.im/)

I cannot watch or download any movies/streams. Anyone got an idea what the deal is exactly? Or they just don't like Linux?

Thanks!

---

### Post by hakermania on 2011-06-09
I get
```
This streaming server is currently in maintenance mode.
please try again later.
```
If this is what you get too, then the error message is clear

---

### Post by suomalainen on 2011-06-09
Thanks for your reply.

No I get this message. See attached pic.....

Maybe the site is set to screw with Windows machines?

---

### Post by TeoBigusGeekus on 2011-06-09
I did this.
Opened the site with Opera.
Right click->Edit site preferences->Network->Browser Identification->Identify as Internet Explorer
Reloaded the page.
Conan o' Brien and Thor started playing normally; Xmen first class complained about missing plug in.
In all three cases, when I tried downloading the video I got the same message you get.
If you want to download the flv, see my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

---

### Post by beew on 2011-06-12
> **TeoBigusGeekus said:**
> I did this.
Opened the site with Opera.
Right click->Edit site preferences->Network->Browser Identification->Identify as Internet Explorer
Reloaded the page.
Conan o' Brien and Thor started playing normally; Xmen first class complained about missing plug in.
In all three cases, when I tried downloading the video I got the same message you get.
If you want to download the flv, see my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread.

Streaming in flash works in both FF and Opera (no need for switching user agent). 

Strange that Dvix streaming works in Opera but not in Firefox (both use the gecko-mediaplayer plugin). Attached screenshot shows what it looks like in Firefox.

Download works if you pretend to be using internet explorer (and in Firefox has to disable adblock) But then the download is something called eMulesetup.exe which will supposedly setup eMule to download the actual file from torrent. It appears to be a Windows virus
[http://www.virus-com.com/viruscom/viruscom_104658.html]("http://www.virus-com.com/viruscom/viruscom_104658.html")

---

### Post by beew on 2011-06-14
Ok, DIVX streaming in Firefox works as well provided flashblock is disabled.

---

