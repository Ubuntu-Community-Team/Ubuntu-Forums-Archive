---
title: "Karmic Koala [9.10] Wireless Connectivity Issue"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by anirvan.majumdar on 2009-11-09
Hello,

It's been a month since I've been working with Ubuntu's Karmic version. Everything seems to be working great, but I feel that there's some issue with the way my laptop connects to the wireless router.
Back when I used Jaunty, my laptop could snap onto a wireless network quite efficiently. But now, the wireless connection icon keeps spinning [the animation when it tries to connect to a network] endlessly, and finally prompts me to re-enter my WPA2 password to re-authenticate. Then it again keeps on trying, before prompting me for the password after some time. This cycle repeats 2-3 times and then finally it latches onto the wireless network.
At my friend's place I had to give up connecting as the prompting-for-pwd-then-connecting cycle kept on and on. 

I find this quite strange because the wireless card seems to be able to detect the neighbouring wireless networks accurately. It's just when I want to connect to one of them that I face these issues. And I never faced this issue with any of the earlier versions of Ubuntu.

Any help?

Thanks,
anirvan

---

### Post by l.e.g.e.n.d.a on 2009-12-01
Hello,
I have almost the same problem. It seems that other people have this problem too:
[http://ubuntuforums.org/showthread.php?t=1082812](http://ubuntuforums.org/showthread.php?t=1082812)

And today I cannot connect to wireless network at all :/ Strange.

---

### Post by bkratz on 2009-12-01
> **l.e.g.e.n.d.a said:**
> Hello,
I have almost the same problem. It seems that other people have this problem too:
[http://ubuntuforums.org/showthread.php?t=1082812](http://ubuntuforums.org/showthread.php?t=1082812)

And today I cannot connect to wireless network at all :/ Strange.




If you happen to be using ndiswrapper see this

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

---

