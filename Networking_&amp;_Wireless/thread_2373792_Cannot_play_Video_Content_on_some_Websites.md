---
title: "Cannot play Video Content on some Websites"
date: 2017-10-09
forum: Networking &amp; Wireless
---

### Post by itguy2432 on 2017-10-09
Hello,

Fresh installation of Ubuntu 16.04.3 on Acer Aspire S7 notebook, hardwired connection, using Chrome and Firefox. Today, previously working sites such as Velocity ([https://www.velocity.com/tv-shows/wheeler-dealers/](https://www.velocity.com/tv-shows/wheeler-dealers/)) stopped loading correctly and playing content. "Sign in with TV Provider" dialog does not display TV providers either. Works fine on VMWare Windows 7 guest running on Ubuntu host. Flash is up to date. I have tried changing MTU, spoofing user agent, using Google's DNS, disabling firewall. Any ideas welcome.

---

### Post by carl4926 on 2017-10-10
It works fine
Chrome doesn't even use flash (exactly)

---

### Post by Autodave on 2017-10-10
You may be in between Firefox updates: several people had that problem last week.  Let's make sure that your system is up to date:

In a terminal, type
sudo apt-get update
sudo apt-get upgrade

When that is done, reboot and see if your browsers are working.

---

### Post by itguy2432 on 2017-10-10
Thank you for the suggestions. carl4926: Flash up to date for FF and Chrome. Does the site work for you? Both my Linux boxes do not load the page correctly. Autodave: I should have mentioned in my original post everything is updated. I have also tried the other preliminary stuff like clearing cache and history, multiple reboots.

Let's focus on Chrome, which was working fine for literally years until this weekend. IIRC, FF doesn't like Hulu (or maybe Hulu doesn't like FF), hence Chrome.

Also: Ad Block is disabled, and my hosts file is reverted to original form, no home re-routs. Ran some traceroutes on Windows and Linux, lot's of timeouts on both, I don't think helpful, but I could be wrong. 

Any help appreciated.

---

### Post by itguy2432 on 2017-10-11
bump

---

### Post by itguy2432 on 2017-10-11
In previous post I said Flash was up to date in Chrome and FF. I meant to say both are updated, and Flash is enabled and not blocked in Chrome. I even tried adding an exception to not ask and simply run Flash on the site in question, but no luck. Any help greatly appreciated.

---

### Post by itguy2432 on 2017-10-14
Bump.

---

### Post by praseodym on 2017-10-15
DRM problem?

[http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10](http://www.omgubuntu.co.uk/2013/10/fixing-amazon-prime-streaming-drm-protected-flash-13-10)

---

### Post by itguy2432 on 2017-11-07
I'll give that a shot, although I can watch videos on Amazon, but am optimistic. Thank you for the suggestion.

---

### Post by again? on 2017-11-07
Try installing the non-free codecs needed for some html5 playback.
```
sudo apt install oxideqt-codecs-extra
```
> This package provides some media codecs needed for the HTML5 <audio> and
<video> tags. Included are the Theora, Vorbis, Opus, VP8, VP9, MP3, AAC
and H.264 codecs

You can go here to show installed codecs.
[https://html5test.com/](https://html5test.com/)

My results.
[ATTACH=CONFIG]277452[/ATTACH]

---

