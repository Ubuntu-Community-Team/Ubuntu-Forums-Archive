---
title: "Disconnecting from a Samba Share"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by unnes on 2007-05-01
I set up a share using samba and set up a dummy account ("share") to test it from Windows. It worked great, so I set up a share for the real account ("unnes") -- but now Windows doesn't want to log out of "share"!

I've tried restarting samba, and I've tried **smbcontrol smbd close-share share**, but neither of them got Vista to give up on that one account. I even deleted the user "share" and the corresponding /home folder, but Vista is still undeterred and won't give me a chance to log in with a different username/pass.

Is there some easy way to log *out* from a samba share? I can tell this is a Windows attempt at making things easy, but this is driving me nuts.

---

