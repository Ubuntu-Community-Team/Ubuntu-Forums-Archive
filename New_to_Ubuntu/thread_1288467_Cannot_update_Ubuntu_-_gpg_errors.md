---
title: "Cannot update Ubuntu - gpg errors"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by mistypotato on 2009-10-11
It's been about 6 months or more since I was able to update Ubuntu 8.10

**The problem has been a gpg error like this.....**

misty@Dellcomputer:~$ sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 60D137693721CFG
gpg: WARNING: unsafe ownership on configuration file `/home/misty/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

On numerous occasions, I have researched, Googled and read every post here I could find on this and tried everything...with no success.

However, I think it's important to note that when I run this, I do in fact get a couple of new keys in the folder....even after deleting them and running the command again I get the two new keys back in the folder...but the UPDATES still wont work as it reports it cant find the key in question.

I am beginning to feel my core system may be compromised or something wacky.

Can anyone help me resolve this?

thanks :KS

---

### Post by LewRockwell on 2009-10-11
we recommend a fresh install of 9.04

(after confirming successful operations via the LiveCD of course)

.

---

### Post by taavikko on 2009-10-11
> **LewRockwell said:**
> we recommend a fresh install of 9.04



That's the last resort.

What's the permissions currently?
```
ls -l ~/.gnupg/
```

I have "-rw------" which transforms to 600
If wanting to set it as such on your own
```
chmod 600 ~/.gnupg/gpg.conf
```

If this doesn't help, use the next
```
chmod -R 600 ~/.gnupg/
```

---

