---
title: "Accessing windows files in Ubuntu"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by dryfire on 2009-05-11
I installed 9.04 from Windows 7, dual boot. Both run well. How can I access the Windows files while running Ubuntu. The HD is identified as "system reserved" and I cannot find the Windows files. I can see and access the other HDs on the system.

TIA
Jim
[email]dryfire@bellsouth.net[/email]

---

### Post by tkelito on 2009-05-11
Have you looked in /hosts folder?

If you used Wubi to install this is where it will place the rest of the directory that you installed Ubuntu into.

Or are you trying to mount the C: drive?

-tkelito

---

### Post by Redache on 2009-05-11
It could be that Windows 7 has an NTFS revision that isn't compatible with the FUSE driver. It's usually installed by default with read capability (I think it might have write by default now as well).

---

### Post by abhiroopb on 2009-05-11
Click on "Places" in your panel and look for something that says Windows or similar. It should be there.

---

### Post by dryfire on 2009-05-11
Files found in host. Thank you

Jim

---

