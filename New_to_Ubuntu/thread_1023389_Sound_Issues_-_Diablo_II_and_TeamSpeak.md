---
title: "Sound Issues - Diablo II and TeamSpeak"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by Shhnap on 2008-12-27
Ok so I'm running TeamSpeak (not under wine) while playing Diablo II (under wine) so that I can talk to everybody in my party but the problem is that while TeamSpeak is running Diablo II will not give any sound. If I run Diablo II without teamspeak in the background, then no problems, Diablo II makes all of the sounds it's supposed to.

I have searched around for help already but the only thing I could find asked me to put the following in a startup script:

```

echo 'quake3.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'quake3.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss

```
From: [http://www.teamspeak.com/?page=faq&cat=client&rate=47#howto_fix_alsa_problems](http://www.teamspeak.com/?page=faq&cat=client&rate=47#howto_fix_alsa_problems)

However, when I check the oss file right after I have made those commands the oss file is still empty. (And I have to type those commands as the super user so there should be no problems)

So my question is? How do I fix this problem? How do I get Diablo II to make sound while TeamSpeak is running? :)

---

