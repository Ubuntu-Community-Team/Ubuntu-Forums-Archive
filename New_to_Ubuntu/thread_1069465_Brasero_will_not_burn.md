---
title: "Brasero will not burn"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by tropdoug on 2009-02-14
Anyone any idea what's happening, I compile a load of mp3 files to burn as a data disc. I have tried burning direct but I get an error (see attachment) I have tried six different cd's in case I really did have one with stuff on it, but got the same error each time. I saved the project as an iso file onto the hard drive, and then tried to burn the iso to disc, same error?

any ideas?

---

### Post by Kevbert on 2009-02-14
This is a bug in brasero. It might be worth trying to update to a newer version.

---

### Post by binbash on 2009-02-14
which version are you using?Go to getdeb.net and update your brasero

---

### Post by tropdoug on 2009-02-16
Thanks guys 

The version I am using is 0.8.2. I will do the update thing and see what happens.

In desperation I loaded on K3B which works fine, but I am trying to keep my system as either gnome or Kde but at the moment I seem to prefer gnome. I will post the result for others when I do the update

---

### Post by zzztownsend on 2009-03-05
I had same problem. I just installed 'serpentine' which works perfectly and only has a few dependencies. I also tried gnomebaker which was very unstable

Cheers

Matt

---

### Post by tropdoug on 2009-03-26
couldn't get brasero to work, so sticking with K3b for now. Thanks everyone

---

### Post by SamNSane on 2009-03-26
I thought I would post this information -- just in case it's applicable to your situation.

I am using the latest version of brasero available for Hardy from GetDeb -- version 0.8.4.

I never burn multi-session discs because I just don't like how subject they are to failure within the ToC. But even burning DaO with brasero has its pitfalls. On my three personal very different (hardware-wise) systems I can always burn to CD-RW discs with no problem. But I ALWAYS am notified that the burn failed when I'm using CD-R or DVD-R discs. This notification comes at the terminus of the burn session, just as brasero is trying to verify the burn. But the fact is that the burn has NOT failed. I have done many manual checks (MD5SUM / SHA1) of the burned discs against the source locations on hard disc, and they always check out.

The fact that I see this behavior on three different motherboards, three different 8.04 installations, and four different burners (One of the systems has 2 burners on it.) makes me think that this is definitely a brasero problem. Or a problem with the way I've configured HH. But my systems are really pretty plain. With the exception of a couple of applications from GetDeb and the launchpad PPAs, everything installed on the system has come from the standard and backport repositories.

---

