---
title: "firefox https won't connect"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by vk3xci on 2010-11-30
OK, this is starting to annoy me... 

Ubuntu 10.10, firefox3.6.12

I can't connect to any site with https, including Add-ons. In the first case I generally get a time-out error, Add-ons gives a pretty terse "Firefox couldn't retrieve Add-ons". I guess the latter is related to the former... an https problem.

Incidentally, Chromium works just fine!

So far I have
enabled ssl v2
enabled cookies
checked settings against a 10.04/FF3.6.12 which does work
torn my hair out
rent my garment...etc

Any more ideas most welcome!

Norm

---

### Post by jtarin on 2010-11-30
[Try this.]("http://support.mozilla.com/en-US/kb/Firefox+cannot+connect+securely+because+the+SSL+protocol+is+disabled")

---

### Post by vk3xci on 2010-11-30
> **jtarin said:**
> [Try this.]("http://support.mozilla.com/en-US/kb/Firefox+cannot+connect+securely+because+the+SSL+protocol+is+disabled")

Thanks, been there but did it over in case I missed something. No Joy. 

You know, I have a feeling I've been here before... can't remember what the cure was :confused:

Norm

---

### Post by xCasualty on 2010-11-30
You should use Chrome instead. It runs a lot faster than FireFox and has addons as well.

Download----> [Here]("http://www.google.com/chrome")

---

### Post by jtarin on 2010-11-30
Swiftfox might be an alternative firefox solution.

[Some solution.]("https://qa.mandriva.com/show_bug.cgi?id=58654")

---

### Post by mikechant on 2010-11-30
Try starting firefox from a terminal and see if you can get any helpful error messages.

---

### Post by vk3xci on 2010-11-30
Solved!!!! thanks to the folk at #ubuntu.au irc.

The problem is in with https and IPv6 :confused:

go to about:config
navigate to network.dns.disableIPv6 and set it to true (double click)

Don't ask me, but it works

---

