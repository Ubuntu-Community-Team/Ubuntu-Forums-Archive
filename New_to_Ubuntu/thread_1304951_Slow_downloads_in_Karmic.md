---
title: "Slow downloads in Karmic"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by CaptainMark on 2009-10-29
Ive gone for a fresh install of Karmic today so i can upgrade to 64bit and ext4. Im getting stupidly slow download speed from synpatic, anyone else finding this, i would put it down to busy servers being launch day but i got the 700mb desktop iso in about 10mins only a few hours ago.

---

### Post by dvlchd3 on 2009-10-29
The download server for the ISO is different from the repositories.  You're right, it is most likely due to all the updates new 9.10 users are downloading.

You may try using a mirror repository:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by Temposs on 2009-10-29
Yeah, you should expect this for a few days. It's the way things always go when a new version is released. Either be patient or wait a few days for the traffic to calm down.

---

### Post by The Titan on 2009-10-29
Do you have issues downloading other packages from Synaptic?  Becauseyou could try choosing another mirror for apt.  The simple way is to open up the software sources from system -> Administration.  Choosing "Other" from the mirrors dropdown and hitting the "Select best Server" button on the top right.

---

### Post by BFG on 2009-10-31
I have noticed that ALL downloading from the internet is slow.  Browsing is as fast as ever, but any download from any site, including synaptic, is very slow.

9.04 machine on same LAN is fast as ever (20Mbps broadband).
Fresh install of 9.10. machine as per sig.

---

### Post by Temposs on 2009-10-31
> **BFG said:**
> I have noticed that ALL downloading from the internet is slow.  Browsing is as fast as ever, but any download from any site, including synaptic, is very slow.

9.04 machine on same LAN is fast as ever (20Mbps broadband).
Fresh install of 9.10. machine as per sig.

This is unrelated to the issue reported by the original poster. Please start a new thread to discuss your particular issue.

---

### Post by kumoshk on 2009-10-31
> **CaptainMark said:**
> Ive gone for a fresh install of Karmic today so i can upgrade to 64bit and ext4. Im getting stupidly slow download speed from synpatic, anyone else finding this, i would put it down to busy servers being launch day but i got the 700mb desktop iso in about 10mins only a few hours ago.

Yeah, I've noticed it, too. I never got this problem quite like this before (I've been using Ubuntu since Gutsy).

I'm guessing the default download source is set to a different location or something (kind of how it was for downloading the ISO—I had to switch that to another, since the speeds of the default were similar to the speeds I have now with apt-get).

How do I change the default mirror it uses to download through apt-get?

I'd really like to have ubuntu.cs.utah.edu as the default.

---

### Post by kumoshk on 2009-10-31
> **kumoshk said:**
> I'd really like to have ubuntu.cs.utah.edu as the default.

Ah, I just figured out the answer. Just go into the software sources and change the download from thing to the right mirror. Pretty easy in karmic. Let's see if it helps the speeds.

---

