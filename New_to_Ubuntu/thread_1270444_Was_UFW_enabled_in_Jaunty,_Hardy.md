---
title: "Was UFW enabled in Jaunty, Hardy?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by ankspo71 on 2009-09-19
Hi Everyone,

I just did a clean install of Karmic Alpha 6 last night, and I am happy to report that I am having no problems with it and it appears to be stable (for me and my computer). 

However, I noticed some boot up progress messages that say something in the lines of these words: "UFW firewall is not active, it has not been enabled." This applies to Ubuntu Karmic 32bit i386 alpha 6.

I know how to enable UFW, which wasn't hard for me to figure out, but I was wondering about these two things...

Was I using Jaunty and Hardy without a firewall enabled the whole time? or is this only a Karmic issue?

Even though UFW is not enabled by default, Ubuntu's IP tables are still working effectively, right?

Thanks,
James

---

### Post by yabbadabbadont on 2009-09-19
No, it wasn't enabled by default in Jaunty.  I believe that the default action when it isn't enabled, is to simply reject all connection attempts.  When enabled, I believe that the default action is to drop them instead.

---

### Post by shae on 2009-09-19
Yeah, Ubuntu does not start with the firewall enabled.  Usually, a firewall is only needed in a server environment, but it never hurts to enable it.  Ubuntu starts without any programs that actively listen to ports anyways.

---

### Post by ankspo71 on 2009-09-19
Ahh, I see, thanks yabbadabbadont and shae. Thanks for the speedy and informative replies.
James

---

