---
title: "Ubuntu &amp; Windows Server 2003 Domain"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by jrgray27 on 2007-08-05
I have been using Ubuntu 7.04 for 2 weeks now and LOVE it. I now want to intergrate it into my Windows 2003 Server Domain. As in join it into the domain. But have no idea. I've googled and found articles for a week now and only have found things that are close. I need either a program or very EXACT STEP BY STEP instructions on how to do it. In this case there is no such thing as to much info. I'm NEW to it (Linux) and I'm a hardcore Windows person that's willing to learn something new. Once again to much info is no problem, what I've found have not work or is not exact to the point where I'm not sure what to change/enter.

I'm greatly appreciated of anyone who can give me instructions or an app that will do this for me.


Thanks a lot,


Floyd

---

### Post by kesomir on 2007-08-05
I think that this was the tutorial I followed back when I did it:

[http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

the only major thing missing was that sound etc didn't work. One fix for that is to use pam_group to assign group membership on the fly at login. Googling for pam_group should give you a few guides.

My caveat is that you need to put the line they mention entering into the files under pam.d at the start of the file, not the end else it won't work :)

Best of luck.

---

