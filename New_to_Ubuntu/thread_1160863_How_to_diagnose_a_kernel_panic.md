---
title: "How to diagnose a kernel panic?"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by kobudo on 2009-05-16
Hi all,

After the recent upgrade to Jaunty from XP (clean install) I have occasionally been stuck with a locked up system and my caps lock & scroll lock keys flashing. I've done some research and found out what this means, so I ask how does one go about tracking down the cause of a kernel panic? 

Also, I don't know if this is related or not, but some of my mpeg video files are showing incorrect play lengths (like a half hour video coming up as being 49 seconds long). If I use the seek bar in Movie Player, I can seek through the entire video just fine (ie skipping to 15:00 into the video) but if it gets to that 49 second point, it stops playing.

I am using madwifi and nvidia accelerated graphics driver version 180, and had the same issues with version 173.

Thanks for any guidance in this matter.

---

### Post by Didius Falco on 2009-05-16
> **kobudo said:**
> Hi all,

After the recent upgrade to Jaunty from XP (clean install) I have occasionally been stuck with a locked up system and my caps lock & scroll lock keys flashing. I've done some research and found out what this means, so I ask how does one go about tracking down the cause of a kernel panic? 

Also, I don't know if this is related or not, but some of my mpeg video files are showing incorrect play lengths (like a half hour video coming up as being 49 seconds long). If I use the seek bar in Movie Player, I can seek through the entire video just fine (ie skipping to 15:00 into the video) but if it gets to that 49 second point, it stops playing.

I am using madwifi and nvidia accelerated graphics driver version 180, and had the same issues with version 173.

Thanks for any guidance in this matter.

Hi, and welcome to the Ubuntu forums.

You should find this guide helpful:

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

You can also download "kerneloops" from Synaptic Package Manager. It's a utility that collects information that can be sent to the linux kernel developers.


I'm by no means any kind of expert - I'm just learning about this stuff as I go.

I hope this helps,

Regards,

Didius

---

