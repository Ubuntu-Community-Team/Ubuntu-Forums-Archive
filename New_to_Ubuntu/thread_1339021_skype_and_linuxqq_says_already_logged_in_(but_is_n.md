---
title: "skype and linuxqq says already logged in (but is not)"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by fangz on 2009-11-27
Hello, all.

I installed a 9.04 desktop Japanese remix ubuntu. I went through some procedure (that I have no idea of) to enable me and everyone else in the lab to log in the computer using each one's own lab accounts, and see their own desktops. The lab accounts were registered on the server and the file system for each lab member is somehow synchronized, I guess.

After a mysterious crash, I had to long-press the power button to shut down the system. Then after I restarted the system, firefox, skype and linuxqq (another instant messeging software widely used by chinese ppl) wouldn't work, complaining about 'already running' or 'already logged in'.

I googled this problem for firefox, and found some suggestions saying I should delete a 'parentlock' thinggy, so I did, then the firefox would start alright, but it gave a warning every time, saying it was closed unexpected previously.

Me being a absolute beginner, decided to reinstall the system. Then firefox is fine again, but still skype and linuxqq says 'already logged in'.

I also tried purge skype then reinstall, but the problem remains.
How do I fix this?

---

### Post by fangz on 2009-11-27
can't believe i fixed it one min after i posted this thread.

for skype, "rm -rf ~/.Skype" then restart skype, it works again.
the same for linuxqq.

i guess think the problem through helped.

cheers!

---

