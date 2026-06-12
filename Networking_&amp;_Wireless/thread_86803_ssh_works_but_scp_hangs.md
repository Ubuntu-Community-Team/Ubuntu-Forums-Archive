---
title: "ssh works but scp hangs"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by pheitman on 2005-11-06
I'm having an odd problem with scp. I can ssh to my ubuntu machine(s) but I can't scp to them - the scp command hangs after authenticating. I have tried this even on localhost with the same behavior. I tried running sshd with debug turned up but didn't see anything that I understood.

So to summarize, I have two Breezy Badger machines with this same problem. I can ssh to them but not scp. Even when the scp target is localhost.

Can someone suggest how to approach diagnosing and fixing this?

Thanks in advance,

peter

---

### Post by pheitman on 2005-12-02
I finally figured this out. My .bashrc file was outputting characters (to set the window title) even when bash was non-interactive. Fixing this allowed scp and sftp to work correctly.

Peter

---

