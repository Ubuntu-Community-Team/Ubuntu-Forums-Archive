---
title: "Lubuntu intermittent wifi issue"
date: 2023-07-24
forum: Networking &amp; Wireless
---

### Post by arius88 on 2023-07-24
I'm running Lubuntu 22.04 and using Mozilla Firefox as my web browser. 

My issue is this: several times a day, sometimes as often as every two minutes, the internet stops working. The wifi signal indicator or whatever it's called is still there, and says I'm connected and have a good strong signal. But all my websites stop loading at once and no matter what I do they won't work. It usually - but not always - fixes it if I turn the internet off and back on, but then it just screws up again, usually within a short amount of time. This is obviously extremely frustrating.

Interestingly, the problem also seems to affect my iPhone - the internet sometimes doesn't work on it either, and often it'll kick out at exactly the same time that it stops working on my computer.

A techie friend said it might have something to do with DNS, but I barely understand what that is and have no idea how to fix it or what might be causing the issue. Google has not been helpful as all the help is specific to Ubuntu, not Lubuntu, and most of the commands don't work. I found a post by someone with my same problem that talked about "intermittent DNS name resolution failures" but their solution was to run


```
sudo dpkg-reconfigure resolvconf
```


and that doesn't work for me on Lubuntu.

I've experienced this problem with other Linux operating systems, so I don't think it's specific to Lubuntu. And as I said, it's also happening on my phone. I live with two housemates, and their internet works just fine, so I'm thinking it's a linux problem of some sort. 

Any suggestions of things I can try?
Or what the lubuntu equivalent of "dpgk-reconfigure" and "resolvconf" would be?

Thanks,
Arius

---

### Post by guiverc on 2023-07-24
Your description would imply it's environment related, or an issue with your router (ie. *something that would impact both your iphone & lubuntu pc*). Be it interference when some other device is using that radio frequency, an old device that is struggling (*fridge on defrost cycle, microwave being used etc*) which causes RF to be emitted creating the issue. Those problems will require the use of RF/EMF meter to find though.

As for Lubuntu, I'm using Lubuntu myself - but I consider it a Ubuntu system as that's what it is.

Lubuntu just means we have different desktop & default packages, but Lubuntu is created by the same infrastructure as Ubuntu with just a different *seed* file that causes different packages to be used.  eg. [Lubuntu's seed is here]("https://ubuntu-archive-team.ubuntu.com/seeds/lubuntu.jammy/desktop") where [Ubuntu Desktop's is here]("https://ubuntu-archive-team.ubuntu.com/seeds/ubuntu.jammy/desktop") where you'll note they're both stored on the same system.

Your base system is Ubuntu, with only different desktop, different default apps, and some of the libraries/toolkits differing.  With Lubuntu, your desktop maybe the original shipped LXQt version, or you may have upgraded via [Lubuntu *backports*]("https://lubuntu.me/jammy-backports-22-04-1-lxqt-1-2/") too, but we won't know unless told (*but they'd not impact your issue I'm 99.99999% convinced*).

Your tried command  relates to a non-existent package `resolvconf` and Lubuntu would given the identical answer to a Ubuntu system in that case.  Alas I don't know what you hoped that would do for you.

---

### Post by coffeecat on 2023-07-25
@arius88, you started this thread in Other Operating Systems > Ubuntu/Debian Based, whose tagline states:

> Support for Ubuntu or Debian based distributions - not for Official Ubuntu flavours

Lubuntu is very much an official Ubuntu flavour, so I've moved the thread to the *Networking & Wireless* sub-forum under *Ubuntu Official Flavours Support*. I'll add a Lubuntu thread prefix as well.

---

### Post by arius88 on 2023-08-03
I've grown somewhat used to disabling and enabling the internet whenever pages stop loading. It would still be nice to have an actual solution. In the meantime, it's happened two days in a row now that the internet apparently stopped working while applying a system upgrade. 

```

Upgrade finished
With some Errors

Failed to download package files
Check your internet connection.

```

Yesterday and today, I opened a terminal and ran sudo apt-get update. I forget what it did yesterday, but it remember it went relatively smoothly. Today it blew through getting a bunch of stuff, mostly from security.ubuntu.com and archive.ubuntu.com, then took what seemed like a painful amount of time "reading package lists," whatever that means. Not sure if that's normal.

Then I ran sudo apt-get upgrade. Today it seems to have worked fine. But yesterday it was giving me errors all over the place (I can't remember what it said exactly) that seemed to imply an intermittent internet connection, and it ultimately failed to complete the upgrade. 

Just wondering, if this happens again, what I should do.
And also, could still use some help fixing this weird issue.

---

