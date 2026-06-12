---
title: "Using skeleton files in conjunction with Likewise and AD"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by hchristopher on 2008-07-17
Hello.  I have a 32-bit PC running Ubuntu 8.04 at work that I recently set up.  It is meant to be multi-user, and to use Active Directory from and MS server for authentication.

To join the computer to AD, I used a program called Likewise that I found in Ubuntu's default package repository.  It works great (my compliments to the programmers).

When a AD user logs on for the first time, the computer automatically creates a home folder for them.  However, it does not seem to create the files in the 'skel' directory.

This is a problem because I would like all new users to have some default Desktop icons that I have chosen.  Before the switch to AD, I could just drop a "Desktop" directory in the skel directory.

All the Likewise documentation I found really only discusses how to install Likewise and how to make the switch to AD.

My real concern is getting those default desktop icons.  It doesn't really matter to me if I was the skel directory, or some other method.  I'd appreciate any suggestions.  Thanks for your help in advance!

---

### Post by likeWiseGuy on 2008-10-03
> **hchristopher said:**
> Hello.  I have a 32-bit PC running Ubuntu 8.04 at work that I recently set up.  It is meant to be multi-user, and to use Active Directory from and MS server for authentication.

To join the computer to AD, I used a program called Likewise that I found in Ubuntu's default package repository.  It works great (my compliments to the programmers).

When a AD user logs on for the first time, the computer automatically creates a home folder for them.  However, it does not seem to create the files in the 'skel' directory.

This is a problem because I would like all new users to have some default Desktop icons that I have chosen.  Before the switch to AD, I could just drop a "Desktop" directory in the skel directory.

All the Likewise documentation I found really only discusses how to install Likewise and how to make the switch to AD.

My real concern is getting those default desktop icons.  It doesn't really matter to me if I was the skel directory, or some other method.  I'd appreciate any suggestions.  Thanks for your help in advance!

Hi, Christopher.

Likewise Open works seamlessly with skeleton files so I'm curious as to what kind of configuration you have. I'm hoping that I can help you out with this as it is important to you.

Please let me know if you are still interested.

---

### Post by Forrest Gump on 2009-03-25
I was experiencing the same problem, and found the solution _[here]("http://www.linux.com/forums/topic/2262")_.

Summary: Edit /etc/security/pam_lwidentity.conf . The line with ```
;skel = /etc/skel
``` needs to have the semicolon (a comment marker) removed. Look for it around line 32 (of 41).

---

### Post by windwalker78 on 2010-03-23
> **Forrest Gump said:**
> I was experiencing the same problem, and found the solution _[here]("http://www.linux.com/forums/topic/2262")_.

Summary: Edit /etc/security/pam_lwidentity.conf . The line with ```
;skel = /etc/skel
``` needs to have the semicolon (a comment marker) removed. Look for it around line 32 (of 41).

Thanks a lot :)

---

