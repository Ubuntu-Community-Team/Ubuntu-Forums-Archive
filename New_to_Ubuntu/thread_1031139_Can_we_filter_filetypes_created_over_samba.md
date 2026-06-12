---
title: "Can we filter filetypes created over samba?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Guruprasad on 2009-01-05
Can we filter file types created over samba?

This is to prevent the virus files from windows from copying over network.

---

### Post by cmnorton on 2009-01-08
Although not a direct answer to your question, I believe offering SAMBA shares to Windows clients is a good reason to run either open source or proprietary anti-virus on your Linux server. 

I do not know of anything that would control the types of files that are created, unless you wrote a file watcher of some type or got an activity picked up by LogWatch, but, even then, you'd be reporting after the file was created. SE Linux has deeper control over user access, but I do not know if it can filter file types.

Have you thought of an ACL from the Windows side, and would it even work on a shared drive?

---

