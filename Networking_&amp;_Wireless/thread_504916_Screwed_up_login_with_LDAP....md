---
title: "Screwed up login with LDAP..."
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by 5of0 on 2007-07-19
I was trying to set up my Ubuntu 7.04 to authenticate via LDAP, and was following a howto when I rebooted and got Authentication Failed.  After reading up, my guess is that I screwed up one or more of the common-* files, so I've tried to fix them (no, I didn't make a backup ](*,) ) to no avail.

All I want right now is someone with a normal, default, original, run-of-the mill Ubuntu system to paste their common-* files in here (list, for specificity and Google).

```

/etc/pam.d/common-auth
/etc/pam.d/common-password
/etc/pam.d/common-account
/etc/pam.d/common-session

```

Hmm, actually it seems I may have succeeded to some degree as I type - I no longer get "Authentication Failed" after the username.  I replaced all the pam_ldap.so with pam_winbind.so, and it got farther.

But I would still like someone to post their normal files, so I can see if that's the problem.

Edit: Okay, so it logged in, but everything is taking ages to happen.  It is the same with booting, a few of the items take ages (probably >1min each) to work that have never had problems before.  I suppose this would make sense since anything that uses auth uses the files that I screwed with...dang.

Other than that, I'll check back in if I get things working.

Edit again: After it finally logged in, I was able to look at the gEdit recently edited files list, and realized that there were LDAP remnants in nsswitch.conf as well, which I had made a backup of.  Things seem to be working a lot better after I replaced those with winbind - yay!  Now I'm going to make backups (!) and see if I can't figure this thing out.

---

