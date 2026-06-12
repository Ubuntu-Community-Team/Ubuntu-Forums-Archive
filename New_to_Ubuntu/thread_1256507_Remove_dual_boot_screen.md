---
title: "Remove dual boot screen?"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by sunwatt on 2009-09-02
After I told a friend about Ubuntu, he installed 9.04 on his XP laptop, dual boot with his XP.

The wireless didnt work, so he uninstalled Ubuntu, but now he is stuck with the dual boot screen every time he boots up.

I looked at his laptop today, and checked add/remove programs in XP and Ubuntu was gone, he uninstalled it. Then I looked in C drive and found the Ubuntu folder, so I put that in the recycle bin, but didnt empty the bin, just in case.

He's not too happy about having to scroll down to xp every time he boots up, and I'd like to help him. I feel semi responsable for this.

If he had plugged in a cable, it would have connected to the net and fixed the wireless Im sure, but thats not whats happened. 

Once I am able to get his laptop back to normal, he might be willing to try again, maybe we'll try Mint this time.

Thanks for any help.

Jim
Very happy with Mint 7.0 on my Dell Mini 9 with a whopping 8gb SSD!

---

### Post by pastalavista on 2009-09-02
Boot up in recovery mode (or whatever Windows calls it) or from the Windows install CD and fix the boot menu. I believe the command 'fixboot' or 'fixmbr' will do it.

---

### Post by OffAxis on 2009-09-02
if you boot the windows machine to the recovery console (from the original install disc), you should be able to issue a 

```
FIXMBR
```
or a 

```
FIXBOOT
```

to fix the problem.

Here's microsoft's support page on the subject:
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)


You can also try Super Grub Disc

[http://supergrubdisc.org](http://supergrubdisc.org)

---

### Post by sunwatt on 2009-09-02
Thanks my friends. I will email this info to him now.

Maybe I was misinformed, but I told my friend  that if he didnt like ubuntu, just uninstall it from the XP add/remove programs feature.

I wish I had been there when my friend installed Ubuntu, so I knew how this dual boot screen could be left behind after an uninstall of Ubuntu.

If I had have been there with him, I would have plugged in the cable, and as I remember, that can get the wireless working.

I've installed Ubuntu 9.04 on one of my laptops, but not dual boot with XP. 

Thanks again friends

Jim

---

### Post by louieb on 2009-09-02
WUBI install? Sounds like it.

If windows version is XP or earlier edit c:/boot.ini and remove the Ubuntu entry.

---

### Post by sunwatt on 2009-09-02
Thank you!!

I sent it on to my friend.

Jim

---

