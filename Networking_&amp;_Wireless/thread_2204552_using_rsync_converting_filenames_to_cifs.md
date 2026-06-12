---
title: "using rsync converting filenames to cifs"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by andschuster on 2014-02-09
Hallo,

I want to transfer files by rsync from an ext4-filesystem to my NAS which uses cifs. Some files have names that include characters which aren't allowed by cifs. So I am looking for a way to change these filenames by simply omitting these characters. The option "--iconv" of rsync is not able to do so, if I understand it correctly. Does anybody know a way to do so?

---

### Post by TheFu on 2014-02-09
I would use "find" with "rename" to fix the filenames on the Linux side first. Didn't know that rsync could do that. Nice, if it really works.

**Can you please post the exact command you are attempting?**

Checking the output from **iconv --list** would be good, since different machines have different character sets available.
Knowing the model of NAS might be helpful too, since many use Linux as their OS.

---

### Post by andschuster on 2014-02-09
I don't want to change the filenames on the Linux side. I only want to eliminate the characters on the fly when copying to the NAS. So I believe "rename" doesn't make the job.

I didn't use the option "--iconv" of "rsync" at all, because I don't want to change the encoding, but eliminating the characters that aren't allowed by cifs.

---

### Post by TheFu on 2014-02-09
> **TheFu said:**
> **Can you please post the exact command you are attempting?**

Please.

---

